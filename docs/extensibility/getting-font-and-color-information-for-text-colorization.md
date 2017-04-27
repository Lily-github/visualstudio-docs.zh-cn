---
title: "获取字体和文本着色的颜色信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 57b3d53f86d132779fb00608886fa7c479b71551
ms.lasthandoff: 04/05/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>获取字体和文本着色的颜色信息
呈现或以的文本显示在用户界面 (UI) 元素中的过程取决于项目、 其技术和开发人员首选项的类型。 **字体和颜色**属性页存储设置。  
  
 显示以的文本的大多数实施方案需要`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`和关联接口的提供、 检索和存储文本显示设置。  
  
> [!NOTE]
>  自定义核心编辑器时 (支持**文本 EditorCategory**)，强烈建议在语言服务中使用着色技术。 有关详细信息，请参阅[字体和颜色概述](../extensibility/font-and-color-overview.md)。  
  
## <a name="getting-default-font-and-color-information"></a>获取默认字体和颜色信息  
 所有**字体和颜色**应中指定的任何窗口中显示文本的设置**显示项**之一**类别**。 有关详细信息，请参阅[字体和颜色，环境中，选项对话框](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
 若要为着色，VSPackage 必须获取当前**字体和颜色**设置。 VSPackage 可以完成此操作通过以下方式根据其需求︰  
  
-   使用的字体和颜色持久性机制检索存储或当前状态。 有关详细信息，请参阅[访问存储的字体和颜色设置](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
-   使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>提供字体和颜色的数据，要获取其实例的服务接口<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>，如果 VSPackage 也不是字体和颜色的提供程序。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 若要确保通过轮询获取的结果保持最新，它可能会有用使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>接口来确定在调用的检索方法之前是否需要更新<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 之后你已获得字体和颜色信息、 分析文本以显示来标识元素需要着色，然后在使用适当的字体和颜色窗口中显示文本。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [使用字体和文本](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [处理颜色](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI （图形设备接口）](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)