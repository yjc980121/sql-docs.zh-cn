---
title: FieldEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5fe89d90510e95468e18b0d744ff566f69654320
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932684"
---
# <a name="fieldenum"></a>FieldEnum
指定特殊的字段中引用[记录](../../../ado/reference/ado-api/record-object-ado.md)对象的[字段](../../../ado/reference/ado-api/fields-collection-ado.md)集合。  
  
## <a name="remarks"></a>备注  
 这些常量提供访问与相关联的特殊字段的"快捷方式"**记录**。 检索[字段](../../../ado/reference/ado-api/field-object.md)对象从**字段**集合，然后获取其内容与**字段**对象的[值](../../../ado/reference/ado-api/value-property-ado.md)属性。  
  
|常量|ReplTest1|描述|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|引用包含的默认字段[Stream](../../../ado/reference/ado-api/stream-object-ado.md)与关联的对象**记录**。|  
|**adRecordURL**|-2|引用包含当前的绝对 URL 字符串的字段**记录**。|
