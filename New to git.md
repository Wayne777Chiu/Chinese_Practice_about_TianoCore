(2019/03/08)
git 新手? 這個 git 網站有一些很棒的文件:

* https://git-scm.com/doc

和如果你過去已經用 svn 作業，這頁面可能有幫助:

* https://git-scm.com/course/svn.html

EDK II git 工作流程
-------------------

參看 [[EDK II Development Process]]

一些有潛在危險的指令
-------------------

如同使用危險的 `rm -rf` 或 `del /s` 命令，git 使用有一些方面你需要小心以對。這裡是一些要小心看待的命令。

* `git reset --hard`
  
  * 這指令取得你目前的分支 (head) 和設置到另一個修訂版本。原始情況下，它設置到目前分支的最後提交。

  * 為什麼它是潛在性危險的:

    * 它將覆蓋掉檔案裡任何你尚未提交的改變。

    * 它能移動你的分支到其他地方和使你失去提交。

  * 方法去回復

    * 檔案裡未提交的改變: *記住* 沒有方法去回復這些失去的改變!

    * 失去提交: 有一個好機會你能利用這 `git reflog` 指令去回復這些提交。

* `git clean`

  * 這指令刪除沒有被你的 git 倉儲裡追跡的當地端樹檔案。

  * 為什麼它是潛在性危險的:

    * 它能刪除你尚未添加到 git 的給新功能的檔案。

  * 方法去回復

    * *記住*。 沒有方法去回復被刪除的檔案!

  * 提示:

    * 使用參數 `--dry-run` 來檢視甚麼要被刪除。

* `git merge`
     
  * 這指令合併兩個分支的歷史紀錄。

  * 現在而言，EDK II 是選擇以線性歷史紀錄來維護且不使用合併( merge )。

  * 為什麼它是潛在性危險的:

    * 當自動合併兩個分支時，git 可能偶爾去選擇到錯誤的動作。雖然很少見，這可能會導致一些改變在最新的樹裡被刪除掉。

  * 方法去回復

    * 如果合併尚未推進到上游 (upstream)，有一些方法可以回復。

      * 最保證的修正方法是透過歷史紀錄去找到你合併前的樹版本。 (有幫助的工具: `gitk`, `tig`, 或 `git log --oneline --graph`)

      * 現在，使用 `git reset --hard <good-version>`

        * 這將強制你的分支回到合併前的狀態。務必理解這個 `git reset --hard` 危險就如同之前的文字敘述那樣。

      * 你可能也可以簡化的使用 `git rebase origin/master` 去移除合併的提交。

    * 假如合併的提交被推進到上游端，那麼很不幸地它將持續在歷史紀錄裡。 這不是甚麼大不了的問題，但只是要確保合併的正確地執行。假如你發現改變真的遺失了，那麼增加新的提交來重新套用這個改變。

* `git pull`

  * 預設情況下，這 `git pull` 指令是一個 `git fetch` 後緊跟著 `git merge`。 因此，它有相同疑慮如上所述的指令 `git merge`

  * 提示: 你也能運行 `git config pull.rebase true` 來設置你的 edk2 樹，這樣 `git pull` 將是 `git fetch` 後緊跟著 `git rebase` (優於 `git merge`)

* `git push -f`

  * 這個指令 '強制' 推進一個分支。這可能強制遠程分支去覆寫它的歷史紀錄。

  * 記住: 主要的 edk2 樹可防護強制推進，而且你能設定你的 github 分支去受到同樣的保護:

    <https://github.com/blog/2051-protected-branches-and-required-status-checks>

  * 為什麼它是潛在性危險的:

    * 假如你覆寫樹上的歷史紀錄，那麼人們可能會懷疑不好的改變已經偷渡到樹裡。

    * 這一般只視為許多人們以'上游'分支為基礎來處理他們工作的壞處。

  * 方法去回復

    * 你可能能夠利用強制推進回去舊的版本假如你找的到該版本的話。

  * 對強制推進有時候是可以的

    * 對於沒有人依賴在其上的你的個人開發分支，去強制推進是可以的。事實上，最終人們會發現強制推進是一個好方式去備份在遠程伺服器上開發工作的目前狀態。


#原文
New to git? The git site has some great documentation:

* https://git-scm.com/doc

And, if you've worked with svn in the past, this page might be
helpful:

* https://git-scm.com/course/svn.html

EDK II git workflows
--------------------

See [[EDK II Development Process]]

Some Potentially Dangerous Commands
-----------------------------------

Similar to using the dangerous `rm -rf` or `del /s` commands, there
are some aspects of git usage you should be careful with. Here are a
few commands to be careful with.

* `git reset --hard`

  * This command takes your current branch (head) and sets it to
    another revision. By default, it sets it to the last commit on the
    current branch.

  * Why it is potentially dangerous:

    * It will overwrite any change in files that you have not
      committed.

    * It can move your branch to somewhere else, and make you lose
      commits.

  * Ways to recover:

    * Uncommitted changes in files: *NONE*. There is no way to recover
      these lost changes!

    * Lost commits: There is a good chance you can recover the commits
      with the `git reflog` command.

* `git clean`

  * This command deletes files in your local tree that are not tracked
    in your git repository.

  * Why it is potentially dangerous:

    * It can delete files for new features that you have not yet added
      to git.

  * Ways to recover:

    * *NONE*. There is no way to recover the deleted files!

  * Tip:

    * Use the `--dry-run` parameter to see what will be deleted.

* `git merge`

  * This command joins together the histories of two branches.

  * For now, EDK II is choosing to maintain a linear history, and not
    use merges.

  * Why it is potentially dangerous:

    * It is occasionally possible for git to choose the wrong action
      when auto-merging the two branches. Although rare, this can lead
      to some changes getting dropped in the latest tree.

  * Ways to recover:

    * If the merge has not be pushed upstream, there are a few ways to
      recover.

      * The best guaranteed way to fix things is to look through the
        history to find the tree version before your merge. (Helpful
        tools: `gitk`, `tig`, or `git log --oneline --graph`)

      * Now, use `git reset --hard <good-version>`

        * This will force your branch back to the state before the
          merge. Be sure to understand the dangers of `git reset
          --hard` as documented above.

      * You might also be able to simply use `git rebase
        origin/master` to remove the merge commit.

    * If the merged commit is pushed upstream, then unfortunately it
      will persist in history. This is not really a big deal, but just
      be sure that the merge worked correctly. If you find that
      changes were actually lost then add new commits to re-apply the
      changes.

* `git pull`

  * By default, the `git pull` command is a `git fetch` followed by a
    `git merge`. Therefore it has the same concerns as the `git merge`
    command documented above.

  * Tip:

    * You can also run `git config pull.rebase true` to set your edk2
      tree up so that `git pull` will be a `git fetch` followed by a
      `git rebase` (rather than `git merge`)

* `git push -f`

  * This command 'force' pushes a branch. This potentially can force
    the remote branch to rewrite its history.

  * Note: The main edk2 tree is protected from force pushes, and you
    can setup your github branches to be similarly protected:

    <https://github.com/blog/2051-protected-branches-and-required-status-checks>

  * Why it is potentially dangerous:

    * If you 'rewrite' the history of a tree, then people will be
      suspicious that bad changes have been snuck into the tree.

    * This is generally only considered bad for 'upstream' branches
      that many people are basing their work off of.

  * Ways to recover:

    * You might be able to force push the old version back if you can
      find out its version.

  * It's sometimes okay to force push

    * For your personal development branches where no one is depending
      on the branch, it is okay to force push. In fact, most people
      will eventually find that force pushing is a good way to backup
      the currect state of their development work on a remote server.
