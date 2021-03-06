---
title: MBAM 1.0 用戶端部署規劃
description: MBAM 1.0 用戶端部署規劃
author: dansimp
ms.assetid: 3af2e7f3-134b-4ab9-9847-b07474ca6ac3
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: d58d6420febd2da9ee9cd4074fc8b5870285b0b4
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10811420"
---
# MBAM 1.0 用戶端部署規劃


根據您部署 Microsoft BitLocker 管理與監視（MBAM）用戶端的時間，您可以在組織中的電腦上啟用 BitLocker 加密，就像在最終使用者接收電腦或之後。 若要在最終使用者收到電腦之後啟用 BitLocker 加密，請設定 [群組原則]。 若要在最終使用者收到電腦之前啟用 BitLocker 加密，請使用企業軟體部署系統來部署 MBAM 用戶端軟體。

您可以在組織中使用一或兩個方法。 如果您同時使用這兩種方法，就可以改善合規性、報告和金鑰復原支援。

**記事** 若要查看 MBAM 用戶端系統需求，請參閱[MBAM 1.0 支援](mbam-10-supported-configurations.md)的設定。

 

## 部署 MBAM 用戶端以在電腦發佈至最終使用者之後啟用 BitLocker 加密


在您設定群組原則之後，您可以使用企業軟體部署系統產品（例如 Microsoft System Center Configuration Manager 2012 或 Active Directory 網域服務），將 MBAM 用戶端安裝 Windows 安裝程式檔案部署到目的電腦。 兩個 MBAM 用戶端安裝 Windows 安裝程式檔案是 MBAMClient-64bit.msi 並 MBAMClient-32bit.msi，這些檔案是與 MBAM 軟體一起提供的。 如需如何部署 MBAM 群組原則物件的詳細資訊，請參閱[部署 MBAM 1.0 群組原則物件](deploying-mbam-10-group-policy-objects.md)。

當您部署 MBAM 用戶端時，將電腦發佈給最終使用者之後，系統會提示使用者將其電腦加密。 這可讓 MBAM 收集資料、包含 PIN 和密碼，然後開始加密程式。

**記事** 在這個方法中，系統會提示使用者啟用並初始化受信任的平臺模組（TPM）晶片（如果先前沒有啟用的話）。

 

## 使用 MBAM 用戶端在電腦發佈至最終使用者之前啟用 BitLocker 加密


在已集中接收和設定電腦的組織中，您可以安裝 MBAM 用戶端，在每個電腦上都能管理 BitLocker 加密，然後再寫入任何使用者資料。 此程式的優點是，每個電腦都會符合 BitLocker 加密的規範。 這個方法不依賴使用者的動作，因為系統管理員已經將電腦加密。 這個案例的主要假設是，在電腦傳送給使用者之前，組織的原則會安裝公司的 Windows 影像。

如果您的組織想要使用（TPM）來加密電腦，系統管理員必須使用 TPM 保護程式來加密電腦的作業系統磁片。 如果您的組織想要使用 TPM 晶片及 PIN 保護器，系統管理員必須使用 TPM 保護程式來加密系統磁碟區標，然後在使用者第一次登入時選取 PIN。 如果您的組織決定只使用 PIN 保護器，系統管理員就不需要先加密標籤。 當使用者登入其電腦時，MBAM 會提示他們提供 PIN 或 PIN，以及它們在稍後重新開機電腦時所使用的密碼。

**記事** TPM 保護器選項要求管理員在將電腦傳送給使用者之前，接受 BIOS 提示來啟用並初始化 TPM。

 

## 相關主題


[規劃部署 MBAM 1.0](planning-to-deploy-mbam-10.md)

[部署 MBAM 1.0 用戶端](deploying-the-mbam-10-client.md)

 

 





