---
title: 如何使用 App-V 5.0 為新應用程式進行序列化
description: 如何使用 App-V 5.0 為新應用程式進行序列化
author: dansimp
ms.assetid: a263fa84-cd6d-4219-a5c2-eb6a553b826c
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 13fdda066f79d918da1970e0cab6c1d6e60f6585
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10800414"
---
# 如何使用 App-V 5.0 為新應用程式進行序列化


**若要在開始排序前查看或執行**

1.  判斷您想要建立的虛擬化應用程式套件類型：

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">應用程式類型</th>
    <th align="left">描述</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Standard</p></td>
    <td align="left"><p>建立包含應用程式或應用程式套件的套件。 這是大部分應用程式類型的首選選項。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>附加元件或外掛程式</p></td>
    <td align="left"><p>建立可延伸標準應用程式功能的套件，例如 Microsoft Excel 的外掛程式。 此外，您也可以將外掛程式用於本機已安裝的應用程式，或針對使用連線群組連結的其他套件使用外掛程式。</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>中介軟體</p></td>
    <td align="left"><p>建立標準應用程式所需的套件（例如，JAVA）。 中介軟體套件是使用連線群組來連結到其他套件。</p></td>
    </tr>
    </tbody>
    </table>



2.  將所有所需的安裝檔案複製到執行排序器的電腦上。

3.  將應用程式排序前，請先製作虛擬環境的備份影像，然後在您完成應用程式的排序之後，每次都要還原到該影像。

4.  檢查下列專案：

    -   如果應用程式安裝程式將安全性存取變更為新的或現有的檔案或目錄，就不會在套件中捕獲這些變更。

    -   如果已針對虛擬化套件的目標卷停用短路徑，您也必須將套件排序為已建立且仍有停用短路徑的磁片。 它不可以是系統音量。

    -   從 App-v 5.0 SP3 開始，主要虛擬應用程式目錄（PVAD）是隱藏的，但您可以將它重新開啟。 請參閱[關於 App-V 5.0 SP3](about-app-v-50-sp3.md#bkmk-pvad-hidden)。

**為新的標準應用程式排序**

1.  在執行排序器的電腦上，按一下 [**所有程式**]，然後按一下 [ **microsoft application**virtualization]，然後按一下 [ **microsoft application virtualization 排序**器]。

2.  在排序器中，按一下 [**建立新的虛擬應用程式套件**]。 選取 [**建立套件（預設）**]，然後按一下 **[下一步]**。

3.  在 [**準備電腦**] 頁面上，查看可能導致套件建立失敗的問題，或可能導致套件包含不必要的資料。 繼續進行之前，您應該先解決所有潛在問題。 進行任何修正之後 **，按一下 [** 重新整理] 以顯示更新的資訊。 解決所有可能的問題之後，請按 **[下一步]**。

    **重要**  
    如果您需要停用病毒掃描軟體，您應該先掃描執行 sequencer 的電腦，以確保無法將不想要的或惡意檔案新增到套件中。



4.  在 [**應用程式類型**] 頁面上，按一下 [**標準應用程式（預設）** ] 核取方塊，然後按一下 **[下一步]**。

5.  在 [**選取安裝程式**] 頁面上，按一下 **[流覽]** ，然後指定應用程式的安裝檔。

    **注意**  
    如果指定的應用程式安裝程式修改檔案或目錄的安全性存取（現有或新），將不會將相關的變更捕獲到套件中。



~~~
If the application does not have an associated installer file and you plan to run all installation steps manually, select the **Perform a Custom Installation** check box, and then Click **Next**.
~~~

6. 在 [**套件名稱**] 頁面上，輸入將與套件建立關聯的名稱。 使用名稱，協助識別將新增到套件中之應用程式的用途和版本。 套件的名稱會顯示在 App-v 5.0 管理主控台中。

   **主要虛擬應用程式目錄**會顯示應用程式將在目的電腦上安裝的路徑。 若要指定此位置，請選取 **[流覽]**。

   **注意**  
   從 App-v 5.0 SP3 開始，主要虛擬應用程式目錄（PVAD）是隱藏的，但您可以將它重新開啟。 請參閱[關於 App-V 5.0 SP3](about-app-v-50-sp3.md#bkmk-pvad-hidden)。



~~~
**Important**  
The primary application virtual directory should match the installation location for the application that is being sequenced. For example, if you install Notepad to **C:\\Program Files\\Notepad**; you should configure **C:\\Program Files\\Notepad** as your primary virtual directory. Alternatively, you can choose to set **C:\\Notepad** as the primary virtual application directory, as long as during installation time, you configure the installer to install to **C:\\Notepad**. Editing the Application Virtualization path is an advanced configuration task. For most applications, the default path is recommended for the following reasons:

-   Application Compatibility. Some virtualized applications will not function correctly, or will fail to open if the directories are not configured with identical virtual directory paths.

-   Performance. Since no file system redirection is required, the runtime performance can improve.



**Tip**  
It is recommended that prior to Sequencing an application, you open the associated installer to determine the default installation directory, and then configure that location as the **Primary Virtual Application Directory**.



Click **Next**.
~~~

7. 在 [**安裝**] 頁面上，當排序器和應用程式安裝程式準備好時，您可以繼續安裝應用程式，讓排序器可以監視安裝程式。

   **重要**  
   您應該一直在安全的位置安裝應用程式，並確認在監視期間沒有其他使用者登入執行排序器的電腦。



~~~
Use the application's installation process to perform the installation. If additional installation files must be run as part of the installation, click **Run** to locate and run the additional installation files. When you are finished with the installation, select **I am finished installing**. Click **Next**.
~~~

8. 在 [**安裝**] 頁面上，請稍候，sequencer 會設定虛擬化的應用程式套件。

9. 在 [**設定軟體**] 頁面上，選擇性地執行套件中包含的程式。 此步驟可讓您在部署和執行目的電腦上的套件之前，先完成任何必要的授權或配置工作。 若要一次執行所有程式，請選取至少一個程式，然後按一下 [**全部執行**]。 若要執行特定程式，請選取該程式或程式，然後按一下 [**執行選取**的專案]。 完成所需的配置工作，然後關閉應用程式。 您可能需要等候數分鐘的時間，所有程式才會執行。

   **注意**  
   若要針對清單中無法使用的任何應用程式執行第一次使用工作，請開啟應用程式。 相關的資訊將會在此步驟中捕獲。



~~~
Click **Next**.
~~~

10. 在 [**安裝報告**] 頁面上，您可以查看您剛剛排序的虛擬化應用程式套件的相關資訊。 在 [**其他資訊**] 中，按兩下事件以取得更詳細的資訊。 若要繼續，請按 **[下一步]**。

11. 隨即會顯示 [**自訂**] 頁面。 如果您已完成安裝並設定虛擬應用程式，請選取 [**立即停止**]，然後跳至此程式的步驟14。 若要執行下列其中一項自訂作業，請選取 [**自訂**]。

    -   準備虛擬套件以進行流式處理。 [資料流程] 可改善虛擬應用程式套件在目的電腦上執行時的體驗。

    -   指定可以執行此套件的作業系統。

    按 **\[下一步\]**。

12. 在 [**流式處理**] 頁面上，執行每個程式，讓它能在目的電腦上優化並更有效率地執行。 可能需要幾分鐘的時間，所有應用程式才會執行。 在所有應用程式都已執行之後，請關閉每個應用程式，然後按 **[下一步]**。

   **注意**  
   如果您在這個步驟中沒有開啟任何應用程式，預設的流式處理方法是點播傳送。 這表示應用程式將會按位下載，直到可以開啟，然後根據背景載入的設定方式，將會載入應用程式的其餘部分。



13. 在 [**目標作業系統**] 頁面上，指定可執行此套件的作業系統。 若要允許您環境中所有受支援的作業系統執行這個套件，請選取 [**允許此套件在任何作業系統上執行**]。 若要將這個套件設定為只在特定作業系統上執行，請選取 [**只允許此套件在下列作業系統上**執行]，然後選取可以執行此套件的作業系統。 按 **\[下一步\]**。

   **重要**  
   請確定您在此處指定的作業系統是由您所排序的應用程式所支援。



14. 隨即會顯示 [**建立套件**] 頁面。 若要在不儲存的情況下修改套件，請選取 [**繼續使用套件編輯器修改套件而不儲存**]。 此選項會在 sequencer 視窗中開啟套件，讓您可以在儲存套件之前加以修改。 按 **\[下一步\]**。

   若要立即儲存套件，請選取 [**立即儲存套件**] （預設）。 新增要與套件相關聯的選擇性**批註**。 若要識別程式版本及有關套件的其他資訊，可以使用批註。

   **重要**  
   系統不支援**批註**和**描述**中不能列印的字元。



~~~
The default **Save Location** is also displayed on this page. To change the default location, click **Browse** and specify the new location. Click **Create**.
~~~

15. [**完成**] 頁面隨即出現。 視需要查看**虛擬應用程式套件報告**窗格中的資訊，然後按一下 [**關閉**]。 您也可以在建立套件之目錄中的**Report.xml**檔案中找到此資訊。

   套件現在可在 sequencer 中取得。

   **重要**  
   成功建立虛擬應用程式套件之後，您就無法在執行排序器的電腦上執行虛擬應用程式套件。



**為附加元件或外掛程式應用程式排序**

1.  

    **注意**  
    在執行下列程式之前，請先在執行排序器的電腦上本機安裝上層應用程式。 或者，如果您已將上層應用程式虛擬化，您可以按照附加元件或外掛程式工作流程中的步驟，將上層應用程式解包到電腦上。

    例如，如果您要為 Microsoft Excel 的外掛程式進行排序，請在執行排序器的電腦上本機安裝 Microsoft Excel。 您也可以在安裝了應用程式的目的電腦上，將上層應用程式安裝在同一個目錄中。 如果外掛程式或附加元件要與現有的虛擬應用程式套件搭配使用，請在建立父虛擬應用程式套件時，將應用程式安裝在所用的同一個虛擬應用程式磁碟機上。



~~~
On the computer that runs the sequencer, click **All Programs**, and then Click **Microsoft Application Virtualization**, and then click **Microsoft Application Virtualization Sequencer**.
~~~

2. *<strong><em>在 sequencer 中，按一下 [* </em> 建立新的虛擬應用程式套件] </strong> 。 選取 [**建立套件（預設）**]，然後按一下 **[下一步]**。

3. 在 [**準備電腦**] 頁面上，查看可能導致套件建立失敗的問題，或可能導致套件包含不必要的資料。 繼續進行之前，您應該先解決所有潛在問題。 進行任何修正之後 **，按一下 [** 重新整理] 以顯示更新的資訊。 解決所有可能的問題之後，請按 **[下一步]**。

   **重要**  
   如果您需要停用病毒掃描軟體，您應該先掃描執行 sequencer 的電腦，以確保無法將不想要的或惡意檔案新增到套件中。



4. 在 [**應用程式類型**] 頁面上，選取 [**附加元件] 或 [外掛程式]**，然後按 **[下一步]**。

5. 在 [**選取安裝程式**] 頁面上，按一下 **[流覽]** ，然後指定附加元件或外掛程式的安裝檔。 如果附加元件或外掛程式沒有關聯的安裝程式檔案，且您打算手動執行所有安裝步驟，請選取 [**選取此選項以執行自訂安裝**] 核取方塊，然後按一下 **[下一步]**。

6. 在 [**安裝] 主**版頁面上，確認已在執行排序器的電腦上安裝主要應用程式。 或者，您可以在執行排序器的電腦上，展開已儲存在本機的現有套件。 若要這樣做，請按一下 [**展開套件**]，然後選取套件。 展開或安裝上層程式後，請選取 **[我已安裝主要上層程式**]。

   按 **\[下一步\]**。

7. 在 [**套件名稱**] 頁面上，輸入將與套件建立關聯的名稱。 使用名稱，協助識別將新增到套件中之應用程式的用途和版本。 套件名稱將會顯示在 App-v 5.0 管理主控台中。 **主要虛擬應用程式目錄**會顯示應用程式的安裝路徑。 若要指定此位置，請輸入路徑，或按一下 **[流覽]**。

   **注意**  
   從 App-v 5.0 SP3 開始，主要虛擬應用程式目錄（PVAD）是隱藏的，但您可以將它重新開啟。 請參閱[關於 App-V 5.0 SP3](about-app-v-50-sp3.md#bkmk-pvad-hidden)。



~~~
Click **Next**.
~~~

8. 在 [**安裝**] 頁面上，當排序器和應用程式安裝程式準備好時，您可以繼續安裝外掛程式或增益集應用程式，讓排序器可以監視安裝程式。 使用應用程式的安裝程式來執行安裝。 如果安裝時必須執行其他安裝檔案，請按一下 [**執行**]，然後找出並執行其他安裝檔案。 完成安裝後，請選取 [**我已完成安裝**]，然後按一下 **[下一步]**。

9. 在 [**安裝報告**] 頁面上，您可以查看剛剛排序的虛擬應用程式套件的相關資訊。 如需**其他資訊**所顯示之資訊的詳細說明，請按兩下該事件。 審閱資訊之後，請按 **[下一步]**。

10. 隨即會顯示 [**自訂**] 頁面。 如果您已完成安裝並設定虛擬應用程式，請選取 [**立即停止**]，然後跳至此程式的步驟12。 若要執行下列其中一項自訂作業，請選取 [**自訂**]。

    -   優化套件在慢速或不可靠的網路上的執行方式。

    -   指定可以執行此套件的作業系統。

    按 **\[下一步\]**。

11. 在 [**流式處理**] 頁面上，執行每個程式，讓它能在目的電腦上優化並更有效率地執行。 [資料流程] 可改善在高延遲網路上的目的電腦上執行虛擬應用程式套件時的體驗。 可能需要幾分鐘的時間，所有應用程式才會執行。 在所有應用程式都已執行之後，請關閉每個應用程式。 您也可以選取 [**強制下載應用程式**] 核取方塊，將套件設定為必須在開啟之前完全下載。 按 **\[下一步\]**。

   **注意**  
   如有需要，您可以在此步驟中停止應用程式的載入。 在 [**應用程式啟動**] 對話方塊中，按一下 [**停止**]，然後選取其中一個核取方塊： [**停止所有應用程式**] 或 [**僅停止此應用程式**]。



12. 在 [**目標作業系統**] 頁面上，指定可執行此套件的作業系統。 若要允許您環境中所有支援的作業系統執行這個套件，請選取 [**允許此套件在任何作業系統上執行**] 核取方塊。 若要將這個套件設定為只在特定作業系統上執行，請選取 [**只允許此套件在下列作業系統上執行**] 核取方塊，然後選取可以執行此套件的作業系統。 按 **\[下一步\]**。

13. 隨即會顯示 [**建立套件**] 頁面。 若要在不儲存的情況下修改套件，請選取 **[繼續使用套件編輯器修改套件但不儲存**] 核取方塊。 此選項會在 sequencer 視窗中開啟套件，讓您可以在儲存套件之前加以修改。 按 **\[下一步\]**。

   若要立即儲存套件，請選取 **[立即儲存套件**]。 您也可以選擇新增與套件相關聯的**描述**。 描述對於識別套件的版本和其他資訊很有用。

   **重要**  
   系統不支援批註和描述中不能列印的字元。



~~~
The default **Save Location** is also displayed on this page. To change the default location, click **Browse** and specify the new location. Click **Create**.
~~~

**為中介軟體應用程式排序**

1. 在執行排序器的電腦上，按一下 [**所有程式**]，然後按一下 [ **microsoft application**virtualization]，然後按一下 [ **microsoft application virtualization 排序**器]。

2. *<strong><em>在 sequencer 中，按一下 [* </em> 建立新的虛擬應用程式套件] </strong> 。 選取 [**建立套件（預設）**]，然後按一下 **[下一步]**。

3. 在 [**準備電腦**] 頁面上，查看可能導致套件建立失敗的問題，或可能導致套件包含不必要的資料。 繼續進行之前，您應該先解決所有潛在問題。 進行任何修正之後 **，按一下 [** 重新整理] 以顯示更新的資訊。 解決所有可能的問題之後，請按 **[下一步]**。

   **重要**  
   如果您需要停用病毒掃描軟體，您應該先掃描執行 App-v 5.0 Sequencer 的電腦，以確保無法將不想要的或惡意檔案新增到套件中。



4. 在 [**應用程式類型**] 頁面上，選取 [**中介軟體**]，然後按一下 **[下一步]**。

5. 在 [**選取安裝程式**] 頁面上，按一下 **[流覽]** ，然後指定應用程式的安裝檔。 如果應用程式沒有關聯的安裝程式檔案，且您打算手動執行所有安裝步驟，請選取 [**選取此選項以執行自訂安裝**] 核取方塊，然後按一下 [**下一步]**。

6. 在 [**套件名稱**] 頁面上，輸入將與套件建立關聯的名稱。 使用名稱，協助識別將新增到套件中之應用程式的用途和版本。 套件的名稱會顯示在 App-v 5.0 管理主控台中。 **主要虛擬應用程式目錄**會顯示應用程式的安裝路徑。 若要指定此位置，請輸入路徑，或按一下 **[流覽]**。

   按 **\[下一步\]**。

7. 在 [**安裝**] 頁面上，當 sequencer 與中介軟體應用程式安裝程式準備就緒時，您可以繼續安裝應用程式，讓排序器可以監視安裝程式。 使用應用程式的安裝程式來執行安裝。 如果安裝時必須執行其他安裝檔，請按一下 [**執行**]，找出並執行其他安裝檔案。 完成安裝後，請選取 [**我已完成安裝**] 核取方塊，然後按一下 **[下一步]**。

8. 在 [**安裝**] 頁面上，請稍候，sequencer 會設定虛擬應用程式套件。

9. 在 [**安裝報告**] 頁面上，您可以查看您剛剛排序的虛擬應用程式套件的相關資訊。 在 [**其他資訊**] 中，按兩下事件以取得更詳細的資訊。 若要繼續，請按 **[下一步]**。

10. 在 [**目標作業系統**] 頁面上，指定可執行此套件的作業系統。 若要在您的環境中啟用所有受支援的作業系統來執行這個套件，請選取 [**允許此套件在任何作業系統上執行**] 核取方塊。 若要將這個套件設定為只在特定作業系統上執行，請選取 [**只允許此套件在下列作業系統上執行**] 核取方塊，然後選取可以執行此套件的作業系統。 按 **\[下一步\]**。

11. 在 [**建立套件**] 頁面上隨即出現。 若要在不儲存的情況下修改套件，請選取 [**繼續使用套件編輯器修改套件而不儲存**]。 此選項會在 sequencer 視窗中開啟套件，讓您可以在儲存套件之前加以修改。 按 **\[下一步\]**。

    若要立即儲存套件，請選取 **[立即儲存套件**]。 或者，您也可以新增要與套件相關聯的**描述**。 描述對於識別套件的程式版本和其他資訊很有用。

    **重要**  
    系統不支援批註和描述中不能列印的字元。



~~~
The default **Save Location** is also displayed on this page. To change the default location, click **Browse** and specify the new location. Click **Create**.
~~~

12. [**完成**] 頁面隨即出現。 視需要查看**虛擬應用程式套件報告**窗格中的資訊，然後按一下 [**關閉**]。 您也可以在此程式步驟11所指定之目錄中的**Report.xml**檔案中找到此資訊。

   套件現在可在 sequencer 中取得。 若要編輯套件屬性，請按一下 **[編輯 \ [套件名稱 \]]**。

   **重要**  
   成功建立虛擬應用程式套件之後，您就無法在執行排序器的電腦上執行虛擬應用程式套件。



~~~
**Got a suggestion for App-V**? Add or vote on suggestions [here](http://appv.uservoice.com/forums/280448-microsoft-application-virtualization). **Got an App-V issue?** Use the [App-V TechNet Forum](https://social.technet.microsoft.com/Forums/home?forum=mdopappv).
~~~

## 相關主題


[App-V 5.0 作業](operations-for-app-v-50.md)









