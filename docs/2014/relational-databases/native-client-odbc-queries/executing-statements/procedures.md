---
title: 过程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d030d4fb12ce9217bbdb88f501a0b0674c5a5828
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206747"
---
# <a name="procedures"></a>过程
  存储过程是包含一个或多个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句的预先编译的可执行对象。 存储过程可具有输入和输出参数，并且还可以生成整数返回代码。 应用程序可以通过使用目录函数枚举可用的存储过程。  
  
 以 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 为目标的 ODBC 应用程序只应使用直接执行以调用某一存储过程。 当连接到早期版本的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，则[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驱动程序实现[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)通过创建临时存储的过程，然后调用上**SQLExecute**. 它会增加开销能够**SQLPrepare**创建临时存储的过程，只有在调用目标存储过程，而非直接执行目标存储过程。 即使在连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的某一实例时，准备调用都要求额外的网络上的往返，并且生成只调用存储过程执行计划的执行计划。  
  
 在执行某一存储过程时，ODBC 应用程序应使用 ODBC CALL 语法。 驱动程序将优化，以便在使用 ODBC CALL 语法时，使用远程过程调用机制来调用该过程。 这比用于将 [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE 语句发送到服务器的机制效率更高。  
  
 有关详细信息，请参阅[运行存储过程](../../native-client-odbc-stored-procedures/running-stored-procedures.md)。  
  
## <a name="see-also"></a>请参阅  
 [执行语句&#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
