---
title: 更新 MED-V 2.0
description: 更新 MED-V 2.0
author: dansimp
ms.assetid: beea2f54-42d7-4a17-98e0-d243a8562265
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 62e8987ec511783422b8dd336dd4f3be2008c9b2
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "10810131"
---
# 更新 MED-V 2.0


針對 Microsoft 企業版桌面虛擬化（MED-V）2.0 套用適當的安全性更新，以協助保護您的系統。

## 更新 MED-V


您可以將 MED-V 更新、由最終使用者互動式更新，或使用電子軟體發佈系統以無提示的方式進行。 安裝 MED-V 主機代理程式升級 MED-V 主機代理程式，並視需要更新 MED-V 工作區。 MED-V 主機代理程式和來賓代理程式會保持同步。如果應用程式是從 MED-V 工作區執行，而 MED-V 主機代理程式正在更新，則必須重新開機主機電腦才能完成更新。 如果沒有任何應用程式正在執行，MED-V 會自動重新開機，且升級完成後不會重新開機主機電腦。

如果您是使用電子軟體發佈系統來更新 MED-V，您可以控制重新開機行為。 若要這樣做，請在安裝 MED-V\_HostAgent\_Setup.exe 時，在命令提示字元上輸入**REBOOT = "ReallySuppress"** ，以取消重新開機。 然後，設定電子軟體發佈系統來捕獲3010傳回代碼（這表示需要重新開機）並執行設定重新開機行為。

## 相關主題


[MED-V 技術參考資料](technical-reference-for-med-v.md)

 

 





