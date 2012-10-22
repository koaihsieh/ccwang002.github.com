---
layout: page
title: "Useful CentOS Cammands"
date: 2012-10-22 22:02
comments: false
sharing: false
footer: true
---

##User Control##
### Add `sudo` Privilege 
Using `visudo` command

    $ visudo
 
Add the following lines:

```
liang     ALL=(ALL)     ALL
```

This will modify the file `/etc/sudoers`.

For a sudoer, one should type `su - ` to import the `root`'s environment (This requires the password of `root`).

However, we can add `PATH` into `/etc/sudoer`

###New User###
(use `galaxy` as example)

```
root $ useradd -m galaxy
root $ passwd galaxy
```

Note. `useradd` command is in `usr/sbin`. For a sudoer to add user, one need to add those path:

    /usr/local/sbin:/sbin:/bin:/usr/sbin:/root/bin

However, one can import the environment of root through the following steps:

1. `visudo` and adding these lines:
    
    ```
# Defaults specification
Defaults    secure_path = /sbin:/bin:/usr/sbin:/usr/bin
# Added by liang. 2012.08.09
# This will import the PATH of root when using sudo.
```

2. find `Default env_keep= '…'`

    ```
Defaults    env_keep = "COLORS DISPLAY HOSTNAME HISTSIZE INPUTRC KDEDIR \
                        LS_COLORS MAIL PS1 PS2 QTDIR USERNAME \
                        LANG LC_ADDRESS LC_CTYPE LC_COLLATE LC_IDENTIFICATION \
                        LC_MEASUREMENT LC_MESSAGES LC_MONETARY LC_NAME LC_NUMERIC \
                        LC_PAPER LC_TELEPHONE LC_TIME LC_ALL LANGUAGE LINGUAS \
                        _XKB_CHARSET XAUTHORITY PATH"                        
# BY Liang  Defaults env_keep += "PATH"
    ```

Reference: [sudo するときに sbin にパスを設定する方法](http://www.sssg.org/blogs/naoya/archives/2096)


##Disk Management##
###檢查硬碟使用量

* 列出系統可用空間 `df -h`

    ```
liang@localhost ~ $ df -h
檔案系統              容量  已用 可用 已用% 掛載點
/dev/sda1             1.4T  778G  500G  61% /
tmpfs                  71G     0   71G   0% /dev/shm
tmpfs                  30G   23G  7.7G  75% /var/lib/mysql_ramdisk
```

* 列出當下資料夾所在的磁區的可用空間 `df -h .`

    ```
liang@localhost ~ $ df -h .
檔案系統              容量  已用 可用 已用% 掛載點
/dev/sda1             1.4T  778G  500G  61% /
```

###檢查各資料夾、檔案大小

* 列出當下資料夾大小 `du -sh .`

    ```
liang@localhost ~ $ du -sh .
39G	.
```

* 列出底下各個資料夾大小（時間較長）`du -sh ./*`

    ```
liang@localhost ~ $ du -sh ./*
517M	./galaxy-dist
92K	    ./galaxy_runtime_log.txt
95M	    ./local
8.0K	./public_html
20G	    ./read_1
20G	    ./read_2
```

<!-- EOF -->
