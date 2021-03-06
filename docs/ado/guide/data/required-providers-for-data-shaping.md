---
title: 数据整理所需的提供程序 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 732563fc2c4e1cc93beac8712d845b960ae56aaf
ms.sourcegitcommit: 97e94b76f9f48d161798afcf89a8c2ac0f09c584
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661270"
---
# <a name="required-providers-for-data-shaping"></a>数据整理所需的提供程序
数据定形通常需要两个提供程序。 OLE DB 的服务提供商、[数据定形服务](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)提供数据定形功能, 数据访问接口 (例如 SQL Server 的 OLE DB 提供程序) 提供数据行来填充形状的[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
 可以将服务提供程序 (MSDataShape) 的名称指定为[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象[提供程序](../../../ado/reference/ado-api/provider-property-ado.md)属性的值或连接字符串关键字 "provider = MSDataShape;"。  
  
 可以将数据提供程序的名称指定为**数据提供程序**动态属性的值, 该[属性](../../../ado/reference/ado-api/properties-collection-ado.md)将添加到 OLE DB 的  数据定形服务或连接字符串关键字 "**数据访问接口 =** _提供程序_"。  
  
 如果未填充**记录集**, 则不需要任何数据提供程序 (例如, 在使用 NEW 关键字创建列的虚构**记录集中**)。 在这种情况下, 请指定 "**Data Provider =** none;"。  
  
## <a name="example"></a>示例  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>请参阅  
 [数据定形示例](../../../ado/guide/data/data-shaping-example.md)   
 [正式形状语法](../../../ado/guide/data/formal-shape-grammar.md)   
 [常用 Shape 命令](../../../ado/guide/data/shape-commands-in-general.md)
