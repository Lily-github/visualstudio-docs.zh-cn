---
title: "IDiaSymbol::get_nested | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_nested 方法"
ms.assetid: 6ae46d43-8486-48d6-a6f2-d73ebf4023e3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_nested
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指定的标志用户定义的数据类型是否嵌套。  
  
## 语法  
  
```cpp#  
HRESULT get_nested (   
   BOOL* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] ，如果用户定义的数据类型嵌套，返回 `TRUE` ;否则，返回 `FALSE`。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)