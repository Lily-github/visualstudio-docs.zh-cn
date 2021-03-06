---
title: “函数”视图 - 采样数据 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9084aad27d14825f4b3d0a648f0880d4db329c78
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237489"
---
# <a name="functions-view---sampling-data"></a>“函数”视图 - 采样数据
采样分析方法的“函数”报表视图列出分析运行期间采样的函数。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中增强的安全功能需要以 Visual Studio 探查器在这些平台上收集数据的方式进行重大更改。 UWP 应用也需要新的收集技术。 请参阅 [Windows 8 和 Windows Server 2012 应用程序上的性能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
|列|描述|  
|------------|-----------------|  
|**进程 ID**|分析运行的进程 ID (PID)。|  
|**进程名**|进程的名称。|  
|**模块名**|函数所在模块的名称。|  
|**模块路径**|函数所在模块的路径。|  
|**源文件**|此函数的定义所在的源文件。|  
|**函数名**|该函数的完全限定名。|  
|**函数行号**|此函数在源文件中的起始行号。|  
|**函数地址**|函数的地址。|  
|**非独占样本数**|此函数执行时收集的样本总数，即当此函数位于调用堆栈上时收集的样本数。 此数量包括在该函数调用的其他函数执行时收集的样本数。|  
|**非独占样本数百分比**|分析运行中属于此函数的非独占样本的所有样本数的百分比。|  
|**独占样本数**|此函数体中的代码执行时，即当此函数位于调用堆栈顶部时收集的样本总数。 不包括在该函数调用的其他函数中收集的样本。|  
|**独占样本数百分比**|分析运行中属于此函数的独占样本的所有样本数的百分比。|  
  
## <a name="see-also"></a>请参阅  
 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)   
 [“函数”视图 - 检测](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [“函数”视图 - 采样](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [“函数”视图](../profiling/functions-view-instrumentation-data.md)