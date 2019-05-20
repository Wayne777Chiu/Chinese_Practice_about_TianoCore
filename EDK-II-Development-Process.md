(2019/03/08)
在你的建置環境裡下載最新版 EDK II 開發專案時，先查看 [[Getting Started with EDK II]] 。

你是使用 git 的新手嗎? 如果是， [[git新手|New to git]] 頁面可能是有幫助的。

EDK II 專案的開發者流程
----------------------

1. 建設 EDK II 樹，如果你還沒有。

    * 在 [[SourceForge to Github Quick Start]] 頁面的文件

2. 創建和切換 (checkout) 一個主題分支 (topic branch) 給新的功能或臭蟲修正
    `$ git checkout -b <new-dev-branch> origin/master`

3. 在工作樹上做改變

4. 中斷工作樹上的改變到沒有破壞*二元查找* (*git bisect*) 的獨立提交。
    - [提交-分區](Commit-Partitioning "wikilink")

    - 預存所有的修正: `$ git add -u` 

    - 追蹤 (add) 新的檔案: `$ git add <path-to-new-file>`

    - 使用 git 提示去選擇預存區的改變: `$ git add -p`

5. 當寫下提交的訊息時，依循以下訂好的提交訊息模板
 
    - [提交-訊息-格式](Commit-Message-Format "wikilink")

    - 提交預存的改變: `$ git commit`

      - 加上 `-s` 參數 去自動附加署名 (Signed-off-by)標籤到提交訊息。

6. 使用在 ‘edk2\\BaseTools\\Scripts’ 目錄之下的 ‘PatchCheck.py’ 腳本來驗證提交是正確的格式

    - 要檢查最後 <N> 次感變: `$ python BaseTools/Scripts/PatchCheck.py -<N>`

      - 例如，兩個改變就會是: `$ python BaseTools/Scripts/PatchCheck.py -2`

    - 強烈建議每次提交之後都執行 PatchCheck.py。 然後你能更容易修改 (amend) 提交去改正問題。

7. 獲取最新的改變從 origin

    `$ git fetch origin`

    注意: 這是 origin/master 的更新，不是你的在地的 master 分支。 (origin/master 可能有較新的提交比 master。)

8. 重定基這個主題分支到 (onto) master 分支

    `$ git rebase origin/master`

9. 創造補丁 (patch) (系列) 到 [[edk2-devel]] 郵件列表
  
    - 清除所有舊的補丁: `$ rm *.patch`

    - 生成新的補丁檔: `$ git format-patch -M --thread origin/master`

      - 加入 `--cover-letter` 參數針對長期補丁系列。 (記得要編輯涵蓋文稿)

      - 加入 `--subject-prefix="PATCH v2` 假如你正在送出第二版本的補丁系列。

    - `$ git send-email *.patch` 

10. 基於評論的反饋來修改在地的提交(資訊)和重複步驟 3 到 9

    - 對最新的提交，你能使用 `$ git commit --amend`

    - 對多重的提交使用 `$ git rebase -i origin/master`

    - 有問題，可諮詢你在 edk2-devel或網路中繼聊天頻道上的 git 權威。

EDK II 專案的維護者流程
----------------------

1. 決定對套裝而言一個補丁是否有符合審查需求。

2. 從伺服器更新 orgin/master

    `$ git fetch origin`

3. 創建和切換到一個整合分支

    `$ git checkout -b <新的整合分支> origin/master`

4. 新增提交在一個整合分支上

    `$ git am <patch-file>`

5.  重定基提交訊息去涵蓋任何重新審定或其他的歸屬

    `$ git rebase -i origin/master`

    - 編輯行(內容)的提交利用一個 'r' 或 'reword'。 這將允許你去新增重新審定的歸屬。

5.  Rebase commit message to include any reviewed-by or other
    attributions

    `$ git rebase -i origin/master`

    - Edit lines to have an 'r' to 'reword' the commit. This will
      allow you to add the Reviewed-by attributions.

6.  Push changes to the EDK II project repository
    -   Pushing the integration branch directly to origin/master is
        preferred

    `$ git push origin HEAD:master`

    - Using the `--dry-run` parameter will show exactly what is going
      to be updated. Use this if you are paranoid. :)



# 原文
First check out [[Getting Started with EDK II]] for downloading the
latest EDK II development project with your build environment.

Are you new to using git? If so, then the [[New to git]] page may be
helpful.

The developer process for the EDK II project
--------------------------------------------

1.  Setup the EDK II tree if you do not have one

    * This is document on the [[SourceForge to Github Quick Start]] page

2.  Create and checkout a topic branch for new feature or bug fix

    `$ git checkout -b <new-dev-branch> origin/master`

3.  Make changes in the working tree

4.  Break up working tree changes into independent commits that do not
    break *git bisect*
    -   [Commit-Partitioning](Commit-Partitioning "wikilink")

    -  To stage all modifications: `$ git add -u`

    -  To add new files: `$ git add <path-to-new-file>`

    -  To have git prompt you to selectively stage changes: `$ git add -p`

5.  Follow the commit message template given below when writing commit
    messages

    - [Commit-Message-Format](Commit-Message-Format "wikilink")

    - To commit staged changes: `$ git commit`

      - Add the `-s` parameter to automatically append your
        Signed-off-by tag to the commit message.

6.  Use the ‘PatchCheck.py’ script under ‘edk2\\BaseTools\\Scripts’
    directory to verify the commits are correctly formatted

    - To check the latest <N> changes: `$ python BaseTools/Scripts/PatchCheck.py -<N>`

      - For example, 2 changes would be: `$ python BaseTools/Scripts/PatchCheck.py -2`

    - It is strongly recommended that you run PatchCheck.py after each
      commit. You can then easily amend the commit to correct any
      issues.

7.  Get the latest changes from origin

    `$ git fetch origin`

    Note: This updates origin/master, but not your local master
    branch. (origin/master may have newer commits than master.)

8.  Rebase the topic branch onto master branch

    `$ git rebase origin/master`

9. Create patch (serial) to the [[edk2-devel]] mailing list

    - Clean out any old patches: `$ rm *.patch`

    - Generate new patch files: `$ git format-patch -M --thread origin/master`

      - Add the `--cover-letter` parameter for long patch series. (Be
        sure to edit the cover-letter.)

      - Add the `--subject-prefix="PATCH v2"` if you are sending out a
        second version of the patch series.

    - `$ git send-email *.patch`

10. Modify local commits based on the review feedbacks and repeat steps
    3 to 9

    - For the latest commit, you can use `$ git commit --amend`

    - For multiple commits use `$ git rebase -i origin/master`

    - Consult your git gurus on edk2-devel or irc channel if you have
      questions.

The maintainer process for the EDK II project
---------------------------------------------

1.  Determine if a patch has met the review requirements for the package

2.  Update the origin/master from the server

    `$ git fetch origin`

3.  Create and checkout an integration branch

    `$ git checkout -b <new-integration-branch> origin/master`

4.  Add commits on the integration branch

    `$ git am <patch-file>`

5.  Rebase commit message to include any reviewed-by or other
    attributions

    `$ git rebase -i origin/master`

    - Edit lines to have an 'r' to 'reword' the commit. This will
      allow you to add the Reviewed-by attributions.

6.  Push changes to the EDK II project repository
    -   Pushing the integration branch directly to origin/master is
        preferred

    `$ git push origin HEAD:master`

    - Using the `--dry-run` parameter will show exactly what is going
      to be updated. Use this if you are paranoid. :)

Updating your master branch
---------------------------

1.  Get the latest changes from origin

    `$ git fetch origin`

2.  Change to the local master branch

    `$ git checkout master`

3.  Apply the latest server changes to you local master branch.

    `$ git rebase origin/master`

**See Also**
------------

-   [[Commit-Message-Format]]
-   [[Code-Style]]
