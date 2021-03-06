---
title: 添加多个字段 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 07a1a3723b4169872c1b8aa872457e67a60d1f71
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926276"
---
# <a name="adding-multiple-fields-and-values"></a>添加多个字段和值
有时，可能会更有效的字段和其对应的值数组中传递**AddNew**方法，而不是设置**值**多次针对每个新字段。 如果*FieldList*是一个数组*值*必须也是一个数组具有相同成员的数目; 否则为就会出错。 字段名称的顺序必须与匹配的每个数组中的字段值的顺序。 下面的代码将数组的字段和值对的数组传递**AddNew**方法。

```
'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant

    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")

    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If

    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2
```
