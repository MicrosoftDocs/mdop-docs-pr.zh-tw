---
title: 刪除 GPO
description: 刪除 GPO
author: dansimp
ms.assetid: 85fca371-5707-49c1-aa51-813fc3a58dfc
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 8a6419943604ee5a76d305228bb7418a8525bf33
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10802834"
---
# 刪除 GPO


[高級群組原則管理] （AGPM）可讓核准者刪除受控制的群組原則物件（GPO），並將它移至 [回收站]。

使用者帳戶必須有核准者或 AGPM 系統管理員（完全控制）角色，或高級群組原則管理中的必要許可權，才能完成此程式。 請參閱本主題中的「其他注意事項」中的詳細資料。

**刪除受控制的 GPO**

1.  在 [**群組原則管理] 主控台**樹狀結構中，按一下要管理 gpo 的林和網域中的 [**變更控制**]。

2.  在 [**內容**] 索引標籤上，按一下 [**受控**] 索引標籤以顯示受控制的 gpo。

3.  以滑鼠右鍵按一下要刪除的 GPO，然後按一下 [**刪除**]。

    -   若要將 GPO 從封存中刪除，同時在生產環境中保持不變的 GPO 部署版本，請按一下 [**僅從封存刪除 gpo] （uncontrol）**。

    -   若要從封存與生產環境中刪除 GPO，請按一下 [**從封存及生產刪除 gpo**]。

4.  輸入要顯示在 GPO 的審核追蹤中的批註，然後按一下 **[確定]**。

5.  當**進度**視窗顯示整體進度完成時，請按一下 [**關閉**]。 該 GPO 隨即會從 [**受控**] 索引標籤中移除，並顯示在 [**回收站**] 索引標籤上，可供您還原或銷毀。 如果 GPO 只是從封存中刪除，它也會顯示在 [無法**控制**] 索引標籤上。

### 其他考量

-   根據預設，您必須是 [核准者] 或 [AGPM 管理員（完全控制）]，才能刪除已部署的 GPO。 具體說來，您必須擁有**清單內容**，並刪除 GPO 的**gpo**許可權。

-   根據預設，您必須是編輯者、核准者或 AGPM 系統管理員（完全控制），才能從封存中刪除 GPO。 具體說來，您必須擁有**清單內容**，並**編輯設定**或**刪除**gpo 的 gpo 許可權。

-   若要從生產環境刪除不受管理的 GPO，而不需先進行控制，請在 [**群組原則管理] 主控台**中，按一下 [**樹林**]，按一下 [**網域**]，按一下 [ ** &lt; MyDomain &gt; **]，然後按一下 [**群群組原則物件** 以滑鼠右鍵按一下無法控制的 GPO，然後按一下 [**刪除**]。

### 其他參考資料

-   [刪除、還原或摧毀 GPO](deleting-restoring-or-destroying-a-gpo.md)

 

 





