---
title: getCharacterStream 方法 (long, long) (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 10cd57cff29c73a2b99d1489eb122eed37859768
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953271"
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>getCharacterStream 方法 (long, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索具有指定位置和长度且作为 Reader  对象或字符流的 NCLOB  数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>Parameters  
 pos   
  
 指示与要检索的部分值的第一个字符之间偏移量的 long 值  。  
  
 *length*  
  
 指示要检索的部分值的字符长度的 long  。  
  
## <a name="return-value"></a>返回值  
 包含 NCLOB  数据的 Reader 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getCharacterStream 方法由 getCharacterStream 方法在 NClob 接口中指定。  
  
## <a name="see-also"></a>另请参阅  
 [getCharacterStream 方法 &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [SQLServerNClob 方法](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 成员](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 类](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
