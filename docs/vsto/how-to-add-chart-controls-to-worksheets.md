---
title: 如何： 向工作表添加图表控件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05fc2cafda3ed4aa0ff7756062c1cec0429ebc96
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548731"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>如何： 向工作表添加图表控件
  你可以添加<xref:Microsoft.Office.Tools.Excel.Chart>到 Microsoft Office Excel 工作表在设计时和运行时在文档级自定义项上的控件。 你还可以添加<xref:Microsoft.Office.Tools.Excel.Chart>运行时在 VSTO 外接程序上的控件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 本主题介绍了以下任务：  
  
-   [在设计时添加图表控件](#designtime)  
  
-   [在文档级项目中的运行时添加图表控件](#runtimedoclevel)  
  
-   [在运行时在 VSTO 外接程序项目中添加图表控件](#runtimeaddin)  
  
 有关详细信息<xref:Microsoft.Office.Tools.Excel.Chart>控件，请参阅[图表控件](../vsto/chart-control.md)。  
  
##  <a name="designtime"></a> 在设计时添加图表控件  
 可按照与从应用程序添加图表相同的方式，将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到工作表中。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart>控件不能从**工具箱**或**数据源**窗口。  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>将图表主机控件添加到 Excel 的工作表中  
  
1.  上**插入**选项卡上，在**图表**组中，单击**列**，单击一个图表，类别，然后单击所需的图表类型。  
  
2.  在**插入图表**对话框中，单击**确定**。  
  
3.  上**设计**选项卡上，在**数据**组中，单击**选择数据**。  
  
4.  在**选择数据源**对话框中，单击**图表****数据范围**框，并清除所有默认选择。  
  
5.  在**图表数据**表中，选择包含图表的数据的单元格范围 (单元格**A5**通过**D8**)。  
  
6.  在**选择数据源**对话框中，单击**确定**。  
  
##  <a name="runtimedoclevel"></a> 在文档级项目中的运行时添加图表控件  
 你可以添加<xref:Microsoft.Office.Tools.Excel.Chart>在运行时动态控件。 文档关闭时，动态创建的图表不会作为主机控件保留在文档中。 有关详细信息，请参阅[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>以编程方式将图表控件添加到工作表中  
  
1.  在 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件处理程序中，插入下列代码以添加 <xref:Microsoft.Office.Tools.Excel.Chart> 控件。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> 在运行时在 VSTO 外接程序项目中添加图表控件  
 可以按编程方式将 <xref:Microsoft.Office.Tools.Excel.Chart> 控件添加到 VSTO 外接程序项目中任何打开的工作表中。 有关详细信息，请参阅[扩展 Word 文档和 Excel VSTO 外接程序在运行时中的工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
 工作表关闭时，动态创建的图表控件不会作为主机控件保留在工作表中。 有关详细信息，请参阅[在运行时将控件添加到 Office 文档](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>以编程方式将图表控件添加到工作表中  
  
1.  下面的代码将生成基于打开工作表的工作表主机项，然后添加 <xref:Microsoft.Office.Tools.Excel.Chart> 控件。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>编译代码  
 此示例具有下列要求：  
  
-   制成图表并存储在工作表中 A5 到 D8 范围内的数据。  
  
## <a name="see-also"></a>请参阅  
 [扩展 Word 文档和 Excel VSTO 外接程序在运行时中的工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文档上的控件](../vsto/controls-on-office-documents.md)   
 [图表控件](../vsto/chart-control.md)   
 [通过使用扩展的对象自动化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [主机项和主机控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  