---
title: setPoolable 方法 (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5424de7d0d6f7bda44ec61ea61f48d63bb097c97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973205"
---
# <a name="setpoolable-method-sqlserverstatement"></a>setPoolable 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  请求语句入池或不入池。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Parameters  
 poolable   
  
 如果为 true  ，则请求语句入池。 如果为 false  ，则请求语句不入池。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 poolable  参数中指定的值是对语句池实现的提示，用于指示应用程序是否希望语句入池。 语句池管理器决定应用程序是否使用该提示。  
  
 语句的池值既应用于由驱动程序实现的内部语句缓存，也应用于由应用程序服务器和其他应用程序实现的外部语句缓存。  
  
 默认情况下, SQLServerStatement 对象在创建时不可入池。 SQLServerPreparedStatement 和 SQLServerCallableStatement 对象在创建时是可入池。  
  
 如果对已关闭的语句调用此方法，将引发 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)。  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) 返回指示对象是否可入池的值。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerStatement 成员](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 类](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
