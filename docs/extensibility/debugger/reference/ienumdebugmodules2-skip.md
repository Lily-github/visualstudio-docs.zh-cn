---
title: "IEnumDebugModules2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2::Skip"
helpviewer_keywords: 
  - "IEnumDebugModules2::Skip"
ms.assetid: 61dc42f4-8544-45bb-8da0-fb22cccec7da
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugModules2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在元素中指定数目的跳过。  
  
## 语法  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 跳过的元素数。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  返回 `S_FALSE` ，如果 `celt` 比其余元素的数量大于;否则，返回错误代码。  
  
## 备注  
 如果 `celt` 比剩余的元素数指定值，枚举设置为末尾，并 `S_FALSE` 返回。  
  
## 请参阅  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)