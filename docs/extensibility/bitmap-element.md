---
title: Bitmap 元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27e37a9da06145df2e940705650b1ab085250c53
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150799"
---
# <a name="bitmap-element"></a>Bitmap 元素
定义位图。 从资源或从文件加载位图。  
  
## <a name="syntax"></a>语法  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必须的。 GUID ID 的命令标识符的 GUID。<br /><br /> 位图的 guid 属性不与任何 VSPackage 或其他命令组相关联。  它应是唯一的位图定义并不用于任何其他用途。|  
|resID|GUID ID 的命令标识符的 ID。 ResID 或 href 属性是必需的。<br /><br /> ResID 属性是一个整数资源 ID，用于确定是要在命令表合并期间加载的位图条。  加载的命令表时，将从相同模块的资源加载指定的资源 ID 的位图。|  
|usedList|所需 resID 属性是否存在。 位图条中选择可用的映像。|  
|href|位图的路径。 ResID 或 href 属性是必需的。<br /><br /> 包含路径中搜索所指示的图像文件，生成的二进制文件中嵌入的。  在命令表合并，映像将复制并没有查找其他资源或负载是必需的。  如果 usedList 属性不存在，则该带中的所有映像。 **注意：** 可能中包括的几种格式之一提供的映像 *.bmp*， *.png*，并且 *.gif*。  早期版本的编译器不支持部分透明 alpha 信息的 32 位位图图像。 这些版本的解决方法是使用 *.png*格式。|  
|条件|可选。 请参阅[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|位图元素进行分组。|  
  
## <a name="example"></a>示例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio 命令表格 (.vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)