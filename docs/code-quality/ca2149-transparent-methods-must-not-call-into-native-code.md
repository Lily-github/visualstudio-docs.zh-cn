---
title: CA2149：透明方法不得调入本机代码
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0e21ae36795d866be76c6caaf9d01388621348d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919365"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149：透明方法不得调入本机代码
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 一个方法调用本机函数通过如 P/Invoke 方法存根。

## <a name="rule-description"></a>规则说明
 对于直接调用到本机代码中（例如通过使用 P/Invoke）的任何透明方法，将引发此规则。 违反此规则会导致<xref:System.MethodAccessException>级别 2 透明度模型中的完全要求<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>级别 1 透明度模型中。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，将标记的方法调用与本机代码的<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>属性。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]