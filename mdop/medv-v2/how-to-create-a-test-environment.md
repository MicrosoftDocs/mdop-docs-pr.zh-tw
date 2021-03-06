---
title: 如何建立測試環境
description: 如何建立測試環境
author: dansimp
ms.assetid: a0db2299-16f3-4516-8769-7d55ca4a1e98
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: ee2ab131f6003b56cce7a60ffea1cd00b067fae3
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10812266"
---
# 如何建立測試環境


以下是一些可協助您建立測試環境的步驟與指示，您可以用來在整個企業部署 MED-V 工作區套件之前先在本機進行測試。 本節提供如何手動或使用電子軟體發佈系統來建立測試環境的指導方針。

**使用 ESD 建立測試環境**

1.  使用貴公司在整個企業中部署軟體的方法，將下列必要元件部署到測試電腦。 依下列順序安裝它們：

    -   **Windows 虛擬電腦**–如果尚未安裝。 如需詳細資訊，請參閱[設定安裝必備元件](configure-installation-prerequisites.md)。

    -   **Windows 虛擬電腦新增和更新**–如果尚未安裝。 如需詳細資訊，請參閱[設定安裝必備元件](configure-installation-prerequisites.md)。

    -   **Med-v 主機代理安裝**檔案–安裝主機代理程式（med-v \ _HostAgent \ _Setup 安裝檔案）。 如需詳細資訊，請參閱[如何手動安裝 Med-v 主機代理程式](how-to-manually-install-the-med-v-host-agent.md)。

    -   **Med-v 工作區安裝程式、VHD 及安裝程式可執行檔**-在**Med-v 工作區包裝**程式中建立。 如需詳細資訊，請參閱[建立 Med-v 工作區套件](create-a-med-v-workspace-package.md)。

        **重要** VHD 與設定可執行程式必須與 MED-V 工作區安裝程式位於同一個資料夾中。 然後，透過執行 setup.exe 來安裝 MED-V 工作區安裝程式。

         

2.  在測試電腦上安裝所有元件之後，請執行 MED-V 主機代理程式，以開始第一次設定。

    按一下 [**開始**]，按一下 [**所有程式**]，按一下 [ **Microsoft 企業版桌面虛擬化**]，然後按一下 [ **med-v 主機代理程式**]。

    **記事** 如果您無法在測試電腦上實際執行 MED-V 主機代理程式，第一次電腦重新開機時，系統會自動啟動。

     

第一次安裝開始，可能需要十分鐘以上的時間才能完成。

如需在第一次執行設定時測試設定設定的相關資訊，請參閱[如何驗證第一次設定](how-to-verify-first-time-setup-settings.md)設定。

**手動建立測試環境**

1.  在本機測試環境中安裝 MED-V 主機代理程式，其中包含 MED-V 必備元件，例如包含新增和更新的 Windows 虛擬電腦。 如需詳細資訊，請參閱[如何手動安裝 Med-v 主機代理程式](how-to-manually-install-the-med-v-host-agent.md)。

2.  將 MED-V 工作區檔案複製到您的測試環境。 MED-V 工作區檔案位於您在**Med-v 工作區包裝**程式中指定的目的地資料夾。

    **重要** 在您的測試環境中，VHD 和設定可執行程式必須與 MED-V 工作區安裝程式位於相同的資料夾中。

     

3.  執行 setup.exe，即可安裝 MED-V 工作區。

4.  執行 MED-V 主機代理程式的第一次開始設定。

    按一下 [**開始**]，按一下 [**所有程式**]，按一下 [ **Microsoft 企業版桌面虛擬化**]，然後按一下 [ **med-v 主機代理程式**]。

第一次安裝開始，可能需要幾分鐘的時間才能完成，視指定的 VHD 大小而定。

您現在已準備好針對您針對 MED-V 工作區所指定的設定、應用程式發佈和 URL 重新導向來測試不同設定。

**記事** 根據預設，MED-V 會覆寫來賓中的螢幕鎖定原則。 不過，這不會造成安全性問題，因為主機電腦仍會採用螢幕鎖定原則。

 

## 相關主題


[如何驗證第一次安裝設定](how-to-verify-first-time-setup-settings.md)

[如何測試應用程式發佈](how-to-test-application-publishing.md)

[如何測試 URL 重新導向](how-to-test-url-redirection.md)

 

 





