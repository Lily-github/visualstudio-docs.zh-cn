---
title: IDebugBinder::GetFunctionObject |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 302c6c983b07e2e2a7a393fac86999df4cb2b492
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099254"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
此方法获取[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用于创建函数参数的对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppFunction`  
 [out]返回[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用于创建函数参数的接口。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)