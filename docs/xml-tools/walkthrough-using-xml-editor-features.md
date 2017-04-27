---
title: "演练：使用 XML 编辑器功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 演练：使用 XML 编辑器功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

该演练中的步骤说明如何创建新 XML 文档。该演练还使用“XML 编辑器”的一些功能，这些功能使其非常适合 XML 编写。  
  
> [!NOTE]
>  在开始该演练之前，将 hireDate.xsd 文件（本主题的下文介绍）保存到本地计算机上。  
  
### 新建 XML 文件并将其与 XML 架构关联  
  
1.  在“文件”菜单上指向“新建”，再单击“文件”。  
  
2.  在“模板”窗格中选择“XML 文件”，再单击“打开”。  
  
     新文件将在编辑器中打开。该文件包含默认的 XML 声明 `<?xml version="1.0" encoding="utf-8">`。  
  
3.  在文档属性窗口的“架构”字段上单击“浏览”按钮 \(**...**\)。  
  
     此时出现“XSD 架构”对话框。  
  
4.  单击“添加”。  
  
     此时显示“打开 XSD 架构”对话框。  
  
5.  选择 hireDate.xsd 文件并单击“打开”。  
  
6.  单击“确定”。  
  
     现在，XML 架构已与 XML 文档关联。XML 架构用于验证文档。智能感知还使用该架构来填充有效元素的成员列表。  
  
### 添加数据  
  
1.  在编辑器窗格中键入 `<`。  
  
     成员列表中显示可能的项：  
  
    -   **\!\-\-**，用于添加注释。  
  
    -   **\!DOCTYPE**，用于添加文档类型。  
  
    -   **?**，用于添加处理指令。  
  
    -   **employee**，用于添加根元素。  
  
2.  选择 **\<\!\-\-** 添加注释节点，再按 ENTER 键。  
  
     编辑器将插入注释结束标记，并将光标置于开始注释标记和结束注释标记之间。  
  
3.  键入“测试 XML 文件”。  
  
4.  在新行上，键入 `<`，然后从成员列表中选择 **employee**。  
  
     编辑器将添加 XML 元素的开始部分 `<employee`。此时，可以在元素中添加属性，也可以键入 `>` 结束开始标记。  
  
5.  键入 `>` 以结束该标记。  
  
6.  编辑器将添加结束标记。添加的结束标记使用波浪形下划线指示验证错误。工具提示将显示消息：元素“employee”的内容不完整。应包含“ID”。  
  
7.  键入 `<`，再从成员列表中选择 **ID**。然后键入 `>`。  
  
     编辑器将添加 XML 元素 `<ID></ID>` 并将光标置于 ID 开始标记的后面。  
  
8.  键入 abc。  
  
     abc 文本具有波浪形下划线。工具提示将显示消息：根据数据类型，“ID”元素的值无效。  
  
9. 右击 ID 元素，再选择“转到定义”。  
  
     编辑器将在新的文档窗口中打开 hireDate.xsd 文件，并将光标置于 ID 架构元素定义上。  
  
10. 返回 XML 文件，然后将 abc 文本替换为 123。  
  
     波浪形下划线和工具提示在 ID 元素值下清除。现在，employee 结束标记的工具提示显示消息：元素“employee”的内容不完整。应包含“hire\-date”。  
  
11. 将光标置于 ID 结束标记后面，键入 `<`，再从成员列表中选择 hire\-date，然后键入 `>`。  
  
     编辑器将添加 XML 元素 `<hire-date></hire-date>` 并将光标置于 hire\-date 开始标记的后面。  
  
12. 键入 2003\-01\-10 作为 hire\-date 的值。  
  
### 格式化 XML 文档  
  
1.  在“XML 编辑器”的工具栏上选择“格式化文档”按钮。  
  
     XML 文档将重新格式化。  
  
### 保存 XML 文档  
  
1.  在“文件”菜单中选择“另存为”。  
  
     此时出现“文件另存为”对话框。默认的文件名为“XMLFile1”。  
  
2.  输入 XML 文档的文件名和位置，再单击“保存”。  
  
## hireDate.xsd 文件  
 以下架构文件供该演练使用。  
  
```  
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## 请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)