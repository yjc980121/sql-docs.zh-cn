---
title: 标量函数转义序列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36e108fcc61b2390d5fd72ac4ad322778ccfb4b2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057074"
---
# <a name="scalar-function-escape-sequence"></a>标量函数转义序列
ODBC 标量函数中使用转义序列。 此转义序列的语法如下所示：  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>备注  
 BNF 表示法中的语法是按如下所示：  
  
 *ODBC 标量函数转义*:: =  
  
 *ODBC esc 启动器*fn*标量函数 ODBC esc 终止符*  
  
 *scalar-function* ::= *function-name* (*argument-list*)  
  
 (非终止符的定义*函数名*并*函数名称*(*自变量列表*) 从列表中的标量函数派生[附录 e:标量函数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)。)  
  
 *ODBC esc 启动器*:: = {  
  
 *ODBC esc 终止符*:: =}  
  
 若要确定是否在数据源支持过程，驱动程序支持 ODBC 过程调用语法，应用程序可以调用**SQLGetInfo**。 有关详细信息，请参阅[附录 e:标量函数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)。
