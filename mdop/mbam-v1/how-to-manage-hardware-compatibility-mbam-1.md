---
title: 如何管理硬體相容性
description: 如何管理硬體相容性
author: dansimp
ms.assetid: c74b96b9-8161-49bc-b5bb-4838734e7df5
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: cf9e2c5b2b33ea93d9834a81700bd2be8a9b9757
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10800230"
---
# 如何管理硬體相容性


在您部署 [允許硬體相容性檢查] 群組原則後，Microsoft BitLocker 管理和監控（MBAM）就可以收集用戶端電腦製造商與模型的相關資訊。 如果您設定此原則，當您在用戶端電腦上部署 MBAM 用戶端時，MBAM 代理會向 MBAM 伺服器報告電腦品牌和模型資訊。

如果貴組織的電腦硬體或電腦不支援信任的平臺模組（TPM）晶片，硬體相容性功能就很有説明。 在這些情況下，您可以使用硬體相容性功能，以確保 BitLocker 加密僅適用于支援它的電腦模型。 如果貴組織中的所有電腦都支援 BitLocker，您就不需要使用硬體相容性功能。

**記事** 根據預設，不會啟用 MBAM 硬體相容性功能。 若要啟用，請在安裝期間選取 [**管理與監視伺服器**] 功能底下的 [**硬體相容性**] 功能。 如需如何設定和設定硬體相容性的詳細資訊，請參閱[部署 MBAM 1.0 伺服器基礎結構](deploying-the-mbam-10-server-infrastructure.md)。

 

硬體相容性功能會以下列方式運作。

****

1.  MBAM 用戶端代理程式會探索基本電腦資訊，例如製造商、型號、BIOS 製造商、BIOS 版本、TPM 製造商及 TPM 版本，然後將此資訊傳遞到 MBAM 伺服器。

2.  MBAM 伺服器會產生用戶端電腦與模型的清單，讓您能夠區分那些可以或不支援 BitLocker 的那些人

3.  在企業中部署的 MBAM 用戶端代理程式會自動更新此清單，並將所有新電腦群組成，且已發現狀態為 [**未知**] 的模型。 然後，系統管理員可以使用 MBAM 管理網站來變更清單專案，將特定的電腦專案與模型指定為**相容**或**不相容**。

4.  在 MBAM 用戶端代理開始加密磁片磁碟機之前，代理程式首先驗證正在執行的硬體的 BitLocker 加密相容性。

    -   如果硬體標示為相容，就會啟動 BitLocker 加密處理常式。 MBAM 也會再次檢查電腦的硬體相容性狀態，每一天一次。

    -   如果硬體標示為不相容，則 agent 會記錄事件，並傳遞「硬體已免除」狀態，做為合規性報告的一部分。 Agent 會每隔7天檢查一次，以查看狀態是否已變更為「相容」。

    -   如果硬體標示為 [未知]，則不會開始 BitLocker 加密程式。 MBAM 用戶端代理程式將逐一重新檢查電腦的硬體相容性狀態。

**警告** 如果 MBAM 用戶端代理程式嘗試加密不支援 BitLocker 磁片磁碟機加密的電腦，電腦可能會損毀。 當貴組織擁有不支援 BitLocker 的舊版硬體時，請確定硬體相容性功能已正確設定。

 

**管理硬體相容性**

1.  開啟網頁瀏覽器，然後流覽至 Microsoft BitLocker 管理及監視網站。 選取左側功能表列中的 [**硬體**]。

2.  在右窗格中，按一下 [**高級搜尋**]，然後篩選，以顯示**功能**狀態為 [**未知**] 的所有電腦模型的清單。 隨即會顯示符合搜尋準則的電腦模型清單。 系統管理員可以在此頁面上新增、編輯或移除新的電腦類型。

3.  查看每個未知的硬體設定，以判斷是否應該將設定設為**相容**或**不相容**。

4.  選取一或多個列，然後按一下 [**設定相容**] 或 [**設定不相容**]，針對所選的電腦模型設定 BitLocker 相容性（視情況而定）。 如果設定為 [**相容**]，BitLocker 會嘗試在符合支援的模型的電腦上強制執行磁片磁碟機加密原則。 如果設定為**不相容**，BitLocker 將不會在那些電腦上強制執行磁片磁碟機加密原則。

    **記事** 將電腦模型設定為相容後，MBAM 用戶端可能需要24小時以上的時間，才能在符合該硬體模型的電腦上開始 BitLocker 加密。

     

5.  系統管理員應該定期監視硬體相容性清單，以查看由 MBAM 代理程式探索的新模型，然後將其相容性設定更新為**相容**或**不相容**（視情況而定）。

## 相關主題


[管理 MBAM 1.0 功能](administering-mbam-10-features.md)

 

 





