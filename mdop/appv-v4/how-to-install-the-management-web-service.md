---
title: 如何安裝 Management Web Service
description: 如何安裝 Management Web Service
author: dansimp
ms.assetid: cac296f5-8ca0-4ce7-afdb-859ae207d2f1
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 4b8cc1b4821cb4041d75003cf7e6ff592e1c5039
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10801353"
---
# 如何安裝 Management Web Service


使用下列程式，在網路上的目的電腦上安裝應用程式虛擬化管理 Web 服務，並使用具有本機系統管理許可權的登入帳戶。 我們建議您在 Web 服務器上安裝此元件，但這不是必要的。

**若要安裝管理 Web 服務**

1.  確認您的目的電腦上沒有安裝舊版的 Application Virtualization Web 服務。

2.  流覽至 [應用程式虛擬化系統] 設定程式在網路上的位置，請從網路執行此程式，或將其目錄複寫到目的電腦，然後按兩下 [ **Setup.exe**]。

3.  安裝精靈開啟後，請在 [**歡迎**] 頁面上，按一下 **[下一步]**。

4.  若要接受授權協定，請在 [**授權協定**] 頁面上，選取 [**我接受授權條款及條件**]，然後按一下 **[下一步]**。

5.  在 [**註冊資訊**] 頁面上，指定**使用者名稱**和組織資訊，然後按 **[下一步]**。

6.  在 [**安裝類型**] 頁面上，按一下 [**自訂**]，然後按一下 **[下一步]**。

    **記事** 如果這不是您在電腦上安裝的第一個元件，就會顯示 [**程式維護**] 頁面。 在 [**程式維護**] 頁面上，按一下 [**修改**]。

     

7.  在 [**自訂設定**] 頁面上，清除 [應用程式**Virt 管理服務**] 以外的所有 Application Virtualization System 元件，然後按 **[下一步]**。

    **記事** 如果電腦上已安裝元件，請在 [**自訂設定**] 頁面上清除該元件，即可自動將它卸載。

     

8.  在 [**資料庫伺服器**] 頁面上，按一下 **[連線至可用資料庫]**，然後按一下 **[下一步**]。

    **記事** 在生產環境中，Microsoft 假設您要連接至現有的資料庫。 如果您想要安裝資料庫，請參閱[如何安裝資料庫](how-to-install-a-database.md)。 安裝資料庫之後，請繼續執行步驟13。

     

9.  在 [**資料庫伺服器類型**] 頁面上，從清單中選取資料庫類型，然後按一下 **[下一步]**。

10. 在 [**資料庫伺服器位置**] 頁面上，從可用伺服器清單中選取資料庫伺服器，或選取 [**使用下列主機名稱**] 核取方塊，然後在 [**伺服器名稱**] 和 [**埠號碼**] 方塊中輸入資訊，然後按 **[下一步]**。

11. 在 [**選取資料庫**] 頁面上，選取您要的資料庫，然後按一下 **[下一步]**。

12. 在 [**資料庫使用者**設定] 頁面上，輸入管理 Web 服務將用來存取資料存儲區的認證，然後按一下 **[下一步]**。

13. 在 [**準備修改程式**] 頁面上，按一下 [**安裝**]。

    **記事** 如果這是您安裝的第一個元件，就會顯示 [已**準備好安裝程式**] 頁面。 在頁面上，按一下 [**安裝**]。

     

14. 在 [**安裝精靈已完成]** 頁面上，按一下 **[完成]**。

## 相關主題


[如何安裝伺服器和系統元件](how-to-install-the-servers-and-system-components.md)

 

 





