---
title: 值（XAttribute 动态属性）
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c31179d33467f6be440882bce6f6cd9559d9a00
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080819"
---
# <a name="value-xattribute-dynamic-property"></a>值（XAttribute 动态属性）

获取或设置 XML 属性的值。

## <a name="syntax"></a>语法

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>属性值/返回值

包含此属性的值的 <xref:System.String>。

## <a name="exceptions"></a>异常

|异常类型|条件|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|设置时，`value` 为 `null`。|

## <a name="remarks"></a>备注

此属性等效于 <xref:System.Xml.Linq.XAttribute.Value%2A> 类的 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> 属性，但此动态属性还支持更改通知。

## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [XAttribute 类动态属性](../designers/xattribute-class-dynamic-properties.md)
- [特性](../designers/attribute-xelement-dynamic-property.md)