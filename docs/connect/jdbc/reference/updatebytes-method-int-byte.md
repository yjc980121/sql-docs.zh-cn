---
title: updateBytes 方法 (int, byte) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBytes (int, byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 625f48ba-53d0-45a6-8fcb-643f1e0cbe8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 60de0b0fd051ed67a2f2804443e419d454c2cb5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996905"
---
# <a name="updatebytes-method-int-byte"></a>updateBytes 方法 (int, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根据给定的列索引使用字节值构成的数组更新指定的列  。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void updateBytes(int index,  
                        byte[] x)  
```  
  
#### <a name="parameters"></a>Parameters  
 索引   
  
 指示列索引的 int  。  
  
 *x*  
  
 **字节**值的数组。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 updateBytes 方法是由 java.sql.ResultSet 接口中的 updateBytes 方法指定的。  
  
 在之前的 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 版本中，可使用 SQLServerResultSet.updateBytes 将字节数组和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型日期、时间、datetime2 或 datetimeoffset 的值相互转换     。 现在对于这些数据类型使用此方法将导致异常，指出不支持该转换。  
  
## <a name="see-also"></a>另请参阅  
 [updateBytes 方法 (SQLServerResultSet)](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)   
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
