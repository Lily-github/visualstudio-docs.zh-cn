---
title: 工作流设计器-Rethrow 活动设计器
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24c13b629047b73b3f3ee15f2fc25a0120a2c177
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755250"
---
# <a name="rethrow-activity-designer"></a>Rethrow 活动设计器

**重新引发**活动设计器用于创建和配置<xref:System.Activities.Statements.Rethrow>活动。

## <a name="the-rethrow-activity"></a>Rethrow 活动

<xref:System.Activities.Statements.Rethrow> 活动引发先前已引发的异常。 此活动只能在 <xref:System.Activities.Statements.Catch> 活动的 <xref:System.Activities.Statements.TryCatch> 处理程序中使用。

### <a name="use-the-rethrow-activity-designer"></a>使用 ReThrow 活动设计器

访问**重新引发**中的活动设计器**错误处理**类别**工具箱**。 **重新引发**活动设计器可以从拖动**工具箱**只要通常放置活动的例如内放置到工作流设计器图面和<xref:System.Activities.Statements.Sequence>。 放置在活动设计器创建<xref:System.Activities.Statements.Rethrow>默认值的活动**DisplayName**的 Throw。 <xref:System.Activities.Activity.DisplayName%2A>值可以在的标头中编辑**重新引发**活动设计器中，或在**DisplayName**属性网格的框。

### <a name="the-rethrow-properties"></a>Rethrow 属性

下表显示<xref:System.Activities.Statements.Rethrow>属性，并说明它们如何使用在设计器中：

|属性名|必需|用法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Rethrow> 活动的可选友好名称。 默认值为 Rethrow。|

## <a name="see-also"></a>请参阅

- [集合](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)