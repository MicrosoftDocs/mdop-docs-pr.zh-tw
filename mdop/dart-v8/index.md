---
title: 診斷與修復工具組8管理員指南
description: 診斷與修復工具組8管理員指南
author: dansimp
ms.assetid: 33685dd7-844f-4864-b504-3ef384ef01de
ms.pagetype: mdop
ms.mktglfcycl: support
ms.sitesec: library
ms.prod: w10
ms.date: 10/03/2017
ms.openlocfilehash: c4f4e7cb49b89759acc4c3c738ff74a4a197b120
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10795529"
---
# <span data-ttu-id="a49f4-103">診斷與修復工具組8管理員指南</span><span class="sxs-lookup"><span data-stu-id="a49f4-103">Diagnostics and Recovery Toolset 8 Administrator's Guide</span></span>


<span data-ttu-id="a49f4-104">Microsoft Diagnostics 與修復工具組（DaRT）8.0 可讓您診斷並修復無法啟動或如預期開始出現問題的電腦。</span><span class="sxs-lookup"><span data-stu-id="a49f4-104">Microsoft Diagnostics and Recovery Toolset (DaRT) 8.0 lets you diagnose and repair a computer that cannot be started or that has problems starting as expected.</span></span> <span data-ttu-id="a49f4-105">您可以使用 DaRT 8.0 來復原無法使用的最終使用者電腦、診斷可能的問題原因，以及快速修復無法引導或封鎖的電腦。</span><span class="sxs-lookup"><span data-stu-id="a49f4-105">By using DaRT 8.0, you can recover end-user computers that have become unusable, diagnose probable causes of issues, and quickly repair unbootable or locked-out computers.</span></span> <span data-ttu-id="a49f4-106">必要時，您也可以快速還原重要的遺失檔案，以及偵測及移除惡意程式碼，即使電腦不在線上也一樣。</span><span class="sxs-lookup"><span data-stu-id="a49f4-106">When it is necessary, you can also quickly restore important lost files and detect and remove malware, even when the computer is not online.</span></span>

<span data-ttu-id="a49f4-107">DaRT 8.0 可讓您在國際標準組織（ISO）和 Windows Imaging （WIM）檔案格式中建立 DaRT 復原影像，並將影像燒制至 CD、DVD 或 USB。</span><span class="sxs-lookup"><span data-stu-id="a49f4-107">DaRT 8.0 lets you create a DaRT recovery image in International Organization for Standardization (ISO) and Windows Imaging (WIM) file formats and burn the image to a CD, DVD, or USB.</span></span> <span data-ttu-id="a49f4-108">接著，您可以使用復原圖像檔案，並將它們部署在本機或遠端分區或復原分區中。</span><span class="sxs-lookup"><span data-stu-id="a49f4-108">You can then use the recovery image files and deploy them locally or to a remote partition or a recovery partition.</span></span>

<span data-ttu-id="a49f4-109">DaRT 8.0 是 Microsoft 桌面優化套件（MDOP）的重要部分，可供軟體保證客戶減少軟體安裝成本的動態解決方案，讓應用程式可以傳送成服務，並協助管理及控制企業桌面環境。</span><span class="sxs-lookup"><span data-stu-id="a49f4-109">DaRT 8.0 is an important part of the Microsoft Desktop Optimization Pack (MDOP), a dynamic solution available to Software Assurance customers that helps reduce software installation costs, enables delivery of applications as services, and helps manage and control enterprise desktop environments.</span></span>

<a href="" id="getting-started-with-dart-8-0"></a>[<span data-ttu-id="a49f4-110">開始使用 DaRT 8.0</span><span class="sxs-lookup"><span data-stu-id="a49f4-110">Getting Started with DaRT 8.0</span></span>](getting-started-with-dart-80-dart-8.md)  

<span data-ttu-id="a49f4-111">[關於 DaRT 8.0](about-dart-80-dart-8.md) **|**[DaRT 8.0](release-notes-for-dart-80--dart-8.md) **|** 的版本資訊[關於 DaRT 8.0 SP1](about-dart-80-sp1.md) **|**[DaRT 8.0 SP1](release-notes-for-dart-80-sp1.md) **|** 的版本資訊[關於 DaRT 8.1](about-dart-81.md) **|**[DaRT 8.1](release-notes-for-dart-81.md) **|** 的版本資訊[DaRT 8.0](overview-of-the-tools-in-dart-80-dart-8.md) **|** 中的工具概述[DaRT 8.0 的協助工具](accessibility-for-dart-80-dart-8.md)</span><span class="sxs-lookup"><span data-stu-id="a49f4-111">[About DaRT 8.0](about-dart-80-dart-8.md)**|**[Release Notes for DaRT 8.0](release-notes-for-dart-80--dart-8.md)**|**[About DaRT 8.0 SP1](about-dart-80-sp1.md)**|**[Release Notes for DaRT 8.0 SP1](release-notes-for-dart-80-sp1.md)**|**[About DaRT 8.1](about-dart-81.md)**|**[Release Notes for DaRT 8.1](release-notes-for-dart-81.md)**|**[Overview of the Tools in DaRT 8.0](overview-of-the-tools-in-dart-80-dart-8.md)**|**[Accessibility for DaRT 8.0](accessibility-for-dart-80-dart-8.md)</span></span>

<a href="" id="planning-for-dart-8-0"></a>[<span data-ttu-id="a49f4-112">規劃 DaRT 8.0</span><span class="sxs-lookup"><span data-stu-id="a49f4-112">Planning for DaRT 8.0</span></span>](planning-for-dart-80-dart-8.md)  

<span data-ttu-id="a49f4-113">[規劃部署 DaRT 8.0](planning-to-deploy-dart-80-dart-8.md) **|**[DaRT 8.0 支援](dart-80-supported-configurations-dart-8.md) **|** 的設定[規劃以建立 DaRT 8.0 恢復影像](planning-to-create-the-dart-80-recovery-image-dart-8.md) **|**[規劃如何儲存和部署 DaRT 8.0 恢復影像](planning-how-to-save-and-deploy-the-dart-80-recovery-image-dart-8.md) **|**[DaRT 8.0 規劃檢查清單](dart-80-planning-checklist-dart-8.md)</span><span class="sxs-lookup"><span data-stu-id="a49f4-113">[Planning to Deploy DaRT 8.0](planning-to-deploy-dart-80-dart-8.md)**|**[DaRT 8.0 Supported Configurations](dart-80-supported-configurations-dart-8.md)**|**[Planning to Create the DaRT 8.0 Recovery Image](planning-to-create-the-dart-80-recovery-image-dart-8.md)**|**[Planning How to Save and Deploy the DaRT 8.0 Recovery Image](planning-how-to-save-and-deploy-the-dart-80-recovery-image-dart-8.md)**|**[DaRT 8.0 Planning Checklist](dart-80-planning-checklist-dart-8.md)</span></span>

<a href="" id="deploying-dart-8-0"></a>[<span data-ttu-id="a49f4-114">部署 DaRT 8.0</span><span class="sxs-lookup"><span data-stu-id="a49f4-114">Deploying DaRT 8.0</span></span>](deploying-dart-80-dart-8.md)  

<span data-ttu-id="a49f4-115">[將 DaRT 8.0 部署到管理員電腦](deploying-dart-80-to-administrator-computers-dart-8.md) **|**[建立 DaRT 8.0 恢復影像](creating-the-dart-80-recovery-image-dart-8.md) **|**[部署 DaRT 恢復影像](deploying-the-dart-recovery-image-dart-8.md) **|**[DaRT 8.0 部署檢查清單](dart-80-deployment-checklist-dart-8.md)</span><span class="sxs-lookup"><span data-stu-id="a49f4-115">[Deploying DaRT 8.0 to Administrator Computers](deploying-dart-80-to-administrator-computers-dart-8.md)**|**[Creating the DaRT 8.0 Recovery Image](creating-the-dart-80-recovery-image-dart-8.md)**|**[Deploying the DaRT Recovery Image](deploying-the-dart-recovery-image-dart-8.md)**|**[DaRT 8.0 Deployment Checklist](dart-80-deployment-checklist-dart-8.md)</span></span>

<a href="" id="operations-for-dart-8-0"></a>[<span data-ttu-id="a49f4-116">適用於 DaRT 8.0 的操作</span><span class="sxs-lookup"><span data-stu-id="a49f4-116">Operations for DaRT 8.0</span></span>](operations-for-dart-80-dart-8.md)  

<span data-ttu-id="a49f4-117">[使用 DaRT 8.0](recovering-computers-using-dart-80-dart-8.md) **|** 復原電腦[使用故障分析](diagnosing-system-failures-with-crash-analyzer--dart-8.md) **|** 程式診斷系統失敗[DaRT 8.0](security-and-privacy-for-dart-80-dart-8.md) **|** 的安全性和隱私權[使用 PowerShell 管理 DaRT 8.0](administering-dart-80-using-powershell-dart-8.md)</span><span class="sxs-lookup"><span data-stu-id="a49f4-117">[Recovering Computers Using DaRT 8.0](recovering-computers-using-dart-80-dart-8.md)**|**[Diagnosing System Failures with Crash Analyzer](diagnosing-system-failures-with-crash-analyzer--dart-8.md)**|**[Security and Privacy for DaRT 8.0](security-and-privacy-for-dart-80-dart-8.md)**|**[Administering DaRT 8.0 Using PowerShell](administering-dart-80-using-powershell-dart-8.md)</span></span>

<a href="" id="technical-reference-for-dart-8-0"></a>[<span data-ttu-id="a49f4-118">DaRT 8.0 技術參考資料</span><span class="sxs-lookup"><span data-stu-id="a49f4-118">Technical Reference for DaRT 8.0</span></span>](technical-reference-for-dart-80-new-ia.md)  

[<span data-ttu-id="a49f4-119">Microsoft Diagnostics 與修復工具組（DaRT）使用者應該使用 Microsoft Defender Offline （WDO）進行惡意程式碼偵測--></span><span class="sxs-lookup"><span data-stu-id="a49f4-119">Microsoft Diagnostics and Recovery Toolset (DaRT) users should use Microsoft Defender Offline (WDO) for malware detection--></span></span>](use-windows-defender-offline-wdo-for-malware-protection-not-dart.md)

<a href="" id="troubleshooting-dart-8-0"></a>[<span data-ttu-id="a49f4-120">疑難排解 DaRT 8.0</span><span class="sxs-lookup"><span data-stu-id="a49f4-120">Troubleshooting DaRT 8.0</span></span>](troubleshooting-dart-80-dart-8.md)  

### <span data-ttu-id="a49f4-121">其他資訊</span><span class="sxs-lookup"><span data-stu-id="a49f4-121">More Information</span></span>

<a href="" id="how-do-i-get-mdop"></a>[<span data-ttu-id="a49f4-122">我要如何取得 MDOP</span><span class="sxs-lookup"><span data-stu-id="a49f4-122">How Do I Get MDOP</span></span>](https://go.microsoft.com/fwlink/?LinkId=322049)  
<span data-ttu-id="a49f4-123">取得有關如何下載 DaRT 的資訊。</span><span class="sxs-lookup"><span data-stu-id="a49f4-123">Get information about how to download DaRT.</span></span>

<a href="" id="release-notes-for-dart-8-0"></a>[<span data-ttu-id="a49f4-124">DaRT 8.0 版本資訊</span><span class="sxs-lookup"><span data-stu-id="a49f4-124">Release Notes for DaRT 8.0</span></span>](release-notes-for-dart-80--dart-8.md)  
<span data-ttu-id="a49f4-125">針對 DaRT 8.0，查看更新的產品資訊和已知問題。</span><span class="sxs-lookup"><span data-stu-id="a49f4-125">View updated product information and known issues for DaRT 8.0.</span></span>

<a href="" id="mdop-techcenter-page"></a>[<span data-ttu-id="a49f4-126">MDOP 技術中心頁面</span><span class="sxs-lookup"><span data-stu-id="a49f4-126">MDOP TechCenter Page</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=225286)  
<span data-ttu-id="a49f4-127">瞭解最新的 MDOP 資訊和資源。</span><span class="sxs-lookup"><span data-stu-id="a49f4-127">Learn about the latest MDOP information and resources.</span></span>

<a href="" id="mdop-information-experience"></a>[<span data-ttu-id="a49f4-128">MDOP 資訊體驗</span><span class="sxs-lookup"><span data-stu-id="a49f4-128">MDOP Information Experience</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=236032)  
<span data-ttu-id="a49f4-129">尋找您的 MDOP 技術的檔、影片及其他資源。</span><span class="sxs-lookup"><span data-stu-id="a49f4-129">Find documentation, videos, and other resources for MDOP technologies.</span></span> <span data-ttu-id="a49f4-130">您也可以[將意見反應傳送給我們](mailto:MDOPDocs@microsoft.com)，或在[Facebook](https://go.microsoft.com/fwlink/p/?LinkId=242445)或[Twitter](https://go.microsoft.com/fwlink/p/?LinkId=242447)上關注我們來瞭解更新。</span><span class="sxs-lookup"><span data-stu-id="a49f4-130">You can also [send us feedback](mailto:MDOPDocs@microsoft.com), or learn about updates by following us on [Facebook](https://go.microsoft.com/fwlink/p/?LinkId=242445) or [Twitter](https://go.microsoft.com/fwlink/p/?LinkId=242447).</span></span>

 

 





