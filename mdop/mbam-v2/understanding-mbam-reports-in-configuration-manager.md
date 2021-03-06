---
title: 瞭解 Configuration Manager 中的 MBAM 報告
description: 瞭解 Configuration Manager 中的 MBAM 報告
author: dansimp
ms.assetid: b2582190-c9de-4e64-bd5a-f31ac1916f53
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 995d628cafd03c8bdd209e467c9d22169b7e03c3
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10810185"
---
# 瞭解 Configuration Manager 中的 MBAM 報告


當 Microsoft BitLocker 管理與監控（MBAM）與 Configuration Manager 整合拓朴一起安裝時，硬體合規性和報告功能會移至 Configuration Manager 基礎結構，並移至 MBAM。 當您使用 Configuration Manager 拓撲結構時，您會從 Configuration Manager （而不是從 MBAM）執行報表，而不是從 [恢復] 審核報告（您可以使用 [管理] 和 [監視] 網站繼續存取）除外。

Configuration Manager 整合拓朴的報告會顯示企業及 MBAM 管理的個別電腦和裝置的 BitLocker 合規性。 報告提供表格式資訊與圖表，並可讓您篩選報表，以從不同的觀點查看資料。

本主題中的資訊說明您從 Configuration Manager 執行的 MBAM 報告。 如需獨立拓朴 MBAM 報告的相關資訊，請參閱[瞭解 MBAM 報告](understanding-mbam-reports-mbam-2.md)。

## 在 Configuration Manager 中存取報表


若要存取 Configuration Manager 中的報告功能，請開啟**Configuration manager 主控台**。 若要顯示可用報表的清單：

-   在 Configuration Manager 2007 中，展開 [**電腦管理**] 節點，然後展開 [**報告**] 節點。

-   在 SystemCenter2012 ConfigurationManager 的 [監視] 工作區中，展開 [概覽] 底下的 [**報告**] 節點，然後按一下 **[****報告**]。

### BitLocker Enterprise 合規性儀表板

BitLocker Enterprise 合規性儀表板提供下列圖表，在整個企業中顯示 BitLocker 合規性狀態：

-   合規性狀態發佈

-   不相容的錯誤發佈

-   依磁片磁碟機類型進行合規性狀態發佈

**合規性狀態發佈**

此圓形圖顯示企業內部的電腦合規性狀態，並顯示電腦的百分比，與所選集合中擁有該符合性狀態的電腦總數。 也會顯示每個狀態的實際電腦數。 圓形圖顯示下列合規性狀態：

-   達到

-   不符合

-   使用者豁免

-   暫時使用者豁免

-   未強制執行原則

-   未知-已報告錯誤的電腦，或屬於集合一部分但未報告其合規性狀態的裝置，例如，如果它們已從組織中斷連線

**不相容的錯誤發佈**

此圓形圖顯示企業中不符合 BitLocker 磁碟機加密原則的電腦類別，並顯示每個類別中的電腦數。 每個類別百分比是從集合中不相容電腦的總數計算而來。

-   使用者已延遲加密

-   找不到相容的 TPM

-   系統磁碟分割無法使用或太大

-   原則衝突

-   正在等待 TPM 自動預配

-   發生未知的錯誤

-   無資訊-沒有安裝 MBAM 用戶端的電腦，或已安裝 MBAM 用戶端但尚未啟用的電腦，例如，服務無法運作

**依磁片磁碟機類型進行合規性狀態發佈**

此橫條圖顯示 [依磁片磁碟機類型列出目前的 BitLocker 合規性狀態]。 狀態為「符合性」和「不相容」。 會顯示 [固定資料磁碟機] 和 [作業系統磁片磁碟機] 的橫條圖。 包括沒有固定資料磁碟機的電腦，而且只會顯示作業系統磁片磁碟機列中的值。 圖表不包括已從 BitLocker 磁碟機加密原則或 "無原則" 類別獲授權的使用者。

### BitLocker 企業合規性詳細資料包表

此報告會在您的企業中顯示針對以 BitLocker 為目標的電腦集合的整個 BitLocker 規範的相關資訊。

**BitLocker Enterprise 合規性詳細資料包表字段**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">欄名稱</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>受管理的電腦</p></td>
<td align="left"><p>MBAM 管理的電腦數。</p></td>
</tr>
<tr class="even">
<td align="left"><p>符合百分比</p></td>
<td align="left"><p>企業中合規性電腦的百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>非相容性%</p></td>
<td align="left"><p>企業中不相容的電腦百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>% 的未知規範</p></td>
<td align="left"><p>合規性狀態未知的電腦百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>% 豁免</p></td>
<td align="left"><p>免除 BitLocker 加密需求的電腦所占的百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>非豁免%</p></td>
<td align="left"><p>免除 BitLocker 加密需求的電腦所占的百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>達到</p></td>
<td align="left"><p>企業中合規性電腦的百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>不相容</p></td>
<td align="left"><p>企業中不相容的電腦百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>未知的合規性</p></td>
<td align="left"><p>合規性狀態未知的電腦百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>免除</p></td>
<td align="left"><p>免除 BitLocker 加密需求的電腦總數。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>非豁免</p></td>
<td align="left"><p>未免除 BitLocker 加密需求的電腦總數。</p></td>
</tr>
</tbody>
</table>

 

**BitLocker Enterprise 合規性詳細資料包表-合規性狀態**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">合規性狀態</th>
<th align="left">免除</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>標準</p></td>
<td align="left"><p>未免除</p></td>
<td align="left"><p>根據指定的原則，電腦是不相容的。</p></td>
</tr>
<tr class="even">
<td align="left"><p>達到</p></td>
<td align="left"><p>未免除</p></td>
<td align="left"><p>根據指定的原則，電腦符合規範。</p></td>
</tr>
</tbody>
</table>

 

### BitLocker Enterprise 相容性摘要報告

您可以使用此報告類型來顯示整個企業的 BitLocker 合規性相關資訊，以及顯示針對 BitLocker 使用之電腦集合中的個別電腦的相容性。

**BitLocker Enterprise 合規性摘要報表欄位**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">欄名稱</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>受管理的電腦</p></td>
<td align="left"><p>MBAM 管理的電腦數。</p></td>
</tr>
<tr class="even">
<td align="left"><p>符合百分比</p></td>
<td align="left"><p>企業中合規性電腦的百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>非相容性%</p></td>
<td align="left"><p>企業中不相容的電腦百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>% 的未知規範</p></td>
<td align="left"><p>合規性狀態未知的電腦百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>% 豁免</p></td>
<td align="left"><p>免除 BitLocker 加密需求的電腦所占的百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>非豁免%</p></td>
<td align="left"><p>免除 BitLocker 加密需求的電腦所占的百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>達到</p></td>
<td align="left"><p>企業中合規性電腦的百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>不相容</p></td>
<td align="left"><p>企業中不相容的電腦百分比。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>未知的合規性</p></td>
<td align="left"><p>合規性狀態未知的電腦百分比。</p></td>
</tr>
<tr class="even">
<td align="left"><p>免除</p></td>
<td align="left"><p>免除 BitLocker 加密需求的電腦總數。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>非豁免</p></td>
<td align="left"><p>未免除 BitLocker 加密需求的電腦總數。</p></td>
</tr>
</tbody>
</table>

 

**BitLocker Enterprise 合規性摘要報告-電腦詳細資料**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">欄名稱</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>電腦名稱稱</p></td>
<td align="left"><p>由 MBAM 管理的使用者指定 DNS 電腦名稱稱。</p></td>
</tr>
<tr class="even">
<td align="left"><p>網功能變數名稱稱</p></td>
<td align="left"><p>用戶端電腦駐留且由 MBAM 管理的完整功能變數名稱。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>合規性狀態</p></td>
<td align="left"><p>由 MBAM 管理之電腦的整體合規性狀態。 有效的狀態是相容且不相容。 請注意，每個磁片磁碟機的相容性狀態（請參閱後面的資料表）可能表示不同的合規性狀態。 不過，這個欄位會根據指定的原則來代表符合性狀態。</p></td>
</tr>
<tr class="even">
<td align="left"><p>免除</p></td>
<td align="left"><p>此狀態表示使用者是否已免除或未免除 BitLocker 原則。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>裝置使用者</p></td>
<td align="left"><p>裝置的使用者。</p></td>
</tr>
<tr class="even">
<td align="left"><p>合規性狀態詳細資料</p></td>
<td align="left"><p>根據指定原則，電腦符合性狀態的錯誤與狀態訊息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>最後一個連絡人</p></td>
<td align="left"><p>電腦上次取得伺服器以報告合規性狀態的日期和時間。 連絡人頻率可設定（請參閱 MBAM 原則設定）。</p></td>
</tr>
</tbody>
</table>

 

### BitLocker 電腦合規性報告

使用此報告類型可收集電腦專用的資訊。 電腦合規性報告提供電腦上每個磁片磁碟機（作業系統及固定資料磁碟機）的詳細加密資訊，以及針對電腦上的每個磁片磁碟機類型所套用的原則的指示。 若要查看每個磁片磁碟機的詳細資料，請展開 [電腦名稱稱] 專案。

**記事** 報告中不會顯示 [可移動資料量] 加密狀態。

 

**BitLocker 電腦合規性報告–電腦詳細資料欄位**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">欄名稱</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>電腦名稱稱</p></td>
<td align="left"><p>由 MBAM 管理的使用者指定 DNS 電腦名稱稱。</p></td>
</tr>
<tr class="even">
<td align="left"><p>網功能變數名稱稱</p></td>
<td align="left"><p>用戶端電腦駐留且由 MBAM 管理的完整功能變數名稱。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>電腦類型</p></td>
<td align="left"><p>電腦類型。 有效類型為非便攜且可移植。</p></td>
</tr>
<tr class="even">
<td align="left"><p>作業系統</p></td>
<td align="left"><p>在 MBAM managed 用戶端電腦上找到的作業系統類型。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>整體合規性</p></td>
<td align="left"><p>由 MBAM 管理之電腦的整體合規性狀態。 有效的狀態是相容且不相容。 請注意，每個磁片磁碟機的相容性狀態（請參閱後面的資料表）可能表示不同的合規性狀態。 不過，這個欄位會根據指定的原則來代表符合性狀態。</p></td>
</tr>
<tr class="even">
<td align="left"><p>作業系統合規性</p></td>
<td align="left"><p>由 MBAM 管理之作業系統的合規性狀態。 有效的狀態是相容且不相容。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>固定資料磁碟機合規性</p></td>
<td align="left"><p>由 MBAM 管理的固定資料磁碟機的合規性狀態。 有效的狀態是相容且不相容。</p></td>
</tr>
<tr class="even">
<td align="left"><p>上次更新日期</p></td>
<td align="left"><p>電腦上次取得伺服器以報告合規性狀態的日期和時間。 連絡人頻率可設定（請參閱 MBAM 原則設定）。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>免除</p></td>
<td align="left"><p>此狀態表示使用者是否已免除或未免除 BitLocker 原則。</p></td>
</tr>
<tr class="even">
<td align="left"><p>免除的使用者</p></td>
<td align="left"><p>從 BitLocker 原則免除的使用者。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>免除日期</p></td>
<td align="left"><p>授與免除的日期。</p></td>
</tr>
<tr class="even">
<td align="left"><p>合規性狀態詳細資料</p></td>
<td align="left"><p>根據指定原則，電腦符合性狀態的錯誤與狀態訊息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>原則密碼強度</p></td>
<td align="left"><p>管理員在 MBAM 原則規格期間選取的密碼強度。 （例如，使用擴散器的128位）。</p></td>
</tr>
<tr class="even">
<td align="left"><p>原則：作業系統磁片磁碟機</p></td>
<td align="left"><p>表示 O/S 和適當的保護器類型是否需要加密。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>原則：固定資料磁片磁碟機</p></td>
<td align="left"><p>表示固定磁碟機是否需要加密。</p></td>
</tr>
<tr class="even">
<td align="left"><p>製造商</p></td>
<td align="left"><p>電腦製造商出現在電腦 BIOS 中的名稱。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>型號</p></td>
<td align="left"><p>電腦製造商模型名稱，如電腦 BIOS 中所示。</p></td>
</tr>
<tr class="even">
<td align="left"><p>裝置使用者</p></td>
<td align="left"><p>由 MBAM 管理的電腦上的已知使用者。</p></td>
</tr>
</tbody>
</table>

 

**BitLocker 電腦合規性報告–電腦卷欄位**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">欄名稱</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>磁片磁碟機盤符</p></td>
<td align="left"><p>使用者指派給特定磁片磁碟機的電腦磁碟機盤符。</p></td>
</tr>
<tr class="even">
<td align="left"><p>磁片磁碟機類型</p></td>
<td align="left"><p>磁片磁碟機類型。 有效值為作業系統磁片磁碟機及固定資料磁片磁碟機。 這些是物理磁片磁碟機，而不是邏輯磁片磁碟機。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>密碼強度</p></td>
<td align="left"><p>管理員在 MBAM 原則規格期間選取的密碼強度。</p></td>
</tr>
<tr class="even">
<td align="left"><p>保護器類型</p></td>
<td align="left"><p>透過用來加密作業系統或固定容量的原則所選取的保護者類型。 作業系統上有效的保護器類型為 [TPM] 或 [TPM + PIN]，而 [固定資料量] 則是密碼。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>保護器狀態</p></td>
<td align="left"><p>指示由 MBAM 管理的電腦已啟用原則中指定的保護器類型。 [有效] 狀態為 [開啟] 或 [關閉]。</p></td>
</tr>
<tr class="even">
<td align="left"><p>加密狀態</p></td>
<td align="left"><p>磁片磁碟機的加密狀態。 有效的狀態為 [已加密]、[未加密] 和 [加密]。</p></td>
</tr>
</tbody>
</table>

 

## 相關主題


[使用 MBAM 搭配 Configuration Manager](using-mbam-with-configuration-manager.md)

 

 





