---
title: "优化 Visual Studio 启动时间 | Microsoft Docs"
ms.custom: 
ms.date: 01/09/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 27a265dbbb1f9426ba2dd254095c84239bbd0db7
ms.lasthandoff: 03/07/2017

---
# <a name="optimize-visual-studio-startup-time"></a>优化 Visual Studio 启动时间
理想情况下，Visual Studio 应总是尽可能快地启动。 但是，Visual Studio 扩展和开启工具窗口会对启动时间产生负面影响，因为在启动时会自动加载它们。 通过**管理 Visual Studio 性能**窗口，不仅可以查看哪些扩展和功能影响 Visual Studio 的启动时间，还可以确定它们的加载行为，以便更好地控制 Visual Studio 的启动速度。

## <a name="control-startup-behavior"></a>控制启动行为

为了避免延长启动时间，Visual Studio 2017 使用按需加载方法以避免在启动时加载扩展。 这意味着不会在 Visual Studio 启动后立即打开扩展，而是在启动后根据需要以异步方式打开。 此外，由于在之前的 Visual Studio 会话中保持工具窗口的打开状态会使启动时间变慢，因此 Visual Studio 以更智能的方式打开工具窗口，从而避免影响启动时间。

如果 Visual Studio 检测到启动速度较慢，则会弹出一条消息，提示你导致速度变慢的扩展或工具窗口。 此消息还提供了**管理 Visual Studio 性能**对话框的链接，此对话框中列出了影响启动性能的扩展和工具窗口。 通过此对话框可以更改扩展和工具窗口的设置以提高启动性能。

![管理 Visual Studio 性能 - 弹出窗口](../ide/media/vside_perfdialog_popup.PNG "管理 Visual Studio 性能 - 弹出窗口")

**管理 Visual Studio 性能**对话框有两个类别：**扩展**和**工具窗口**。

### <a name="control-extensions"></a>控制扩展
如果某个扩展使 Visual Studio 的启动变慢，那么选择它的一个扩展类型时，此扩展将显示在**管理 Visual Studio 性能**对话框中。 如果对启动时间的影响（在“影响”部分下面列出）很高，令人无法接受，则可以选择“禁用”按钮，以便在启动时始终禁用此扩展。 可以使用扩展管理器或“管理 Visual Studio 性能”对话框重新启用扩展，以用于以后的会话。

![管理 Visual Studio 性能 - 扩展](../ide/media/vside_perfdialog_extensions.PNG "管理 Visual Studio 性能 - 扩展")

除了启动扩展，你也可以禁用加载解决方案或当用户键入时加载的扩展。 只需选择场景以查看关联的扩展列表。

### <a name="control-tool-windows"></a>控制工具窗口
如果工具窗口使 Visual Studio 启动变慢，可以选择保留其默认行为（对启动速度没有任何帮助），或者选择以下两种行为之一来替代其默认行为：

- **启动时不显示窗口：**如果选择此选项，则打开 Visual Studio 时指定的工具窗口将始终关闭，即使它在上一个会话中为打开状态。 可以从菜单打开工具窗口。
- **启动时自动隐藏窗口：**如果工具窗口在上一个会话中保留打开状态，那么选择此选项将在启动时折叠工具窗口组，以避免初始化工具窗口。 如果你经常使用工具窗口，那么这是一个不错的选择。因为工具窗口仍然可用，但不会再对 Visual Studio 启动时间产生负面影响。

![管理 Visual Studio 性能 - 工具窗口](../ide/media/vside_perfdialog_toolwindows.PNG "管理 Visual Studio 性能 - 工具窗口")

如果你以后改变主意，可以在**管理 Visual Studio 性能**对话框中还原任何选项。 若要打开“管理 Visual Studio 性能”对话框，请在菜单栏上选择“帮助”->“管理 Visual Studio 性能”。

## <a name="speed-up-solution-load"></a>加速解决方案的加载

Visual Studio 2017 引入了名为**轻型解决方案加载**的新功能，可减少在 IDE 中加载大型解决方案所需的时间和内存。 如果你有包含多个 C#、VB 或 C++ 项目的大型解决方案，则启用轻型解决方案加载可能会看到显著的性能优势。

由于启用轻型解决方案加载时某些 IDE 功能不是完全可用的，因此默认情况下此功能处于关闭状态。 以下内容将帮助你决定是否启用此功能。

### <a name="enable-lightweight-solution-load"></a>启用轻型解决方案加载

可以针对整个 IDE 或单个解决方案启用轻型解决方案加载。 若要对整个 IDE 启用轻型解决方案加载，请转到“工具”->“选项”，然后转到“项目和解决方案”部分。

![“工具选项”对话框](../ide/media/VSIDE_LightweightSolutionLoad.png)

若要对单个解决方案启用轻型解决方案加载，请选择解决方案资源管理器中的顶层解决方案节点。  在“属性”窗口中，为属性“轻型加载”选择下列值之一。

- **启用：**为此解决方案启用轻型解决方案加载，而不考虑 IDE 范围的设置。
- **禁用：**为此解决方案禁用轻型解决方案加载，而不考虑 IDE 范围的设置。
- **默认：**轻型解决方案加载行为遵从 IDE 范围的设置。

![“解决方案资源管理器”](../ide/media/VSIDE_LSL Solution Setting.png)

更改轻型解决方案加载设置后，此更改将在下次加载解决方案时生效。 不需要重新启动 IDE。

### <a name="automatically-enable-lightweight-solution-load"></a>自动启用轻型解决方案加载

在 Visual Studio 2017 中打开大型解决方案时，你可能会看到一个弹出消息，提示你启用轻型解决方案加载。 仅针对包含许多 C#、VB 或 C++ 项目的解决方案才显示此消息。 选择“启用”命令即可仅对此解决方案启用轻型解决方案加载。 不会更改 IDE 范围设置。

![弹出窗口](../ide/media/VSIDE_LSL Popup.png)

你可以稍后在解决方案的“属性”窗口中禁用轻型解决方案加载。

### <a name="lightweight-solution-load-limitations"></a>轻型解决方案加载限制
启用轻型解决方案加载后，IDE 的大多数功能都完全可用。 但是，某些 IDE 功能和第三方扩展可能不完全兼容。  启用轻型解决方案加载后以下功能无法使用：

#### <a name="third-party-extensions"></a>第三方扩展
启用轻量级解决方案加载后，某些扩展可能会发生意外行为。

#### <a name="edit-and-continue"></a>编辑并继续
开始调试后“编辑并继续”功能在未加载的项目中不起作用。 在此类项目中包含的文件为只读文件，如果尝试编辑则会报告项目未加载的错误。

#### <a name="f-support"></a>F# 支持
启用轻量级解决方案加载后，F# 项目可能无法正确生成，且符号在“转到”中可能不完全可用。
