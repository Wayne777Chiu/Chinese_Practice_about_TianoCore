(2019/03/08)

# 如何回報安全性問題
Tianocore 專案使用的臭蟲追蹤系統是 [Tianocore Bugzilla](https://bugzilla.tianocore.org) 。必須去 [創造](https://bugzilla.tianocore.org/createaccount.cgi) 一個新帳號來輸入一個新的問題或更新已經存在的問題。新的安全性問題必須使用 **Tianocore Security Issue** 產品項來輸入。 在產品項 **Tianocore Security Issue** 裡的問題只能被 **報告者** 和 **infosec** 群組的成員來看見。 報告中請包涵你認為已經引入 (involved) 的模組的路徑和該問題的詳細描述。

額外的資訊關於 Tianocore Bugzilla 能被找到於 [報告問題](Reporting-Issues "wikilink")

# 安全性問題如何去評估

當一個安全性問題被輸入，這個問題會受到 **infosec** 群組來進行評估去決定是否屬於安全性問題。 假如認為這個問題不是一個安全性問題，那麼這個問題會被轉成一個標準問題和按照一般問題解決流程來進行。 若該問題被確認為安全性問題，**infosec** 會評估該問題的優先權、嚴重性和影響範圍。 討論、解決方式和更新都會在 Bugzilla 進行。 會決定一個公開披露的日子，當日會公開揭露問題和新增到安全性公告列表。

假如你有興趣參與 Tianocore 安全性問題的評估，那麼請寄一封想加入 Tianocore Bugzilla infosec 群組的電子請求信給 Tianocore 社群經營者或一位 Tianocore 管理員。

**注意**: 不要在郵件裡傳送任何關於安全性問題的詳細說明。

# 安全性公告

目前安全性公告的列表可以在 Gitbook:
**[安全性公告記錄檔]( https://www.gitbook.com/book/edk2-docs/security-advisory/details)**

# 原文

# How to report a Security Issue

The bug tracking system used for Tianocore projects is [Tianocore Bugzilla](https://bugzilla.tianocore.org).  An account must be [created](https://bugzilla.tianocore.org/createaccount.cgi) to enter a new issue or update exiting issues.  New security issues must be entered using the **Tianocore Security Issue** product.  Issues in the **Tianocore Security Issue** product are only visible to the **Reporter** of the issue and the members of the **infosec** group.  In your report please include the paths of the modules you believe are involved and a detailed description of the issue.

Additional information about Tianocore Bugzilla can be found in [Reporting Issues](Reporting-Issues "wikilink")

# How Security Issues are Evaluated

When a Tianocore Security Issue is entered, the issue is evaluated by the **infosec** group to determine if the issue is a security issue or not.  If it is not deemed to be a security issue, then the issue is converted to a standard issue and follows the normal issue resolution process.   If the issue is confirmed to be a security issue, then the priority, severity, and impact of the issue is assessed by the **infosec** group.  Discussions, resolution, and patches are completed within Bugzilla.  A date for public disclose is determined, and on that date the issue is made public and added to the list of Security Advisories.

If you are interested in being involved in the evaluation of Tianocore Security Issues, then please send an email request to join the Tianocore Bugzilla infosec group to the Tianocore Community Manager or one of the Tianocore Stewards.

**NOTE**: Never send any details related to a security issue in email.

# Security Advisories

List of current EDK II Security Advisories can be found at this Gitbook : 
**[Security Advisory Log]( https://www.gitbook.com/book/edk2-docs/security-advisory/details)**



