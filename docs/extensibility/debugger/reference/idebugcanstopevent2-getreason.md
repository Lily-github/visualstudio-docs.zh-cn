---
title: IDebugCanStopEvent2::GetReason |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0eaefee714467084898182b338ceda63ebdc0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101984"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
获取调试引擎 (DE) 想要停止的原因的原因。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pcr`  
 [out]返回一个值从[CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)描述此事件的原因的枚举。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法通常称为之前[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)方法，以便调用方可以确定是否将传递不为零 (`TRUE`) 到`IDebugCanStopEvent2::CanStop`方法。  
  
 停止的原因可能是`CANSTOP_ENTRYPOINT`，这意味着 DE 已达到入口点，或`CANSTOP_STEPIN`，这意味着 DE 到的函数具有单步执行。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)