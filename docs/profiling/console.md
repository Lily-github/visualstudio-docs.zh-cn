---
title: 控制台 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04cf166880ac8bcf83d4657b9c1c2eec1b46a14a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34690811"
---
# <a name="console"></a>控制台
VSPerfCmd.exe“Console”选项在新的命令提示符窗口中启动指定的应用程序。 “Console”只能与 VSPerfCmd“Launch”选项一起使用。 如果应用程序不是命令行应用程序，“Console”不起作用。  
  
## <a name="syntax"></a>语法  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>参数  
 无  
  
## <a name="required-options"></a>必需选项  
 只能在同时包含“Launch”选项的命令行上指定“Console”。  
  
 **Launch：**`AppName`  
 启动探查器以及由 `AppName` 指定的应用程序。  
  
## <a name="see-also"></a>请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)