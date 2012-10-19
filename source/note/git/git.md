<script src='js/jquery.min.js' type="text/javascript"></script>
<script src='js/jquery.timeago.js' type="text/javascript"></script>

#Git Tutorial#

Last modified time: <span id='lastedit'></span>

Back to [Index](index.html)

----
##Reference Links
* Host place: [Github](https://github.com/), [Bitbucket](https://bitbucket.org/)
* Tutorial: 
    * [寫給大家的 Git 教學](http://littleb.tc/slides/2012/everyone/git.html)
    * [Pro Git](http://git-scm.com/doc)
    * [巴哈姆特Git教學情報](http://forum.gamer.com.tw/C.php?page=1&bsn=60292&snA=1154)
    * 從個版上轉貼，見本文下方       
* Tutorial - Installation:
	* Windows: [安裝筆記 (msysgit, TortoiseGit)](http://blog.crboy.net/2012/05/git-on-windows.html), [Github for Windows](http://windows.github.com/)
	* Mac: Xode 4 will install Git by default
* Advanced tutorial - Rebase:
    * [使用 git rebase 避免無謂的 merge](http://ihower.tw/blog/archives/3843/)
    * [Rebasing Merge Commits in Git](http://notes.envato.com/developers/rebasing-merge-commits-in-git/)
    * [Master and **origin/master** have diverged, how to **undiverge** branches?](http://stackoverflow.com/questions/2452226/master-branch-and-origin-master-have-diverged-how-to-undiverge-branches)        
* Advanced tutorial (etc):
    * [Good branching model](http://nvie.com/posts/a-successful-git-branching-model/)        
* Management Tool:
    * Mac: [SourceTree](http://www.sourcetreeapp.com/), [GitX](http://gitx.frim.nl/)
    * Win: [msysgit](http://msysgit.github.com/), [TortoiseGit](http://code.google.com/p/tortoisegit/)

----
##Commands 

###Simple Workflow
1. 首先要設定好 .gitignore2. 在bitbucket上先建好repo再git clone下來比較方便，不用設remote3. `branch master` 為穩定的版本，`branch develop`為平常開發在更新的版本，剩下的branch就看大家要開發什麼功能就開一個新的branch來做它4. 主要由一個人來管理branch的merge 最好這個人可以看著branch的分支表，這樣比較清楚要下什麼指令5. 根據我的經驗，rebase在遠端同步上比較麻煩，merge比較清楚。所以正常的開發都會使用merge，所以統整的流程像這樣

###Commands Lookup Table
####Initialization
        git branch develop        git checkout develop                    # git checkout -b develop####Working        git branch <new function>        git checkout develop        git add . -v                    # -v 可以看到add了什麼                                        # 使用 git reset HEAD^ 還原add步驟        git commit -m "message"         # 因為windows的關係，message要用英文        git push -u origin <new function>       # push新的branch時要下的指令        git push HEAD                   # 平常下的指令 git pull 也可以####Merge branches 
(都給一個人做也沒有關系XD)
        git fetch -v        git branch -a                   # 看一下有沒有把新的branch加下來        gitk                            # 可以看一下樹狀圖                                        # 或者進入資料夾用tortoiseGit按右鍵                                        # 選擇 "…log" (這個好用很多！)        現在要把 <tobeMerged> 整合到 <merge>, Ex <tobeMerge> = <new fnt>                                                 <merge> = develop
        現在要把 <tobeMerged> 整合到 <merge>, Ex <tobeMerge> = <new fnt>                                                 <merge> = develop        git checkout <merge>        git merge <tobeMerged>####Update branch "develop"（每個人都要的，因為每個人開發的新功能，都會被整併到這條"develop"主開發線）        git fetch -v        git checkout branch        git merge origin/branch        gitk or tortoiseGit->log        # 此時develop, origin/develop兩標籤                                          會指著同一個commit表示同步完成！        # 如果出現 merge error 此時並不會完成merge的步驟，          那些被merge的檔案會被更動(像是加入 >>>>>>> <<<<<<等字樣)而Stage          所以更動完所以merge怪異點後，可以commit一次就會完成同步。

####Upload branch \<new fnt\>
        git add .        git commit -m "Something usefull message"        # 最好做到一個程度就要commit，多幾次無妨        git branch -a        git push -u origin <new fnt>    # 把新的branch上傳時會這樣        git push                        # 之後branch的更新三不五時，或是有奇怪的現象時
        git remote prune origin         # 把untracked branches給移除

<script>
  //select all out-site link, make them opened in new tab.
  $('a[href^="http://"], a[href^="https://"]').attr('target', '_blank'); 
  var dateObj = new Date(new Date(document.lastModified).getTime()+8*3600*1000);
jQuery(document).ready(function($) {
  $('#lastedit').text(jQuery.timeago(dateObj)).css({
      'font-weight':    'bold',
      'color':          '#C71585'
  });
});
</script>
