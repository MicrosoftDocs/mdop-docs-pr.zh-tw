---
title: 關於應用程式授權
description: 關於應用程式授權
author: dansimp
ms.assetid: 6b487641-1627-4e91-b829-04f001008176
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 546bc630b95fe52f960c7bdfb771d3e2561f9318
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10802481"
---
# 關於應用程式授權


您可以直接從應用程式虛擬化伺服器管理主控台管理應用程式授權。

## 授權類型


系統中心應用程式虛擬化系統目前支援下列授權類型：

-   [**無限制的授權**]：允許任意數量的並行使用者存取應用程式。 當您想要將企業範圍的授權與應用程式建立關聯時，此授權方法相當適合。

-   **併發授權**-可讓您定義允許使用應用程式的併發使用者數目上限。

-   [**署名授權**]：可讓您指派授權給個別使用者。 已命名的授權可以用來確保特定的使用者永遠能夠執行該應用程式。

您可以將併發與命名的授權合併至同一個應用程式。

授權預設為停用，但您可以從 [**提供者屬性**] 對話方塊的 [**提供者管道**] 索引標籤啟用它。 如需啟用和停用授權的詳細資料，請參閱[如何設定或停用應用程式授權](how-to-set-up-or-disable-application-licensing.md)。

## 提供者原則


已針對應用程式服務提供者（ASP）模型開發提供者原則。 在這個模型中，單一的 ASP 可以為多個用戶端託管單一應用程式虛擬化系統，而每個用戶端都需要保持隔離。 用戶端可能會有極大的需求，例如，一個用戶端可能需要驗證，而另一個無法進行驗證。 您可以使用提供者原則，將許可權與用戶端產生關聯，以便只有已核准的使用者才能存取每個虛擬應用程式或虛擬應用程式套件。

針對企業客戶，您可以在一或多個應用程式有嚴格的授權需求時，使用這個功能。 在這種情況下，[**提供者屬性**] 對話方塊的 [**提供者管道**] 索引標籤上已停用授權元件。

[**提供者管線**] 索引標籤也有可啟用驗證、授權（**強制存取許可權設定**）和測光（**記錄使用方式資訊**）的核取方塊。 如果您的設定有特殊需求，您可以透過按一下 [**高級**] 按鈕，撰寫您自己的管線元件，並將它們新增到系統中。

## 帳戶頒發機構


[帳戶頒發機構] 是安裝應用程式虛擬化伺服器的網域。 當您在伺服器安裝過程中進行時，系統會提示您提供功能變數名稱;系統會在已安裝電腦的網域上偵測並使用預設值。 當使用者嘗試登入系統時，系統會提示他們輸入認證，然後才能存取該網域。

應用程式虛擬化系統支援多個網域。 如果信任關係是在網域之間建立，您可以將應用程式存取權授予其他網域中的使用者群組。 使用者必須提供每個網域可識別的認證。

在應用程式虛擬化伺服器管理主控台中，您可以變更主要網域（帳戶頒發機構），以及用來存取它的認證。

## 驗證


驗證是用來確認使用者身分識別的機制。 任何擁有可識別的使用者名稱和密碼的使用者都可以存取。

在應用程式虛擬化系統中，您可以透過 [**提供者管線**] 索引標籤上的核取方塊來啟用或停用驗證。根據預設，會啟用 Windows 驗證。

## 授權


[授權] 是用來確認使用者身分識別的程式。 確認使用者的身分識別之後，系統會判斷使用者是否已獲權存取系統，以及使用者被授與哪些應用程式的存取權。 應用程式虛擬化伺服器管理主控台在 [**提供者管線**] 索引標籤上有 [**強制執行存取許可權設定**] 核取方塊，以啟用或停用授權。

在應用程式虛擬化系統中，只能將存取權授予使用者群組，不適用於個別使用者。

## 相關主題


[如何在伺服器管理主控台中管理應用程式授權](how-to-manage-application-licenses-in-the-server-management-console.md)

[如何設定或停用應用程式授權](how-to-set-up-or-disable-application-licensing.md)

[伺服器管理主控台：提供者原則節點](server-management-console-provider-policies-node.md)

 

 




