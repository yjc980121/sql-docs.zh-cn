---
title: 语句的批处理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8951469279e5c3577aef355e339397b329bb5d63
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206772"
---
# <a name="batches-of-statements"></a>语句的批处理
  一批[!INCLUDE[tsql](../../../includes/tsql-md.md)]语句包含两个或多个语句，用分号 （;），内置于单个字符串中传递给隔开**SQLExecDirect**或[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)。 例如：  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 批处理通常可减少网络流量，因而比单个提交语句效率更高。 使用[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)定位在下一个结果集时已完成，但当前结果集。  
  
 当 ODBC 游标属性设置为行集大小为 1 的只进只读游标的默认值时，始终可以使用批处理。  
  
 如果在针对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用服务器游标时执行批处理，则服务器游标会隐式转换为默认结果集。 **SQLExecDirect**或**SQLExecute**返回 SQL_SUCCESS_WITH_INFO，并且调用**SQLGetDiagRec**返回：  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>请参阅  
 [执行语句&#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
