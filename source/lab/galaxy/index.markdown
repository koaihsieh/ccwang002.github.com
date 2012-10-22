---
layout: page
title: "Galaxy Setup"
date: 2012-10-22 22:00
comments: false
sharing: false
footer: true
---

<script src='js/jquery.min.js' type="text/javascript"></script>
<script src='js/jquery.timeago.js' type="text/javascript"></script>

##Brief

* The following is the installation of Galaxy.  
* All the tutorials can be found at this site: <http://wiki.g2.bx.psu.edu/FrontPage>  

By default, it use:

* SQLite
* built-in http server instead of Apache
* Runs all tools locally
* Runs in a single process

To make the Galaxy faster, the steps are introduced in the section [Tune](#tune) follow the links below:

* [Admin Tutorial](http://wiki.g2.bx.psu.edu/Admin/Training/Galaxy%20Admin%20Tutorial)
* [Performance](http://wiki.g2.bx.psu.edu/Admin/Config/Performance/Production%20Server)

For the actual setting on the lab server 173, please refer to Section [Actual Setting](#actualset)

---
##Preparation##
###Initial Installation###
1. install the python 2.5+  
`sudo apt-get install python-all-dev python-setuptools`
2. install Mercury ( [tutorial using Ubuntu](https://help.ubuntu.com/community/Mercurial) )  
`sudo apt-get install mercurial meld`

If the version of Python is not 2.5+, the solution:

    $ mkdir ~/galaxy-python
    $ ln -s /path/to/python2.5 ~/galaxy-python/python
    $ export PATH=~/galaxy-python:$PATH
    
put the new version python in the alternative directory.
<a name='install'></a>
###Install Galaxy
The following instruction is from [here](http://wiki.g2.bx.psu.edu/Admin/Get%20Galaxy)

1. get the latest copy  
`hg clone https://bitbucket.org/galaxy/galaxy-dist/`
2. type `sh run.sh`  
    Then the galaxy server will be on <http://localhost:8080> locally
3. for Python 2.5+ may encounter a problem that `Ctrl-c` cannot stop the Galaxy server.       
    To solve this problem, start the server using `sh run.sh --reload`

###Update Galaxy
1. type `hg incoming` to check if there is a new distribution
2. It is recommended to use Galaxy's [News Brief](http://wiki.g2.bx.psu.edu/DevNewsBriefs) to check new version

##Run Galaxy Over Network (HTTP Serverice by Galaxy Itself)##
###Galaxy Setup
1. Modify the file `~/galaxy/universe_wsgi.ini`
2. Find, uncomment and change the following lines to `host =  0.0.0.0` and one can change the port by setting `port = 8080`
 
##Run Galaxy Over Network (Proxy by Apache)##
The tutorial is [here](http://wiki.g2.bx.psu.edu/Admin/Config/Apache%20Proxy)  
This setting enable the access to Galaxy by <http://your.server/galaxy/>

###Apache Setup
Put the following lines in the apache2 configuration file  
in my case, `/etc/apache2/httpd.conf`  
Then insert the following code:    

``` 
RewriteEngine on
RewriteRule ^/galaxy$ /galaxy/ [R] 
RewriteRule ^/galaxy/static/style/(.*) /home/nate/galaxy-dist/static/june_2007_style/blue/$1 [L] 
RewriteRule ^/galaxy/static/scripts/(.*) /home/nate/galaxy-dist/static/scripts/packed/$1 [L] 
RewriteRule ^/galaxy/static/(.*) /home/nate/galaxy-dist/static/$1 [L] 
RewriteRule ^/galaxy/favicon.ico /home/nate/galaxy-dist/static/favicon.ico [L] 
RewriteRule ^/galaxy/robots.txt /home/nate/galaxy-dist/static/robots.txt [L] 
RewriteRule ^/galaxy(.*) http://localhost:8080$1 [P]
```

<a name='setup'></a>
###Galaxy Setup
In `universe_wsgi.ini` change `host` to `host = 0.0.0.0`. Then insert  

```
[filter:proxy-prefix]
use = egg:PasteDeploy#prefix
prefix = /galaxy

[app:main]
 
filter-with = proxy-prefix
cookie_path = /galaxy
```

###Further Topics
* External user authentication
* Display sites
* SSL
* Compression and caching
* Sending files using Apache 

##Start/Stop Galaxy
###Start the Galaxy Server
One can simply start the Galaxy Server under `~/galaxy-dist/` by
    
    $ sh run.sh --reload
the `--reload` is for Python 2.5+, which can terminate the process by `Ctrl-c`.

There is another way to keep Galaxy server online for a long time, allowing the user to logout. By using `nohup` command,

    $ nohup sh run.sh --reload > ~/galaxy_runtime_log.txt 2>&1 &
    
or

    $ nohup sh ~/galaxy-dist/run.sh --reload > ~/galaxy_runtime_log.txt 2>&1 &

will keep the Galaxy run at background, and keep all the message at `~/galaxy_runtime_log.txt`.

###Stop the Galaxy Server
If it is running at background, use `ps` to find the process and kill. For example,

    $ ps aux|grep liang
    
One will get 

```    
root     13393  0.0  0.0  90148  3320 ?        Ss   20:50   0:00 sshd: liang [priv]
liang    13397  0.0  0.0  90148  1752 ?        S    20:50   0:00 sshd: liang@pts/4
liang    13398  0.0  0.0  66204  1636 pts/4    Ss   20:50   0:00 -bash
liang    13826  0.0  0.0  63864  1148 pts/4    S    21:08   0:00 sh run.sh --reload
liang    14004  0.0  0.0 159452 11832 pts/4    S    21:08   0:00 python ./scripts/paster.py serve universe_wsgi.ini --reload
liang    14005  8.4  0.0 607000 124556 pts/4   Sl   21:08   0:17 /home/liang/local/Python-2.7/bin/python ./scripts/paster.py serve universe_wsgi.ini --reload
liang    14086  0.0  0.0  65624  1004 pts/4    R+   21:12   0:00 ps aux
liang    14087  0.0  0.0  61204   792 pts/4    R+   21:12   0:00 grep liang
```

So kill the following process: 

```    
liang    13826  0.0  0.0  63864  1148 pts/4    S    21:08   0:00 sh run.sh --reload
liang    14004  0.0  0.0 159452 11832 pts/4    S    21:08   0:00 python ./scripts/paster.py serve universe_wsgi.ini --reload
liang    14005  8.4  0.0 607000 124556 pts/4   Sl   21:08   0:17 /home/liang/local/Python-2.7/bin/python ./scripts/paster.py serve universe_wsgi.ini --reload
```

In this example, 

    $ kill 13826 14004
    
will end the Galaxy server.
   
<a name='tune'></a> 
##Tuning
###Switch to a Database Server##
original site: <http://wiki.g2.bx.psu.edu/Admin/Config/Performance/Production%20Server>

* modify the `universe_wsgi.ini`  
    
```
database_connection = mysql:///galaxy?unix_socket=/var/run/mysqld/mysqld.sock
```

###Apache Proxy (不需要)

1. Enable modules: `rewrite`, `proxy`  

    ```
    $ sudo a2enmod rewrite proxy
    ```

2. Add theses lines in the apache config file `/etc/apache2/httpd.conf`  

```
RewriteEngine on
RewriteRule ^/static/style/(.*) /home/nate/galaxy-dist/static/june_2007_style/blue/$1 [L]
RewriteRule ^/static/scripts/(.*) /home/nate/galaxy-dist/static/scripts/packed/$1 [L]
RewriteRule ^/static/(.*) /home/nate/galaxy-dist/static/$1 [L]
RewriteRule ^/favicon.ico /home/nate/galaxy-dist/static/favicon.ico [L]
RewriteRule ^/robots.txt /home/nate/galaxy-dist/static/robots.txt [L]
RewriteRule ^(.*) http://localhost:8080$1 [P]
```    

###Make Galaxy as a Service
Please refer to the README file at `$HOME/galaxy-dist/contrib/README` 

Then one can start/stop the Galaxy by (in Ubuntu for example)

    $ sudo sh /etc/init.d/galaxy start
    $ sudo sh /etc/init.d/galaxy stop
    

###Load Balancing And Web Application Scaling (不需要)
<http://wiki.g2.bx.psu.edu/Admin/Config/Performance/Web%20Application%20Scaling>

---

<a name='actualset'></a>
##Actual Setting##
**CAUTION:** be careful on the PUBLIC SERVER!!

1. use `uname -a` to check the current linux version.   
It is `64 bit`.
2. use `cat /etc/redhat-release` to check the CentOS version.   
It is `CentOS release 5.7 (Final)`. So it may encounter problems when install Python 2.5+.

### Install Python 2.7
The step has many solutions:

1. use tutorial [here](http://www.joywang.info/?p=112) to install the Python 2.7 in my own `$HOME` directory, using no root privilege.
2. use root to upgrade the system's python to 2.7 (may cause dependency problem)

I use the **solution 1** in the following steps. However, unlike the tutorial, I only install the python 2.7.

The Python installation structure is 

* Python 2.7:  `$HOME/local/Python-2.7`
* Other executables: `$HOME/local/bin`
* Header files: `$HOME/local/include`
* Libraries: `$HOME/local/lib`
* Temporary artifacts: `$HOME/temp`

And the installation steps are as follow.

1. create the directories needed.   

       $ mkdir ~/temp ~/local
   
2. download the Python 2.7 source

{% codeblock lang:bash%}
$ cd ~/temp  
$ wget http://python.org/ftp/python/2.7/Python-2.7.tgz  
$ tar zxvf Python-2.7.tgz  
$ cd Python-2.7
{% endcodeblock %}

3. install Python 2.7

{% codeblock lang:bash%}
$ ./configure --prefix=$HOME/local/Python-2.7
$ make
$ make install
{% endcodeblock %}

4. one will get the following message, but it is ok since we are not going to use these modules

```
Python build finished, but the necessary bits to build these modules were not found:
bsddb185           dl                 imageop         
sunaudiodev                                           
To find the necessary bits, look in setup.py in detect_modules() for the module's name.
```

###Hooking up Python 2.7 as Login
1. back to home directory `cd `
2. put the new python path into file `.bash_profile`.   
It can be done also by Vim or any other text editor.  

{% codeblock lang:bash%}
# path for Python 2.7 locally    
export PATH=\"$HOME/local/bin:\$PATH\"    
export PATH=\"$HOME/local/Python-2.7/bin:\$PATH\"  
{% endcodeblock %}

###Install Galaxy
1. Follow the setup [above](#install).
2. At the `hg clone …` step, it may show   

{% codeblock lang:bash%}
warning: bitbucket.org certificate with fingerprint 24:9c:45:8b:9c:aa:ba:55:4e:01:6d:  
58:ff:e4:28:7d:2a:14:ae:3b not verified (check hostfingerprints or web.cacerts config   
setting)
{% endcodeblock %}

to solve this, follow <http://mercurial.selenic.com/wiki/CACertificates>
3. To solve the Mercurial HTTPS certificate problem, first new a setting file `.hgrc` at home directory.   
Add the following lines:

```
[web]
cacerts = /etc/pki/tls/certs/ca-bundle.crt
```

###Configuration of Galaxy
For detail please refer to [Galaxy Setup](#setup) part.

1. Set `host = 0.0.0.0` and keep the port to be 8080 `port = 8080`
2. New a MySQL account `galaxy` with no password and a DB using same name, granted all privilege.
3. Modify the file `~/galaxy-dist/universe_wsgi.ini`. Find the line started with `database_connection = … `, uncomment it and change it into  
  
    ```
    database_connection = mysql:///galaxy?unix_socket=/var/lib/mysql/mysql.sock
    ```

4. Start the galaxy server by 

        $ sh run.sh --reload | egrep --color=auto 'WARNING|Error'
 
   Watch the debug message.  
   In my case, the following WARNING/Error popped up.
       
```
galaxy.tools WARNING 2012-08-14 02:22:35,018 A when tag has not been defined for 'master_variable_type (master_variable_type_selector) --> allPairs', assuming empty inputs.
galaxy.tools WARNING 2012-08-14 02:22:36,879 A when tag has been defined for 'manipulation (manipulation_selector) --> modify_each_score', but does not appear to be selectable.
galaxy.tools.test DEBUG 2012-08-14 02:22:38,227 Error in add_param for report_discordant_pairs: Unable to determine parameter type of test input 'report_discordant_pairs'. Ensure that the parameter exists and that any container groups are defined first.
docutils WARNING 2012-08-14 02:22:38,270 <string>:50: (WARNING/2) Literal block expected; none found.
galaxy.tools.test DEBUG 2012-08-14 02:22:38,281 Error in add_param for min_coverage_intron: Unable to determine parameter type of test input 'min_coverage_intron'. Ensure that the parameter exists and that any container groups are defined first.
galaxy.tools.test DEBUG 2012-08-14 02:22:38,282 Error in add_param for max_coverage_intron: Unable to determine parameter type of test input 'max_coverage_intron'. Ensure that the parameter exists and that any container groups are defined first.
galaxy.tools.test DEBUG 2012-08-14 02:22:39,504 Error in add_param for force: Unable to determine parameter type of test input 'force'. Ensure that the parameter exists and that any container groups are defined first.
galaxy.web.framework.base DEBUG 2012-08-14 02:22:42,544 Enabling 'error' controller, class: Error
```
    
5. Make `galaxy` to be launched as daemon. read the file `~/galaxy-dist/contrib/README`  
   For CentOS it should be as follow:
   
```
$ sudo cp ~/galaxy-dist/contrib/galaxy.fedora-init /etc/init.d/
$ cd /etc/init.d; mv galaxy.fedora-init galaxy; chmod 755 galaxy
$ chkconfig galaxy on
```

   Then one can start/stop Galaxy by
   
       $ sudo /etc/init.d/galaxy start
       $ sudo /etc/init.d/galaxy stop
       
6. Disable the developer setting. Find and change the following options:

    ```
debug = False
use_interactive = False
cleanup_job = onsuccess
```

###Using Local Data (看不懂，但也許用不到)
Tutorial: <http://wiki.g2.bx.psu.edu/Admin/Config/Performance/Production%20Server#Local_Data>  

1. Samples to locate these large local data are at `~galaxy_dist/tool-data/`

###Upload via FTP (有點複雜)
Tutorial: <http://wiki.g2.bx.psu.edu/Admin/Config/Upload%20via%20FTP>

1. modify the file `~/galaxy-dist/universe_wsgi.ini`. Find, uncommented, and change the following line:
    
        ftp_upload_dir = /home/galaxy/galaxy-dist/database/files/
        ftp_upload_site = 172.17.0.173

2. Add a MySQL user `galaxyftp`, granted the least privilege to `SELECT` from the `galaxy_user` table and nothing else. The result will be like this:  
    ![MySQL Setup](/lab/data/galaxyftp_mysql.png)
3. Configure the FTP server  
However, this step is a bit complicated, so we are not going to configure the ftp server.

4. Still we can use put those file into the directory 

        /home/galaxy/galaxy-dist/database/files/<YOUR EMAIL ADDRESS>   
For example, my email of the Galaxy account is `b98901114@ntu.edu.tw`.   
Then I put my file into the directory   

        /home/galaxy/galaxy-dist/database/files/b98901114@ntu.edu.tw/ 
Galaxy will search that folder and show it up in the Uploading File page  
    ![Uploading local file](/lab/data/ftp_test.png)
    
##Future Work
###Cluster
Tutorial: <http://wiki.g2.bx.psu.edu/Admin/Config/Performance/Cluster>

###Clean Up Spaces
Tutorial - Purging Unwanted Histories, Libraries and Datasets: <http://wiki.g2.bx.psu.edu/Admin/Config/Performance/Purge%20Histories%20and%20Datasets>


<!--END OF THE MARKDOWN -->
