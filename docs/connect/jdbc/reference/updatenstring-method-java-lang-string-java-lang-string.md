---
title: updateNString 方法 (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6daca03f-c60f-4842-b9e3-11d136e78312
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0fdc853608cf1897e97e08aac673aff78df00aef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998551"
---
# <a name="updatenstring-method-javalangstring-javalangstring"></a>updateNString 方法 (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  通过指定的列标签使用字符串值更新指定列  。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void updateNString(java.lang.String columnLabel,  
                          java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Parameters  
 columnLabel   
  
 一个包含列标签的字符串  。  
  
 nString   
  
 **String**对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 updateNString 方法是由 java.sql.ResultSet 接口中的 updateNString 方法指定的。  
  
 此方法将 Java**字符串**传递到选定的**nchar**、 **nvarchar (max)** 、 **ntext**和**xml**列。 在其他数据类型列上使用此方法会引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [updateNString 方法 (SQLServerResultSet)](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
