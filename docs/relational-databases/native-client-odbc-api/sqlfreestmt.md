---
title: SQLFreeStmt | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b985db3cb58a7029a3b5ec489d2e23b0c1292919
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786728"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  通用   
      不建议在 ODBC 3.0 和更高版本中使用**SQLFreeStmt** 。 但是，如果应用程序需要重用该语句，则仍应将**SQLFreeStmt**与**SQL_RESET_PARAMS**和**SQL_UNBIND**选项一起使用）。 你还可以使用[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)、 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)、 [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)和[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)来替换或复制**SQLFreeStmt**的功能，并应改为使用它们。  
  
 通常，重复使用语句比丢弃它们并分配新语句更有效。 但在某些情况下，如重用语句，仍然必须使用 SQLFreeStmt。  
  
## <a name="see-also"></a>另请参阅  
 [SQLFreeStmt 函数](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API 实现细节](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
