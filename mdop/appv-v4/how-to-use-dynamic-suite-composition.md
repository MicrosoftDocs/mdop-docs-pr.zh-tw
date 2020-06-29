---
title: 如何使用動態套件組合
description: 如何使用動態套件組合
author: dansimp
ms.assetid: 24147feb-a0a8-4791-a8e5-cbe5fe13c762
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 3bff4c9721352785cf6db5c497234ceaa3c5e448
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10801015"
---
# 如何使用動態套件組合


應用程式虛擬化中的動態套件組合可讓您將應用程式定義為依存于其他應用程式，例如中介軟體或外掛程式。 這可讓應用程式與虛擬環境中的中介軟體或外掛程式互動，通常是這種情況。 這個功能非常實用，因為次應用程式套件可以與數個其他應用程式搭配使用，稱為*主要應用*程式，讓每個主要應用程式都能參考同一個輔助套件。

當您順序依賴外掛程式（例如 ActiveX 控制項）或依賴于中介軟體（JRE）等中介軟體的應用程式時，您可以使用動態套件組合。 如果使用這些相依元件的每個應用程式都需要排序（包括元件），那麼對這些元件所做的更新將需要重新排序所有主要的應用程式。 如果您將沒有元件的主要應用程式排序，然後將中介軟體或外掛程式順序排列為次要套件，則只有副套件必須更新。

這種方法的優點之一是它會縮小主要套件的大小。 另一個優點是，它可讓您更好地控制次要應用程式的存取權限。 請注意，次要應用程式可以使用正常的方式來流式處理，而且不需要完全緩存即可執行。

主要套件可以有一個以上的次要套件。 不過，只支援一個相依性層面，所以您無法將次要套件定義為相依于另一個次要套件。 此外，次要應用程式只能是中介軟體或外掛程式，不能是其他完整軟體產品。

如果您想要讓幾個主要的應用程式依賴單一的中介軟體產品，請務必測試此設定，以判斷在部署前，可能會對系統效能造成的影響。

**重要** 封裝相依性可以指定為主要應用程式的強制性。 如果副套件已標示為強制性，且在載入期間由於某些原因無法存取，則次要套件的載入將會失敗。 此外，主要的應用程式也會在使用者嘗試啟動時失敗。

 

您可以使用下列程式來建立附屬套件（適用于外掛程式或中介軟體元件），然後您就可以使用最後一個程式，在次要套件的 OSD 檔案中定義相依性。

**使用動態套件組合建立外掛程式的副套件**

1.  在使用乾淨影像設定的先後順序電腦上，安裝 Application Virtualization 排序器並儲存電腦狀態。

2.  將主要應用程式排序，並將套件儲存到伺服器上的內容資料夾中。

3.  從步驟1將先後順序電腦還原為已儲存的狀態。

4.  在先後順序的電腦上安裝並設定主要應用程式。

    **重要** 您必須指定副套件的新套件根。

     

5.  啟動 sequencer 監視階段。

6.  在先後順序的電腦上安裝外掛程式，並視需要進行設定。

7.  開啟主要的應用程式，並確認該外掛程式正常運作。

8.  在 sequencer 主機中，建立一個虛擬的應用程式來代表將包含該外掛程式的副套件，然後選取一個圖示。

9.  將套件儲存到伺服器上的內容資料夾中。

    **記事** 為了協助管理次要套件，建議套件名稱必須包含「次要套件」一詞，以強調這是不能作為獨立應用程式的套件，例如**\ [外掛程式 name \] 輔助套件**。

     

**使用動態套件組合建立中介軟體的副套件**

1.  在使用乾淨影像設定的先後順序電腦上，安裝 Application Virtualization 排序器並儲存電腦狀態。

2.  在先後順序電腦上將中介軟體安裝在本機，然後加以設定。

3.  將主要應用程式排序，並將套件儲存到伺服器上的內容資料夾中。

4.  從步驟1將先後順序電腦還原為已儲存的狀態。

5.  啟動 sequencer 以建立新的套件。

6.  啟動 sequencer 監視階段。

7.  在先後順序的電腦上安裝中介軟體應用程式，並將它設定為在一般安裝中。

8.  完成先後順序程式。

9.  將套件儲存到伺服器上的內容資料夾中。

    **記事** 為了協助管理次要套件，建議套件名稱必須包含「次要套件」一詞，以強調這是不能做為獨立應用程式的套件，例如**\ [中介軟體名稱 \] 次套件**。

     

**在主要套件中定義相依性**

1. 在伺服器上，開啟副封裝的 OSD 檔案以進行編輯。 （最好是使用 XML 編輯器來變更 OSD 檔案; 不過，您也可以使用 [記事本] 做為替代）。

2. 從該檔案複製**基本代碼 HREF**線。

3. 開啟主要套件的 OSD 檔案以進行編輯。

4. 在 <strong> &lt; &gt; </strong> ** &lt; VIRTUALENV &gt; **節結尾的 [ ** &lt; /ENVLIST &gt; ** ] 標籤末尾，在** &lt; /VIRTUALENV &gt; **標記之前插入相依性標記。

5. 在您剛建立的相依性標記之後，在次要套件中貼上 [**基本代碼 HREF** ** &lt; ] &gt; **行。

6. 如果次要套件是強制性套件，即必須在開始主要套件之前啟動，請在**CODEBASE**標記內新增**強制 = "TRUE"** 屬性。 如果不是強制性的，則可以省略屬性。

7. 插入下列專案以關閉 [相依性** &lt; ] &gt; **標記：

   **&lt;/DEPENDENCIES&gt;**

8. 查看您對 OSD 檔案所做的變更，然後儲存並關閉檔案。 下列範例顯示已新增的區段應該如何顯示。 此處顯示的標記值僅限範例。

   **&lt;VIRTUALENV&gt;**

        **&lt;ENVLIST&gt;**

   **…**

        **&lt;/ENVLIST&gt;**

        **&lt;DEPENDENCIES&gt;**

             **&lt;CODEBASE HREF="rtsp://virt\_apps/package.1/package.1.sft" GUID="D54C80FA-9DFF-459D-AA33-DD852C9FBFBA" SYSGUARDFILE="package.1\\osguard.cp"/&gt;**

             **&lt;CODEBASE HREF="rtsp://sample\_apps/package.2/sample.sft" GUID="D54C80FA-9DFF-459D-AA33-DD852C9FBFBA" SYSGUARDFILE="package.2\\osguard.cp" MANDATORY="TRUE" /&gt;**

        **&lt;/DEPENDENCIES&gt;**

   **&lt;/VIRTUALENV&gt;**

9. 如果副封裝在 OSD 檔案的** &lt; ENVLIST &gt; **區段中有任何專案，您必須將這些專案複製到主要套件中的相同區段。

## 相關主題


[如何使用 App-v 排序器建立或升級虛擬應用程式](how-to-create-or-upgrade-virtual-applications-using--the-app-v-sequencer.md)

 

 




