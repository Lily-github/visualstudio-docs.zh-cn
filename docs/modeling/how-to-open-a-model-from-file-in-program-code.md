---
title: "如果：在程序代码中从文件打开模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7d68697-5418-4263-bdb2-48401924ea71
caps.latest.revision: 8
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 8
---
# 如果：在程序代码中从文件打开模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以在任何应用程序的 DSL 模型。  
  
 从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展，可以为此使用 ModelBus。  ，则移动了， ModelBus 提供标准机制为引用一个模型或组件在设计以及查找该模型。  有关更多信息，请参见 [通过使用 Visual Studio Modelbus 集成模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。  
  
## 目标 Framework  
 设置应用程序项目的 **目标框架** 到 **.NET framework 4**。  
  
#### 设置目标框架  
  
1.  打开要读取 DSL 模型的应用程序中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目。  
  
2.  在**“解决方案资源管理器”**中右击该项目，再单击**“属性”**。  
  
3.  在项目属性窗口，请在 **应用程序** 选项卡上，将 **目标框架** 字段设置为 **.NET framework 4**。  
  
> [!NOTE]
>  您可能需要执行此操作，即使您选择了项目创建对话框的 **.NET framework 4** 。  目标结构不应是 **.NET framework 4 client profile**。  
  
## 引用  
 必须将这些引用。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 应用程序项目:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.11.0`  
  
    -   如果看不到此在 **添加引用** 对话框的 **.NET** 选项卡下，单击 **浏览** 选项并定位到 `%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Common\Assemblies \`。  
  
-   DSL 程序集，则会在 bin 文件夹下 DSL 项目。  其名称功能的形式为: *公司*。*TheProject*`. Dsl.dll`。  
  
## 在 DSL 的关键类  
 在可以编写读取 DSL 的代码之前，应知道特定的名称 DSL 生成类。  在 DSL 解决方案中，打开 **DSL** 项目并在 **GeneratedCode** 文件夹。  或者，请双击项目 **引用**的 DSL 程序集，并在 **对象浏览器**的 DSL 命名空间。  
  
 这些是您应确定的类:  
  
-   *TheDslRootClass* \- 这是根类的名称。 `DslDefinition.dsl`的。  
  
-   *TheDslName* `SerializationHelper` \- 此类在 DSL 项目的 `SerializationHelper.cs` 定义。  
  
-   *TheDslName* `DomainModel` \- 此类在 DSL 项目的 `DomainModel.cs` 定义。  
  
## 读取文件  
 下面的示例旨在读取关键类的 DSL 如下所示:  
  
-   FamilyTreeModel  
  
-   FamilyTreeSerializationHelper  
  
-   FamilyTreeDomainModel  
  
 在 DSL 的另一个域类是人员。  
  
```  
using System;  
using Microsoft.VisualStudio.Modeling;  
using Company.FamilyTree; // Your DSL namespace  
  
namespace StandaloneReadDslConsole  
{ class Program  
  { static void Main(string[] args)  
    {  
      // The path of a DSL model file:  
      string dslModel = @"C:\FamilyTrees\Tudor.ftree";  
      // Set up the Store to read your type of model:  
      Store store = new Store(  
        typeof(Company.FamilyTree.FamilyTreeDomainModel));  
      // The Model type generated by the DSL:  
      FamilyTreeModel familyTree;  
      // All Store changes must be in a Transaction:  
      using (Transaction t =   
        store.TransactionManager.BeginTransaction("Load model"))  
      {  
        familyTree =   
           FamilyTreeSerializationHelper.Instance.  
              LoadModel(store, dslModel, null, null, null);  
        t.Commit(); // Don't forget this!  
      }  
      // Now we can read the model:  
      foreach (Person p in familyTree.People)  
      {  
        Console.WriteLine(p.Name);   
        foreach (Person child in p.Children)  
        {  
          Console.WriteLine("    " + child.Name);  
        }  
} } } }  
```  
  
## 对文件的保存  
 前面代码的下面添加更改该模型然后将其保存到文件。  
  
```  
using (Transaction t =  
  store.TransactionManager.BeginTransaction("update model"))  
{  
  // Create a new model element:  
  Person p = new Person(store);  
  // Set its embedding relationship:  
  p.FamilyTreeModel = familyTree;  
  // - same as: familyTree.People.Add(p);  
  // Set its properties:  
  p.Name = "Edward VI";  
  t.Commit(); // Don't forget this!  
}  
// Save the model:  
try  
{  
  SerializationResult result = new SerializationResult();  
  FamilyTreeSerializationHelper.Instance  
    .SaveModel(result, familyTree, @"C:\FamilyTrees\Tudor-upd.ftree");  
  // Report any error:  
  if (result.Failed)  
  {  
    foreach (SerializationMessage message in result)  
    {  
      Console.WriteLine(message);  
    }  
  }  
}  
catch (System.IO.IOException ex)  
{ ... }  
```