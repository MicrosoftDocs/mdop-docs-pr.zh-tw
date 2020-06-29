---
title: 如何排序新的中介軟體應用程式 (App-V 4.6 SP1)
description: 如何排序新的中介軟體應用程式 (App-V 4.6 SP1)
author: dansimp
ms.assetid: 304045c2-5e5e-4c91-b59e-a91fdf2500fb
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: b26559b8f5c451d01fefe899e96a83dd388b8140
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10801110"
---
# 如何排序新的中介軟體應用程式 (App-V 4.6 SP1)


使用下列程式，使用 Application Virtualization （App-v） Sequencer 來建立新的中介軟體虛擬應用程式套件。 中介軟體應用程式是連接軟體模組或應用程式的軟體。 如需可排序之應用程式類型的詳細資訊，請參閱[如何判斷要順序的應用程式類型（app-v 4.6 SP1）](how-to-determine-which-type-of-application-to-sequence---app-v-46-sp1-.md)。

在 App-v 中使用動態套件組合來使用這種類型的套件。 動態套件組合可讓您定義虛擬應用程式套件，以依賴另一個虛擬應用程式套件。 相依性可讓應用程式與虛擬環境中的中介軟體或外掛程式互動，這通常會造成這種互動。 這個功能非常實用，因為次應用程式套件可以與數個其他主要應用程式搭配使用，這可讓每個主要的應用程式都能參考同一個副套件。 如需如何使用動態套件組合的詳細資訊，請參閱如何在 Microsoft 技術文件庫（）中[使用動態套件組合](https://go.microsoft.com/fwlink/?LinkID=203804&clcid=0x409) https://go.microsoft.com/fwlink/?LinkID=203804&clcid=0x409) 。

**重要**  
在排序期間，如果執行 app-v 排序器的電腦是執行 Windows Vista 或 Windows 7，且在虛擬環境之外啟動重新開機，例如**開始**  /  **關閉**，則當系統提示您關閉禁止 Windows 關閉的程式時，您必須按一下 [**取消**]。 如果您按一下 [**強制關閉**]，套件建立就會失敗。 當您按一下 [**取消**] 時，app-v Sequencer 會在應用程式排序時成功記錄重新開機。



**為新的中介軟體應用程式排序**

1.  若要啟動 app-v 排序器，請在執行 app-v 排序器的電腦上，按一下 [**開始**  /  **所有程式**]  /  **microsoft application virtualization**  /  **microsoft application virtualization 排序**器。

2.  若要啟動 [**建立新套件] 嚮導**，請按一下 [**建立新的虛擬應用程式套件**]。 若要建立套件，請選取 [**建立套件（預設）**]，然後按一下 **[下一步]**。

3.  在 [**準備電腦**] 頁面上，查看可能導致套件建立失敗的問題，或套件中包含不必要的資料。 我們強烈建議您在繼續進行之前先解決所有潛在問題。 修正衝突之後，若要更新顯示的資訊，**請按一下 [** 重新整理]。 解決所有可能的問題之後，請按 **[下一步]**。

    **重要**  
    如果您需要停用病毒掃描軟體，您必須掃描執行應用程式 VSequencer 的電腦，以確保無法在套件中新增不需要的或惡意檔案。



4.  在 [**應用程式類型**] 頁面上，選取 [**中介軟體**]，然後按一下 **[下一步]**。

    如需可排序之應用程式類型的詳細資訊，請參閱[如何判斷要順序的應用程式類型（app-v 4.6 SP1）](how-to-determine-which-type-of-application-to-sequence---app-v-46-sp1-.md)。

5.  在 [**選取安裝程式**] 頁面上，按一下 **[流覽]** ，然後指定應用程式的安裝檔。 如果應用程式沒有關聯的安裝程式檔案，且您打算手動執行所有安裝步驟，請選取 [**選取此選項以執行自訂安裝**] 核取方塊，然後按一下 [**下一步]**。

6.  在 [**套件名稱**] 頁面上，指定將與套件建立關聯的名稱。 名稱可協助識別將新增到套件中之應用程式的用途和版本。 套件名稱也會顯示在 App V 管理主控台中。 **安裝位置**會顯示應用程式的虛擬化路徑，將會安裝應用程式。 若要編輯此位置，請選取 **[編輯] （[高級]）**。

    **重要**  
    編輯應用程式虛擬化路徑是一個高級的配置工作。 您應該完全瞭解變更路徑的意義。 對於大部分的應用程式，我們建議預設路徑。



~~~
Click **Next**.
~~~

7. 在 [**安裝**] 頁面上，當 sequencer 和中介軟體應用程式安裝程式準備好時，請安裝應用程式，讓排序器可以監視安裝程式。 使用應用程式的安裝程式來執行安裝。 如果安裝時必須執行其他安裝檔，請按一下 [**執行**]，找出並執行其他安裝檔案。 完成安裝後，請選取 [**我已完成安裝**] 核取方塊，然後按一下 **[下一步]**。

8. 在 [**安裝**] 頁面上，請稍候，Sequencer 會設定虛擬應用程式套件。

9. 在 [**安裝報告**] 頁面上，您可以查看剛剛排序的虛擬應用程式套件的相關資訊。 如需**其他資訊**所顯示之資訊的詳細說明，請按兩下該事件。 審閱資訊之後，請按 **[下一步]**。

10. 在 [**目標作業系統**] 頁面上，指定可執行此套件的作業系統。 若要在您的環境中啟用所有受支援的作業系統來執行這個套件，請選取 [**允許此套件在任何作業系統上執行**] 核取方塊。 若要將這個套件設定為只在特定作業系統上執行，請選取 [**只允許此套件在下列作業系統上執行**] 核取方塊，然後選取可以執行此套件的作業系統。 按 **\[下一步\]**。

11. 在 [**建立套件**] 頁面上，若要修改套件但不儲存，請選取 [**繼續使用套件編輯器來修改套件但不儲存**] 核取方塊。 選取此選項會在 Sequencer 視窗中開啟套件，讓您可以在儲存套件之前加以修改。 按 **\[下一步\]**。

   若要立即儲存套件，請選取預設值 [**立即儲存套件**] 核取方塊。 在 [**批註**] 方塊中新增要與套件相關聯的選擇性批註。 若要識別套件的版本及其他資訊，可以使用 [批註]。 也會顯示預設的**儲存位置**。 若要變更預設位置，請按一下 **[流覽]**，然後指定新的位置。 隨即會顯示未壓縮的套件大小。 如果套件大小超過 4 GB （未壓縮），且您打算將套件資料流程資料流至目的電腦，您必須選取 [**壓縮套件**]。 按一下 \[建立\]****。

12. 在 [**完成**] 頁面上，檢查 [**虛擬應用程式套件報告**] 窗格中顯示的資訊後，按一下 [**關閉**]。 在 [**虛擬應用程式套件報告**] 窗格中顯示的資訊，也可在此程式的步驟11所指定的目錄中取得，在名為**Report.xml**的檔案中提供。

   套件現在可在 Sequencer 中取得。 若要編輯套件屬性，請按一下 **[編輯 \ [套件名稱 \]]**。 如需有關修改套件的詳細資訊，請參閱[如何修改現有的虛擬應用程式套件（app-v 4.6 SP1）](how-to-modify-an-existing-virtual-application-package--app-v-46-sp1-.md)

   **重要**  
   成功建立虛擬應用程式套件之後，您就無法在執行排序器的電腦上執行虛擬應用程式套件。



## 相關主題


[Application Virtualization Sequencer 的工作 (App-V 4.6 SP1)](tasks-for-the-application-virtualization-sequencer--app-v-46-sp1-.md)

[如何判斷要順序的應用程式類型（App-v 4.6 SP1）](how-to-determine-which-type-of-application-to-sequence---app-v-46-sp1-.md)








