---
title: MED-V 2.0 的新功能
description: MED-V 2.0 的新功能
author: dansimp
ms.assetid: 53b10bff-2b6f-463b-bdc2-5edc56526792
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 78dba25fec7ae2bb41da00902b59dcd15030f2b6
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10810113"
---
# MED-V 2.0 的新功能


Microsoft 企業版桌面虛擬化（MED-V）2.0 已演化了 Windows 7 的應用程式相容性支援，以及此案例不需要的已移除功能。 例如，諸如在 MED-V 工作區中加密、集中的 MED-V 伺服器以及 MED-V 工作區修剪傳輸等功能都已移除。

## 標準功能的變更


本節討論 MED-V 2.0 功能變更的主要區域。

### MED-V-V 工作區建立

MED-V 工作區所用的虛擬硬碟現已在 Windows 虛擬電腦中建立。 用來建立 MED-V 工作區的方法包括安裝 Windows XP SP3、更新作業系統，並準備要透過軟體管理基礎結構加以管理。

除了專有的 MED-V 工作區加密和壓縮功能之外，還會移除離線管理和修剪傳送功能。 當您建立 MED-V 工作區時，系統管理員應該在影像中準備並設定適當的應用程式和管理工具，而不是使用 MED-V 1.0 中提供的虛擬機器準備工具。

在您的 MED-V 工作區封裝期間，現在需要並驗證在 MED-V 影像上執行 Sysprep。 MED-V 工作區包裝程式提供圖形使用者介面（GUI），可引導管理員完成封裝程式。 從 MED-V 1.0 的主控台已與管理影像、管理 MED-V 工作區設定檔，以及暫存和加密 MED-V 工作區的需求搭配使用。

### MED-V 工作區部署

若要部署 MED-V 工作區，管理員現在可以充分利用其電子軟體發佈工具。 已移除 MED-V 1.0 中提供的用戶端 pull 方法，現已使用 MED-V 外的方法來傳送 MED-V 工作區。 系統管理員可以像對待任何其他應用程式套件一樣，處理 MED-V 工作區，而且可以使用現有的工具和程式來排程 MED-V 的部署和安裝。 MED-V 安裝可以悄悄地部署，而且可以在現有的軟體發佈基礎結構中輕鬆管理。

### MED-V 工作區管理

MED-V 2.0 中的 MED-V 工作區是以 Windows 虛擬電腦虛擬硬碟為基礎。 MED-V 已延伸 Windows 虛擬電腦提供的功能，不需要使用加密或特殊工具存取 MED-V 工作區，即可改善無縫體驗。

將 MED-V 部署到工作站之後，就可以使用 Windows 虛擬電腦以全螢幕模式開啟 MED-V 工作區。 這項新功能已移除針對無縫或全螢幕模式設定喜好設定的原則需求，同時還移除了需要強制全螢幕以進行診斷和疑難排解的需求。

將應用程式發佈到 MED-V 工作區後，就不會再使用設定檔來執行，而是手動輸入應用程式的路徑。 相反地，它會在來賓上安裝應用程式時自動執行。 已移除包含透過修剪傳輸傳送之影像版本的中央影像儲存庫。 相反地，MED-V 可讓系統管理員管理實際電腦等 MED-V 工作區，只要在沒有專用的 MED-V 基礎結構的複雜性的情況下，就能散佈應用程式和更新。

## MED-V 功能中的變更


MED-V 2.0 的幾個重要區域反映了下列功能的改善或新增功能。

### MED-V-V 工作區建立

必須使用 Windows 虛擬電腦建立 MED-V 工作區。 您必須先遷移現有的虛擬 PC 2007 影像。 在 MED-V 2.0 中不包含「虛擬機器準備」工具，管理員應該根據 MED-V 2.0 說明檔案來設定、更新及優化其影像。 在 MED-V 影像上執行 Sysprep 是必要的步驟，必須在封裝之前執行。

### MED-V 工作區封裝

Windows PowerShell 是 MED-V 工作區包裝程式的基礎。 此功能取代了一些舊版的主機功能，也就是 MED-V 中受管理的集中式功能。 MED-V 工作區包裝程式只會將具有適當設定和影像的虛擬硬碟封裝在一起，以便由系統管理員輕鬆部署。 您可以使用 Windows PowerShell 來提供高級功能。

### MED-V 工作區分配

MED-V 2.0 不再需要專用伺服器基礎結構，且已移除部署 MED-V 工作區的用戶端 pull 方法。 MED-V 工作區現在是使用您的電子軟體發佈基礎結構來部署，而且可以儲存在其他安裝套件所用的常見共用上。

### 第一次設定

第一次設定程式現已與 Sysprep 的標準成像慣例整合。 使用 MED-V 工作區第一次時，設定處理常式可以動態地將在 MED-V 工作區包裝程式中指定的設定動態套用至影像，因為它會開始迷你設定。 已移除主機中的 [腳本工具]，第一次安裝程式會根據管理員在 MED-V 工作區中設定的選項來進行。

### 應用程式發佈

在部署 MED-V 工作區之後，系統管理員可以在 MED-V 影像上安裝應用程式，或同時使用兩者結合。 MED-V 不會再檢查 MED-V 工作區原則以發佈應用程式，而是參照來賓上實際安裝的元件。 當應用程式安裝在來賓上時，系統會自動偵測併發布至主機 [**開始**] 功能表，且已準備好由最終使用者開始。

### URL 重新導向

MED-V 2.0 根據系統管理員設定和管理的原則，提供無縫的主機對訪客網址重新導向。 將 URL 重新導向至來賓瀏覽器之後，預設的體驗是嘗試將使用者限制在該重新導向的網站上。 這會將使用者所能執行的流覽活動最小化，而不是由系統管理員所設計。 已移除來賓對主機瀏覽器的重新導向。

### 疑難排解

MED-V 現在會利用標準主機程式來進行疑難排解。 因為 MED-V 工作區已不再加密，所以它可以在 Windows 虛擬電腦主控台內以全螢幕模式開啟，您可以在此以標準工作站的形式查看和使用它。 此外，記錄不會在本機進行加密，也不會集中記錄。 MED-V 現在會大量使用本機事件記錄，而輸出的記錄層級（從資訊到調試層級）就能輕鬆設定。 最後，我們已提供疑難排解工具，讓管理員與技術支援人員都能以圖形、匯總的方式顯示所有疑難排解選項，而且他們可以輕鬆地選取最符合其需求的活動。

MED-V 已不再以系統服務的方式執行。 相反地，它是以使用者擁有的程式的方式執行，而且只有在使用者登入時才會執行。先前由由系統擁有的服務所提供的功能，現在已在使用者端程式中提供。

## 相關主題


[MED-V 部署](deployment-of-med-v.md)

[適用於 MED-V 的操作](operations-for-med-v.md)

 

 





