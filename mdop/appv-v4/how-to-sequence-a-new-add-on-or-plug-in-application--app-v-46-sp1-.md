---
title: 如何排序新附加元件或外掛應用程式 (App-V 4.6 SP1)
description: 如何排序新附加元件或外掛應用程式 (App-V 4.6 SP1)
author: dansimp
ms.assetid: 2c018215-66e5-4301-8481-159891a6b35b
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 5c5bc1e96ead819459cda3879127ebdaf94f0ee7
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10801125"
---
# 如何排序新附加元件或外掛應用程式 (App-V 4.6 SP1)


使用下列程式，透過應用程式虛擬化（App-v） Sequencer 來建立新的附加元件或外掛程式虛擬應用程式套件。 附加元件或外掛程式應用程式是一種可擴展應用程式功能的應用程式，例如 Microsoft Excel 的外掛程式。 如需有關您可以排序之應用程式類型的詳細資訊，請參閱[如何判斷要順序的應用程式類型（app-v 4.6 SP1）](how-to-determine-which-type-of-application-to-sequence---app-v-46-sp1-.md)。

**重要**  
在執行下列程式之前，請先在執行排序器的電腦上本機安裝上層應用程式。 例如，如果您要為 Microsoft Excel 的外掛程式進行排序，請在執行排序器的電腦上本機安裝 Microsoft Excel。 您也可以在安裝了應用程式的目的電腦上，將上層應用程式安裝在同一個目錄中。 如果外掛程式或附加元件要與現有的虛擬應用程式套件搭配使用，請在建立父虛擬應用程式套件時，將應用程式安裝在所用的同一個虛擬應用程式磁碟機上。



您也可以使用現有的虛擬應用程式套件做為父應用程式。 若要使用現有的虛擬應用程式套件，請在為新的附加元件或外掛程式排序前，先使用下列程式。

1.  若要啟動 app-v 排序器，請在執行 app-v 排序器的電腦上，按一下 [**開始**  /  **所有程式**]  /  **microsoft application virtualization**  /  **microsoft application virtualization 排序**器。

2.  若要將現有的套件展開至執行排序器的電腦，請按一下 [**工具**]，將 [  /  **套件] 展開至 [本機系統**

3.  流覽並選取您要展開的套件（**sprj**檔案），然後按一下 [**開啟**]。 繼續執行下列程式。

**為新的附加元件或外掛程式應用程式排序**

1.  若要啟動 app-v 排序器，請在執行 app-v 排序器的電腦上，按一下 [**開始**  /  **所有程式**]  /  **microsoft application virtualization**  /  **microsoft application virtualization 排序**器。

2.  若要啟動 [**建立新套件] 嚮導**，請按一下 [**建立新的虛擬應用程式套件**]。 若要建立套件，請選取 [**建立套件（預設）**]，然後按一下 **[下一步]**。

3.  在 [**準備電腦**] 頁面上，查看可能導致套件建立失敗的問題，或套件中包含不必要的資料。 我們強烈建議您在繼續進行之前先解決所有潛在問題。 修正衝突之後，若要更新顯示的資訊，**請按一下 [** 重新整理]。 解決所有可能的問題之後，請按 **[下一步]**。

    **重要**  
    如果您需要停用病毒掃描軟體，請掃描執行 sequencer 的電腦，以確保無法在套件中新增不需要的或惡意的檔案。



4.  在 [**應用程式類型**] 頁面上，選取 [**附加元件] 或 [外掛程式]**，然後按 **[下一步]**。

    如需可排序之應用程式類型的詳細資訊，請參閱[如何判斷要順序的應用程式類型（app-v 4.6 SP1）](how-to-determine-which-type-of-application-to-sequence---app-v-46-sp1-.md)。

5.  在 [**選取安裝程式**] 頁面上，按一下 **[流覽]** ，然後指定附加元件或外掛程式的安裝檔。 如果應用程式沒有關聯的安裝程式檔案，且您打算手動執行所有安裝步驟，請選取 [**選取此選項以執行自訂安裝**] 核取方塊，然後按一下 [**下一步]**。

6.  在 [**選取主要**頁面] 上，按一下 **[流覽]** ，然後指定上層應用程式。

    **重要**  
    如果您要安裝的附加元件或外掛程式無法在本機安裝，請停止這裡，然後在執行排序器的電腦上安裝應用程式。 例如，您必須在本機安裝 Microsoft Excel 外掛程式的**Excel.exe**程式檔。



~~~
Click **Next**.
~~~

7. 在 [**套件名稱**] 頁面上，指定將與套件建立關聯的名稱。 使用名稱，協助識別將新增到套件中之應用程式的用途和版本。 套件名稱也會顯示在 App V 管理主控台中。 **安裝位置**會顯示應用程式的虛擬化路徑，將會安裝應用程式。 若要編輯此位置，請選取 **[編輯] （[高級]）**。

   **重要**  
   編輯應用程式虛擬化路徑是一個高級的配置工作。 您應該完全瞭解變更路徑的意義。 對於大部分的應用程式，我們建議預設路徑。



~~~
Click **Next**.
~~~

8. 在 [**安裝**] 頁面上，當排序器和應用程式安裝程式準備好時，請安裝外掛程式或增益集應用程式，讓排序器可以監視安裝程式。 使用應用程式的安裝程式來執行安裝。 如果安裝時必須執行其他安裝檔案，請按一下 [**執行**]，然後找出並執行其他安裝檔案。 完成安裝後，請選取 [**我已完成安裝**]，然後按一下 **[下一步]**。

9. 在 [**安裝報告**] 頁面上，您可以查看剛剛排序的虛擬應用程式套件的相關資訊。 如需**其他資訊**所顯示之資訊的詳細說明，請按兩下該事件。 審閱資訊之後，請按 **[下一步]**。

10. 如果您已完成安裝並設定虛擬應用程式，請在 [**自訂**] 頁面上選取 [**立即停止**]，然後跳至此程式的步驟14。 如果您想要自訂以下清單中的任何專案，請選取 [**自訂**]。

    -   編輯與應用程式相關聯的檔案類型關聯。

    -   準備虛擬套件以進行流式處理。 [資料流程] 可改善虛擬應用程式套件在目的電腦上執行時的體驗。

    -   指定可以執行此套件的作業系統。

    按 **\[下一步\]**。

11. 在 [**編輯快速鍵**] 頁面上，您可以選擇性地設定將與套件中各種應用程式相關聯的檔案類型關聯（FTA）。 若要建立新的 FTA，請在左窗格中，選取並展開您要自訂的應用程式，然後按一下 [**新增**]。 在 [**新增檔案類型關聯**] 對話方塊中，為新的 FTA 提供必要的資訊。 在應用程式底下，選取 [**快速鍵**]，查看與應用程式相關聯的快捷方式資訊。 在 [**位置**] 窗格中，您可以查看圖示檔資訊。 若要編輯現有的 FTA，請按一下 [**編輯**]。 若要移除 FTA，請選取 FTA，然後按一下 [**移除**]。 按 **\[下一步\]**。

12. 在 [**流式處理**] 頁面上，執行每個程式，讓它能在目的電腦上優化並更有效率地執行。 可能需要幾分鐘的時間，所有應用程式才會執行。 在所有應用程式都已執行之後，請關閉每個應用程式，然後按 **[下一步]**。

   **注意**  
   如果您想要在此步驟中停止載入應用程式，請在 [**應用程式啟動**] 對話方塊中，按一下 [**停止**]，然後選取其中一個核取方塊、[**停止所有應用程式**] 或 [**僅停止此應用程式**]。



13. 在 [**目標作業系統**] 頁面上，指定可執行此套件的作業系統。 若要在您的環境中啟用所有受支援的作業系統來執行這個套件，請選取 [**允許此套件在任何作業系統上執行**] 核取方塊。 若要將這個套件設定為只在特定作業系統上執行，請選取 [**只允許此套件在下列作業系統上執行**] 核取方塊，然後選取可以執行此套件的作業系統。 按 **\[下一步\]**。

14. 在 [**建立套件**] 頁面上，若要修改套件但不儲存，請選取 **[繼續使用套件編輯器修改套件但不儲存**] 核取方塊。 選取此選項會在 Sequencer 視窗中開啟套件，讓您可以在儲存套件之前加以修改。 按 **\[下一步\]**。

   若要立即儲存套件，請選取 [**立即儲存套件**] 的預設值。 或者，您也可以選取 [**批註**]，以新增將與套件相關聯的批註。 若要識別套件的版本及其他資訊，可以使用 [批註]。 也會顯示預設的**儲存位置**。 若要變更預設位置，請按一下 **[流覽]** ，然後指定新的位置。 隨即會顯示未壓縮的套件大小。 如果套件大小超過 4 GB （未壓縮），且您打算將套件資料流程資料流至目的電腦，您必須選取 [**壓縮套件**]。 按一下 \[建立\]****。

15. 在 [**完成**] 頁面上，在您回顧了 [**成功的虛擬應用程式套件報告**] 窗格中顯示的資訊後，按一下 [**關閉**]。 [**成功的虛擬應用程式套件報告**] 窗格中顯示的資訊也適用于此程式步驟14（名為**Reports.xml**的檔案）中所指定的目錄。

   套件現在可在 sequencer 中取得。 按一下 **[編輯 \ [套件名稱 \]** 編輯套件屬性。 如需有關修改套件的詳細資訊，請參閱[如何修改現有的虛擬應用程式套件（app-v 4.6 SP1）](how-to-modify-an-existing-virtual-application-package--app-v-46-sp1-.md)。

   **重要**  
   成功建立虛擬應用程式套件之後，您就無法在執行排序器的電腦上執行虛擬應用程式套件。



## 相關主題


[Application Virtualization Sequencer 的工作 (App-V 4.6 SP1)](tasks-for-the-application-virtualization-sequencer--app-v-46-sp1-.md)

[如何判斷要順序的應用程式類型（App-v 4.6 SP1）](how-to-determine-which-type-of-application-to-sequence---app-v-46-sp1-.md)








