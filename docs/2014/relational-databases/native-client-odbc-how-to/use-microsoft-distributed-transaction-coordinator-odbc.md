---
title: 使用 Microsoft 分布式事务处理协调器（ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 425f9fc0b7637aab1869130a2830c2f3c134fe7d
ms.sourcegitcommit: 82a1ad732fb31d5fa4368c6270185c3f99827c97
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688703"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>使用 Microsoft 分布式事务处理协调器 (ODBC)
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>使用 MS DTC 更新两个或更多 SQL 服务器  
  
1.  使用 MS DTC OLE DtcGetTransactionManager 函数连接到 MS DTC。 有关 MS DTC 的信息，请参阅 Microsoft 分布式事务处理协调器。  
  
2.  对要建立的每个 Microsoft SQL Server 连接调用 SQL DriverConnect 一次。  
  
3.  调用 MS DTC OLE ITransactionDispenser::BeginTransaction 函数以开始 MS DTC 事务，并获得代表事务的事务对象。  
  
4.  对于要在 MS DTC 事务中登记的每个 ODBC 连接调用一次或多次 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)。 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 第二个参数必须是 SQL_ATTR_ENLIST_IN_DTC，并且第三个参数必须是在步骤 3 中获得的 Transaction 对象。  
  
5.  对于要更新的每个 SQL Server 调用一次 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)。  
  
6.  调用 MS DTC OLE ITransaction::Commit 函数以提交 MS DTC 事务。 Transaction 对象不再有效。  
  
 若要执行一系列 MS DTC 事务，请重复步骤 3 到 6。  
  
 若要释放对 Transaction 对象的引用，请调用 MS DTC OLE ITransaction::Return 函数。  
  
 若要将 ODBC 连接用于 MS DTC 事务，然后将该连接用于本地 SQL Server 事务，请调用 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)（带有 SQL_DTC_DONE）。  
  
> [!NOTE]  
>  还可以对每个 SQL Server 轮流调用 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 和 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)，而不是按照前面步骤 4 和 5 中的建议调用它们。  
  
## <a name="see-also"></a>另请参阅  
 [执行事务&#40;ODBC&#41;](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
