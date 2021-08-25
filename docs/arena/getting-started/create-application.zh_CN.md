# 應用程式部署

### 相關要求

* {1>註冊<1}一個 Arena Cloud 帳戶 
* 相容於 {1>Arena Cloud<1} 的 Colyseus 伺服器

## 建立一個應用程式部署

您的遊戲或應用程式可以有諸多應用程式部署，其可用於分隔您的環境（Dev、Staging、Prod）和/或區域（美國東部、歐盟西部、亞太地區南部）。每個應用程式部署都有自身專屬的資源池，並可在您帳戶管理的其他部署中獨立運作。 

若要開始建立您的第一個應用程式部署...

{1>新建應用程式按鈕<1}

- 登入後，選擇儀錶板右上角的{1>建立一個新的應用程式<1}。

- 填寫申請詳情欄位並選擇您的{1>計劃<1}和{2>地區<2}

- 若您的搶先體驗電子郵件中提供了 {1>Arena 代碼<1}，請在{2>代碼<2}欄位中輸入該代碼。

{1>註冊流程<1}

- 提交並等待您的應用程式建立

!!!請注意，新應用程式部署最多可能需要 2 分鐘，具體取決於所選區域

## 應用程式儀錶板

在您新建立的應用程式上選擇{1>管理<1}，即可查看您的應用程式儀錶板。從這裡，您可以看到您的活動快照和存取工具；透過各項工具，您可以更新代碼、查看活動伺服器、重新啟動您的應用程式和查看日誌。

{1>Arena 應用程式管理視圖<1}

- {1>目前的使用情況：<1}顯示目前 CCU 以及您目前的 Arena 計劃限制（如果有）
- {1>連結：<1}可存取您應用程式的 URL 和埠口
- {1>API 密鑰：<1}應用程式的唯一參考識別碼，可用於透過 Arena Public API 存取應用程式部署
- {1>Arena 計劃：<1}您應用程式目前註冊的託管計劃。
- {1>{2>GIT 更新：<2}<1}GIT 近期更新的資訊。
- {1>{2>GIT 訊息：<2}<1}近期更新的簽入訊息。
- {1>{2>GIT 哈希：<2}<1}近期更新的哈希值。!!!請注意，{3>{4>GIT<4}<3} 詳情{5>{6>僅<6}<5}在使用 CI/CD GitSync 服務（為 Powered Ascent 和 Up Arena 計劃提供）時可見