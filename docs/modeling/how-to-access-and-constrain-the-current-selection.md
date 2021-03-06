---
title: 如何：访问和约束当前所选内容
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5d8fb0a2e5d218b76e972fc97a53afcd2f8ef3e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31952357"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>如何：访问和约束当前所选内容

当您为域特定语言编写的命令或笔势处理程序时，你可以确定用户右击哪些元素。 你还可以选择阻止某些形状或字段。 例如，你可以排列当用户单击图标修饰器，而是选择包含它的形状。 约束以这种方式选择可减少你必须编写的处理程序的数量。 它还可方便的用户，可以单击任意位置在形状中而无需避免修饰器。

## <a name="access-the-current-selection-from-a-command-handler"></a>从命令处理程序中访问当前选定内容

为域特定语言的命令集类包含自定义命令的命令处理程序。 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>类，派生的域特定语言的命令集类提供用于访问当前所选内容的几个成员。

根据该命令的命令处理程序可能需要在模型设计器、 模型资源管理器或活动的窗口中选择。

### <a name="to-access-selection-information"></a>若要访问所选内容信息

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>类定义可用来访问当前所选内容的以下成员。

    |成员|描述|
    |------------|-----------------|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 方法|返回`true`如果任何在模型设计器中选择的元素是隔离舱形状; 否则为`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 方法|返回`true`关系图是模型设计器中选定; 否则为如果`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 方法|返回`true`恰好一个元素是模型设计器中选定; 否则为如果`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 方法|返回`true`恰好一个元素是选定的活动窗口中; 否则为如果`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 属性|获取在模型设计器中选择的元素的只读集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 属性|获取活动窗口中的选定元素的只读集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 属性|在模型设计器中获取所选内容的主要元素。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 属性|获取活动窗口中的所选内容的主要元素。|

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>属性<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>类提供对访问<xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>表示模型设计器窗口，并提供模型设计器中的所选的元素的其他访问的对象。

3.  此外，生成的代码定义一个资源管理器工具窗口属性，该命令中的资源管理器中选择属性设置为域特定语言的类。

    -   资源管理器工具窗口属性返回的域特定语言的资源管理器工具窗口类的一个实例。 资源管理器工具窗口类派生自<xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>类和表示的域特定语言的模型资源管理器。

    -   `ExplorerSelection`属性返回所选的元素中的域特定语言模型资源管理器窗口。

## <a name="determine-which-window-is-active"></a>确定哪个窗口处于活动状态

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>接口包含定义提供对在外壳程序中的当前选择状态的访问的成员。 你可以获取<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>从包类或通过的域特定语言的命令集类的对象`MonitorSelection`每个基类中定义的属性。 包类派生自<xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>类，并且命令集类派生自<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>类。

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>若要从命令处理程序确定哪种类型的窗口处于活动状态

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>属性<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>类返回<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>提供对在外壳程序中的当前选择状态的访问的对象。

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>属性<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>接口获取活动选择容器，它可以是不同于活动的窗口。

3.  添加到该命令的以下属性类将为您设置以确定哪种类型的窗口是活动的域特定语言。

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>约束所选内容

通过添加所选内容的规则，你可以控制时用户在模型中选择元素选择了哪些元素。 例如，若要允许用户的数量的元素视为单个单元，可以使用选择规则。

### <a name="to-create-a-selection-rule"></a>若要创建一个选择规则

1.  DSL 的项目中创建自定义代码文件

2.  定义选择规则类派生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>类。

3.  重写<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A>选择规则类要应用的选择条件的方法。

4.  将 ClassDiagram 类的分部类定义添加到你的自定义代码文件。

     `ClassDiagram`类派生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>类并在生成的代码文件中，Diagram.cs，DSL 项目中定义。

5.  重写<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>属性`ClassDiagram`类以返回自定义选择规则。

     默认实现<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>属性获取一个不会修改选择的 selection 规则对象。

### <a name="example"></a>示例

下面的代码文件创建一个用于扩展所选内容，以包括所有实例的每个初始时会选中的域形状的选择规则。

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>