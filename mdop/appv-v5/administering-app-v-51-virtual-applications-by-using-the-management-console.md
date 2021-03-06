---
title: 使用 Management Console 管理 App-V 5.1 虛擬應用程式
description: 使用 Management Console 管理 App-V 5.1 虛擬應用程式
author: dansimp
ms.assetid: a4d078aa-ec54-4fa4-9463-bfb3b971d724
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 63ec965519bedef08b09c961dc5d1c90e1d8d694
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10800700"
---
# 使用 Management Console 管理 App-V 5.1 虛擬應用程式


在您的環境中使用 Microsoft Application Virtualization （App-v）5.1 管理伺服器來管理套件、連線群組和套件存取。 伺服器會將應用程式圖示、快速鍵及檔案類型關聯發佈到執行 App-v 5.1 用戶端的已授權電腦。 一或多個管理伺服器通常會共用通用資料存放區，以取得設定和封裝資訊。

管理伺服器使用 Active Directory 網域服務（AD DS）群組來管理使用者授權，並安裝 SQL Server 來管理資料庫和資料存放區。

由於管理伺服器會根據需求將應用程式流式處理至使用者，因此這些伺服器非常適合擁有可靠、高頻寬局域網的系統組態。 管理伺服器包含下列元件：

-   管理伺服器–使用管理伺服器來管理套件和連線群組。

-   發佈伺服器–使用發佈伺服器將套件部署到執行 App-v 5.1 用戶端的電腦。

-   管理資料庫-使用管理資料庫來管理套件存取，併發布伺服器與管理伺服器的同步處理。

## 管理主控台任務


您可以使用 App-v 5.1 管理主控台執行的最常見工作包括：

-   [如何連線到 Management Console](how-to-connect-to-the-management-console-51.md)

-   [如何使用 Management Console 新增或升級套件](how-to-add-or-upgrade-packages-by-using-the-management-console-51-gb18030.md)

-   [如何使用 Management Console 設定對套件的存取權](how-to-configure-access-to-packages-by-using-the-management-console-51.md)

-   [如何使用 Management Console 發佈套件](how-to-publish-a-package-by-using-the-management-console-51.md)

-   [如何在 Management Console 中刪除套件](how-to-delete-a-package-in-the-management-console-51.md)

-   [如何使用 Management Console 新增或移除系統管理員](how-to-add-or-remove-an-administrator-by-using-the-management-console51.md)

-   [如何使用 Management Console 註冊及取消註冊發佈伺服器](how-to-register-and-unregister-a-publishing-server-by-using-the-management-console51.md)

-   [如何使用 App-V 5.1 Management Console 建立自訂設定檔案](how-to-create-a-custom-configuration-file-by-using-the-app-v-51-management-console.md)

-   [如何使用 Management Console 將存取權與設定傳輸到另一個套件版本](how-to-transfer-access-and-configurations-to-another-version-of-a-package-by-using-the-management-console51.md)

-   [如何使用 Management Console 自訂特定 AD 群組的虛擬應用程式延伸模組](how-to-customize-virtual-applications-extensions-for-a-specific-ad-group-by-using-the-management-console51.md)

-   [如何使用 Management Console 檢視及設定應用程式與預設虛擬應用程式延伸模組](how-to-view-and-configure-applications-and-default-virtual-application-extensions-by-using-the-management-console-beta.md)

App-v 5.1 管理主控台的主要元素包括：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">管理 [主控台] 索引標籤</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[套件] 索引標籤</p></td>
<td align="left"><p>使用 [ <strong> 套件] 索引標籤 </strong> 來新增或升級套件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[連線群組] 索引標籤</p></td>
<td align="left"><p>使用 [ <strong> 連接群組] 索引標籤 </strong> 來管理連線群組。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[伺服器] 索引標籤</p></td>
<td align="left"><p>使用 [ <strong> 伺服器] 索引標籤 </strong> 來註冊新的伺服器。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[管理員] 索引標籤</p></td>
<td align="left"><p>使用 [ <strong> 管理員] 索引標籤 </strong> 來註冊、新增或移除 app-v 5.1 環境中的系統管理員。</p></td>
</tr>
</tbody>
</table>

 

**重要** 您必須在開啟 Web 管理主控台的瀏覽器上啟用 JavaScript。

 






## <a href="" id="other-resources-for-this-app-v-5-1-deployment-"></a>此 App-v 5.1 部署的其他資源


-   [Microsoft Application Virtualization 5.1 系統管理員指南](microsoft-application-virtualization-51-administrators-guide.md)

-   [App-V 5.1 作業](operations-for-app-v-51.md)

 

 





