---
title: getBoolean 方法 (java.lang.String) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBoolean (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ba98a27b-722d-4904-ac65-0f082fde1fe6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a9bdf91105e9e7db82f51b5ba9885506e2edd8cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953531"
---
# <a name="getboolean-method-javalangstring-sqlserverresultset"></a>getBoolean 方法 (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索此 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象的当前行中指定列名称作为 Java 编程语言中的 boolean  的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public boolean getBoolean(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parameters  
 *columnName*  
  
 一个包含列名的字符串  。  
  
## <a name="return-value"></a>返回值  
 一个布尔值  。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getBoolean 方法是由 java.sql.ResultSet 接口中的 getBoolean 方法指定的。  
  
 仅对于数字和字符数据类型支持此方法。 它将值 "1"、1和 "**true**" 转换为**true**, 并将值 "0"、0和 "**false**" 转换为**false**。 对于所有其他值，未定义此行为。  
  
## <a name="see-also"></a>另请参阅  
 [getBoolean 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)   
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
