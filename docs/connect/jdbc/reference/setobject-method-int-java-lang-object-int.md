---
title: setObject 方法 (int, java.lang.Object, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject (int, java.lang.Object, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78bfb6cc-8ca4-4879-9e2b-04164e746314
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3912570ab30f5d73578ecee285febfe933dd2f33
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973469"
---
# <a name="setobject-method-int-javalangobject-int"></a>setObject 方法 (int, java.lang.Object, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用给定的对象和目标类型设置指定参数的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setObject(int n,  
                            java.lang.Object obj,  
                            int targetSqlType)  
```  
  
#### <a name="parameters"></a>Parameters  
 *n*  
  
 指示参数编号的 int  。  
  
 obj   
  
 一个对象。  
  
 targetSqlType   
  
 一个 int 值，此值指示 java.sql.Types 中定义的目标类型  。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 setObject 方法是由 java.sql.PreparedStatement 接口中的 setObject 方法指定的。  
  
 从 JDBC Driver 3.0 开始, 此方法的行为通过 **sendTimeAsDatetime** 连接属性 ([设置连接属性](../../../connect/jdbc/setting-the-connection-properties.md)) 进行修改, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [SQLServerDataSource. Sqlserverdatasource.setsendtimeasdatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)。  
  
 有关详细信息, 请参阅[配置如何将 .Java 值发送到服务器](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)。  
  
## <a name="see-also"></a>另请参阅  
 [setObject 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement 类](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
