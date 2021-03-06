---
title: SQLServerXAConnection 成员 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85d106ad25c1823f873ade24800e44987d78a2f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970253"
---
# <a name="sqlserverxaconnection-members"></a>SQLServerXAConnection 成员
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  下表列出由 [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) 类公开的成员。  
  
## <a name="constructors"></a>构造函数  
 无。  
  
## <a name="fields"></a>字段  
 无。  
  
## <a name="inherited-fields"></a>继承的字段  
 无。  
  
## <a name="methods"></a>方法  
  
|“属性”|描述|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|（继承自 [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)）注册给定的事件侦听器，以便在此 Connection 对象发生事件时通知该侦听器。|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|（继承自 [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)）关闭此 Connection 对象表示的物理连接。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|（继承自 [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)）为此 Connection 对象表示的物理连接创建对象句柄。|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|检索 [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) 对象，事务管理器将使用它来管理分布式事务中此 [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) 对象的参与。|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|（继承自 [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)）删除给定的事件侦听器。|  
  
## <a name="inherited-methods"></a>继承的方法  
  
|类继承自：|方法|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener、close、getConnection、removeConnectionEventListener|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|javax.sql.PooledConnection|addConnectionEventListener、close、getConnection、removeConnectionEventListener|  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerXAConnection 类](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
