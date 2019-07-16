(2019/03/08)
# 什麼是軟性功能凍結?

軟性功能凍結是 edk2 的開發過程中的穩定階段的開始。到了軟性功能凍結的日期，開發者們必須
傳送他們的修補到信件列表 **和** 接收到正面的維護者評論 `Reviewed-by` 或 `Acked-by` 標籤)。
這意味著功能，特別是不平凡的，必須在軟性功能凍結日之前已經由維護者所同意。

在軟性功能凍結和 [硬性功能凍結](HardFeatureFreeze) 之間，之前經過審核和單元測試的功能可能被附加(或合併)到主要分支上，進行整合性測試。
在軟性功能凍結之後才被發佈 **或** 審核的功能添加或啟動補丁將被延遲到即將到來的[穩定版標籤](EDK-II#穩定版標籤)。

# 通過軟性功能凍結我應該做甚麼?

作為一個維護者，對任何你正聚焦到下一版[穩定版標籤](EDK-II#穩定版標籤)的功能，你應該確保跟這功能有相依性的補丁你已經檢視和同意過。

當一個開發者，你可能應該聚焦在早於軟性凍結日期至少 1-2 週的日期。而這將給維護者足夠時間去審核和測試你的補丁。對於主要功能你可能應該與維護者溝通關於這(功能的)主要意圖。這也會有幫助假如你去:

- 為 [TianoCore 功能需求](https://bugzilla.tianocore.org/enter_bug.cgi?product=Tianocore%20Feature%20Requests) 產品輸入一個 Bugzilla 票證。

- (可選擇性) 寫下描述功能和動機的頁面在 [edk2 維基](Home)。

- 在 [發布計畫維基頁面](EDK-II-Release-Planning) 裡，連結你的 Bugzilla 項目和/或功能維基頁面。

- 盡早完成這一切，讓你可以與維護者一起進行審查流程。

(這定義被模組化在 QEMU 的 [軟性功能凍結](https://wiki.qemu.org/Planning/SoftFeatureFreeze) 之後)

# 通告軟性功能凍結

對主動開發循環的建議時間表被展示在 [EDK II 發布計畫](EDK-II-Release-Planning) 文章裡。在軟性功能凍結之前不久，一個通告電子郵件被寄送給 [edk2-devel](https://lists.01.org/mailman/listinfo/edk2-devel) 郵件列表。 這通告被在 `EDK II 發行` 章節裡名列 [Maintainer.txt](https://github.com/tianocore/edk2/blob/master/Maintainers.txt) 的維護者之一來公布。

# 原文
# What is the soft feature freeze?

The soft feature freeze is the beginning of the stabilization phase of edk2's
development process. By the date of the soft feature freeze,  developers must
have sent their patches to the mailing list **and** received positive
maintainer reviews (`Reviewed-by` or `Acked-by` tags). This means that
features, and in particular non-trivial ones, must have been accepted by
maintainers before the soft freeze date.

Between the soft feature freeze and the [hard feature
freeze](HardFeatureFreeze), previously reviewed and unit-tested features may be
applied (or merged) to the master branch, for integration testing. Feature
addition or enablement patches posted **or** reviewed after the soft feature
freeze will be delayed until after the upcoming [stable
tag](EDK-II#stable-tags).

# What should I do by the soft feature freeze?

As a maintainer, for any feature that you're targeting to the next [stable
tag](EDK-II#stable-tags), you should make sure that you've reviewed and
accepted the patches related to the feature.

As a developer, you probably should target a date that is at least 1-2 weeks
earlier than the soft freeze date. This will give the maintainer enough time to
review and test your patches. For major features you should probably
communicate with the maintainer about their intentions. It also helps if you:

- Enter a Bugzilla ticket for the [TianoCore Feature
  Requests](https://bugzilla.tianocore.org/enter_bug.cgi?product=Tianocore%20Feature%20Requests)
  product.

- Optionally, write a Feature page in the [edk2 wiki](Home) describing the
  feature and the motivation.

- On the [release planning wiki page](EDK-II-Release-Planning), link to your
  Bugzilla entry and/or the feature wiki page.

- Do all this early enough that you can work with the maintainer to get the
  review process underway.

(This definition is modeled after QEMU's [soft feature
freeze](https://wiki.qemu.org/Planning/SoftFeatureFreeze).)

# Announcing the soft feature freeze

The proposed schedule for the active development cycle is shown in the [EDK II
Release Planning](EDK-II-Release-Planning) article. Shortly before the soft
feature freeze, an announcement email is sent to the
[edk2-devel](https://lists.01.org/mailman/listinfo/edk2-devel) mailing list.
The announcement is posted by one of the maintainers that are listed in
[Maintainers.txt](https://github.com/tianocore/edk2/blob/master/Maintainers.txt),
in section `EDK II Releases`.
