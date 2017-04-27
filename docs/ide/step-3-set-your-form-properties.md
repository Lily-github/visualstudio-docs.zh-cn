---
title: "步骤 3：设置窗体属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 步骤 3：设置窗体属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

接下来，使用**“属性”**窗口来更改窗体的外观。  
  
 ![链接到视频](../data-tools/media/playvideo.png "PlayVideo") 有关本主题的视频版本，请参阅[教程 1：用 Visual Basic 创建图片查看器 \- 视频 1](http://go.microsoft.com/fwlink/?LinkId=205209) 或[教程 1：用 C\# 创建图片查看器 \- 视频 1](http://go.microsoft.com/fwlink/?LinkId=205199)。  这些视频使用 Visual Studio 的早期版本，因此在一些菜单命令和其他用户界面元素上略有差异。  但是，概念和过程与当前版本的 Visual Studio 大同小异。  
  
### 设置窗体属性  
  
1.  确保您查看的是 Windows 窗体设计器。  在 Visual Studio 集成开发环境 \(IDE\) 中，选择**“Form1.cs \[设计\]”**选项卡（或 Visual Basic 中的**“Form1.vb \[设计\]”**）。  
  
2.  选择**“Form1”**窗体中的任意位置以将其选定。  查看**“属性”**窗口，该窗口此时应显示窗体的属性。  窗体具有各种属性。  例如，可以设置前景色和背景色、窗体顶部显示的标题文本、窗体的大小和其他属性。  
  
    > [!NOTE]
    >  如果**“属性”**窗口未出现，请通过选择工具栏上的正方形**“停止调试”**按钮来停止程序或直接关闭窗口。  如果程序已停止，且仍未显示**“属性”**窗口，请在菜单栏上选择**“视图”**和**“属性窗口”**。  
  
3.  选中窗体后，在**“属性”**窗口中找到**“Text”**属性。  根据列表排序的方式，您可能需要向下滚动。  选择**“Text”**，键入“图片查看器”，然后选择 Enter。此时，窗体的标题栏中将显示文本**“图片查看器”**，并且**“属性”**窗口的外观应与下图类似。  
  
     ![“属性”窗口](../ide/media/express_edittextproperty.png "Express\_EditTextProperty")  
“属性”窗口  
  
    > [!NOTE]
    >  可以通过“按分类顺序”视图或“字母顺序”视图对属性进行排序。  可以通过使用**“属性”**窗口上的按钮在这两类视图之间进行切换。  在本教程中，通过“字母顺序”视图查找属性会更加轻松。  
  
4.  返回 Windows 窗体设计器。  选择窗体右下角的拖动手柄，此拖动手柄是位于窗体右下角的白色小正方形，如下所示。  
  
     ![拖动句柄](../ide/media/express_bottomrt_drag.png "Express\_BottomRT\_Drag")  
拖动手柄  
  
     拖动手柄以调整窗体的大小，使其更宽且更高一些。  
  
5.  查看**“属性”**窗口，您会发现**“Size”**属性已更改。  每当您调整窗体的大小时，**“Size”**属性都会更改。  尝试拖动窗体的手柄以将其大小调整为大约 550 x 350（无需精确），这个大小应适合于此项目。  或者，您可以直接在**“Size”**属性中输入值，然后选择 Enter 键。  
  
6.  重新运行程序。  记住，您可以使用以下任何一种方法来运行程序。  
  
    -   选择**“F5”**键。  
  
    -   在菜单栏上，依次选择**“调试”**、**“启动调试”**。  
  
    -   在工具栏上，选择**“启动调试”**按钮，如下所示。  
  
         ![“开始调试”工具栏按钮](../ide/media/express_icondebug.png "Express\_IconDebug")  
“启动调试”工具栏按钮  
  
     与之前的操作一样，IDE 会生成并运行程序，并且将显示一个窗口。  
  
7.  在转到下一个步骤之前，请停止程序，因为 IDE 不允许您在程序处于运行状态时更改程序。  记住，您可以使用以下任何一种方法来停止程序。  
  
    -   在工具栏上，选择**“停止调试”**按钮。  
  
    -   在菜单栏上，依次选择**“调试”**、**“停止调试”**。  
  
    -   选择**“Form1”**窗口上角的 X 按钮。  
  
### 继续或查看  
  
-   若要转到下一个教程步骤，请参见[步骤 4：使用 TableLayoutPanel 控件设置窗体布局](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)。  
  
-   若要返回上一个教程步骤，请参见[步骤 2：运行程序](../ide/step-2-run-your-program.md)。