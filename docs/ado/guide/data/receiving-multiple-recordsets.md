---
title: 接收多个记录集 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6d6e649201b8bf23a1b696d574baea2f4b049e06
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924533"
---
# <a name="receiving-multiple-recordsets"></a>接收多个记录集
[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)支持返回多个**记录集**对象的单个命令包含多个 SQL 语句，一个**记录集**每个 SQL 语句。 依据的顺序**记录集**将返回将遵循在其中的 SQL 语句放置在命令文本中的顺序。  
  
 Microsoft OLE DB Provider for SQL Server 也会返回多个结果集对 ADO 时该命令包含 COMPUTE 子句。 例如，包含以下 SQL 语句的命令将返回结果，在两个**记录集**对象： 一个用于的行集 (*ProductID*， *ProductName*，*UnitPrice*)，另一个用于在表中的所有产品的平均价格。  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 可以使用**Recordset.NextRecordset**方法要枚举的两个对象。  
  
 有关详细信息，请参阅[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)。
