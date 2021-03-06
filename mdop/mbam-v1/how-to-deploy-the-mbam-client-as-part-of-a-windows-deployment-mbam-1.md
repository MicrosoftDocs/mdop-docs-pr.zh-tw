---
title: 如何將 MBAM 用戶端部署為 Windows 部署的一部分
description: 如何將 MBAM 用戶端部署為 Windows 部署的一部分
author: dansimp
ms.assetid: 8704bf33-535d-41da-b9b2-45b60754367e
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: a63311bcc93d84472ceff5c80c9222fefd5445c0
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10810839"
---
# 如何將 MBAM 用戶端部署為 Windows 部署的一部分


Microsoft BitLocker 管理和監控（MBAM）用戶端可讓系統管理員在企業中的電腦上強制執行及監視 BitLocker 磁片磁碟機加密。 您可以在電腦影像和 Windows 部署程式期間，在用戶端電腦上啟用 BitLocker 管理和加密，以將 BitLocker 用戶端整合到組織中。

**注意**  
若要查看 MBAM 用戶端系統需求，請參閱[MBAM 1.0 支援](mbam-10-supported-configurations.md)的設定。



在 Windows 部署的初始影像階段中使用 BitLocker 加密用戶端電腦，可以降低 MBAM 實現的管理負荷。 這個方法也可確保已部署的每個電腦都已執行 BitLocker 且設定正確。

**警告**  
本主題說明如何使用 [登錄編輯程式] 變更 Windows 登錄。 如果您不正確地變更 Windows 登錄，可能會導致嚴重的問題，可能需要重新安裝 Windows。 變更登錄前，您應該先製作一份登錄檔案（系統 .dat 和使用者 .dat）的備份複本。 Microsoft 不能保證變更註冊表時可能會發生的問題，可以解決。 變更註冊表的風險由您自行承擔。



**若要將電腦加密為 Windows 部署的一部分**

1.  如果您的組織打算在 BitLocker 中使用受信任的平臺模組（TPM）保護器或 TPM + PIN 保護器選項，您必須先啟動 TPM 晶片，然後才能開始部署 MBAM。 當您啟用 TPM 晶片時，您會在稍後的程式中避免重新開機，並確保根據貴組織的需求正確地設定 TPM 晶片。 您必須在電腦的 BIOS 中手動啟用 TPM 晶片。 如需有關如何設定 TPM 晶片的詳細資訊，請參閱製造商檔。

2.  安裝 MBAM 用戶端代理程式。

3.  我們建議您將電腦加入網域 .。。

    -   如果電腦未加入網域，則無法將恢復密碼儲存在 MBAM 金鑰復原服務中。 根據預設，除非能儲存復原金鑰，否則 MBAM 不允許進行加密。

    -   如果電腦在修復金鑰儲存在 MBAM 伺服器上之前以 [復原] 模式啟動，電腦必須是 reimaged。 沒有可用的恢復方法。

4.  以系統管理員身分開啟命令提示字元，停止 MBAM 服務，然後將服務設定為 [**手動**] 或 [按**需**]。 然後，執行下列命令：

    **net stop mbamagent**

    **sc config mbamagent start = 要求**

5.  將 MBAM 代理程式的登錄設定設為 [忽略群組原則]，並執行**僅限作業系統加密**執行此動作、執行**regedit**，然後從 c:\\program files Files\\Microsoft\\MDOP 匯入登錄機碼範本 MBAM\\MBAMDeploymentKeyTemplate.reg。

6.  在 regedit 中，移至 HKLM\\SOFTWARE\\Microsoft\\MBAM 並設定下表所列的設定。

    登錄專案

    組態設定

    DeploymentTime

    0 = 關閉

    1 = 使用部署時間原則設定（預設）

    UseKeyRecoveryService

    0 = 不使用金鑰委託（在這種情況下，不需要接下來的兩個登錄專案）。

    1 = 在金鑰還原系統中使用金鑰委託（預設）

    建議：電腦必須能夠與金鑰復原服務進行通訊。 繼續進行之前，請先確認電腦可以與服務進行通訊。

    KeyRecoveryOptions

    0 = 僅上傳復原金鑰

    1 = 上傳復原金鑰和金鑰復原套件（預設）

    KeyRecoveryServiceEndPoint

    將此值設定為金鑰復原網頁伺服器的 URL。

    範例： HTTP:// &lt; 電腦名稱稱 &gt; /MBAMRecoveryAndHardwareService/CoreService.svc。



~~~
**Note**  
MBAM policy or registry values can be set here to override the previously set values.
~~~



7. MBAM agent 會在 MBAM 用戶端部署期間重新開機系統。 當您準備好進行此重新開機時，請以系統管理員的命令提示字元執行下列命令：

   **net start mbamagent**

8. 當電腦重新開機且 BIOS 提示您接受 TPM 變更時，請接受變更。

9. 在 Windows 用戶端作業系統影像處理常式中，當您準備好要開始加密時，請重新開機 MBAM 代理服務。 接著，若要將 [開始] 設定為 [**自動**]，請以系統管理員身分開啟命令提示字元，並執行下列命令：

   **sc config mbamagent start = auto**

   **net start mbamagent**

10. 移除 [旁路] 註冊表值。 若要這樣做，請執行 regedit，流覽至 HKLM\\SOFTWARE\\Microsoft 登錄專案，以滑鼠右鍵按一下 [ **MBAM** ] 節點，然後按一下 [**刪除**]。

## 相關主題


[部署 MBAM 1.0 用戶端](deploying-the-mbam-10-client.md)









