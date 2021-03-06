---
title: 如何確保損毀分析器可以存取符號檔案
description: 如何確保損毀分析器可以存取符號檔案
author: dansimp
ms.assetid: 39e307bd-5d21-4e44-bed6-bf532f580775
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: support
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 8e0ba2fa777039e1c6ffb91dd997438d8ea50616
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10809458"
---
# 如何確保損毀分析器可以存取符號檔案


通常，調試資訊會儲存在與程式不同的符號檔案中。 當您調試已停止回應的應用程式時，您必須具備符號資訊的存取權。

當您執行 [損**毀分析**程式] 時，會自動下載符號檔案。 如果電腦沒有網際網路連線，或網路需要電腦存取 HTTP proxy 伺服器，則無法下載符號檔案。

**確保故障分析程式可以存取符號檔案**

1.  **將轉儲檔案複製到另一部電腦。** 如果由於缺少網際網路連線而無法下載符號，請將儲存體轉儲檔案複製到有網際網路連線的電腦，然後在該電腦上執行獨立的 [中斷式中斷**分析程式] 嚮導**。

2.  **從另一部電腦存取符號檔案。** 如果無法下載符號是因為沒有網際網路連線，您可以從有網際網路連線的電腦上下載符號，然後將其複製到沒有網際網路連線的電腦，或者您可以將網路磁碟機對應到本機網路上可用的符號位置。 如果您在 Windows 復原環境（WindowsRE）中執行 [當機]，您**可以在 Microsoft** Diagnostics 和復原工具集（DaRT）10復原影像中包含符號檔案。

3.  **透過 HTTP proxy 伺服器存取符號檔案。** 如果由於必須存取 HTTP proxy 伺服器而無法下載符號，請使用下列步驟來存取 HTTP proxy 伺服器。 在 DaRT 10 中，當您在 [指定符號檔案位置] 對話方塊頁面（**選用 [server： port "格式）** 標示時，[**崩潰分析工具]** 的設定會顯示在 [**指定符號檔案位置**] 對話方塊頁面上。 您可以使用這個文字方塊來指定 proxy 伺服器。 在表單** &lt; 主機名稱 &gt; ： &lt; port &gt; **中輸入 proxy 位址，其中 &lt; **主機名稱** &gt; 是 DNS 名稱或 IP 位址，而 &lt; **埠** &gt; 則是 TCP 埠號碼。 有兩種模式可讓**崩潰分析**程式執行。 以下是如何在其中每個模式中使用 proxy 設定的方法：

    -   **線上模式：** 在此模式中，如果 [proxy 伺服器] 欄位留空，嚮導就會使用 [控制台] 中的 [網際網路選項] 的 [proxy 設定]。 如果您在提供的文字方塊中輸入 proxy 位址，就會使用該位址，並會覆寫 [網際網路選項] 中的設定。

    -   Windows 復原環境（WindowsRE）：當您從 [**診斷及修復工具**]**視窗執行 [** 當機] 時，沒有預設的 proxy 位址。 如果電腦直接連線至網際網路，則不需要 proxy 位址。 因此，您可以在嚮導設定中將此欄位留白。 如果電腦未直接連線至網際網路，且位於擁有 proxy 伺服器的網路環境中，您必須在嚮導中設定 proxy 欄位，以存取符號存放區。 您可以從網路系統管理員取得 proxy 位址。 只有在公用符號存放區連線至網際網路時，才能設定 proxy 伺服器。 如果符號已在 DaRT 復原影像中，或在本機都可用，則不需要設定 proxy 伺服器。

## 相關主題


[使用損毀分析器來診斷系統失敗](diagnosing-system-failures-with-crash-analyzer-dart-10.md)

[適用於 DaRT 10 的操作](operations-for-dart-10.md)

 

 





