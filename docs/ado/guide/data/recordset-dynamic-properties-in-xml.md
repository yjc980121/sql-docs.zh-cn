---
title: 在 XML 中的记录集动态属性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a058a2d0c5a808f29807744c6ba01f658bebc120
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924446"
---
# <a name="recordset-dynamic-properties-in-xml"></a>XML 中的记录集动态属性
当前保存为 XML 格式 （从客户端游标引擎） 下的记录集提供程序特定属性：  
  
-   更新重新同步  
  
-   唯一表  
  
-   唯一的架构  
  
-   唯一目录  
  
-   重新同步命令  
  
-   IrowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   重新调整形状名称  
  
-   AutoRecalc  
  
 这些属性作为保留的记录集的元素定义的属性保存在架构部分。 这些属性的行集架构命名空间中定义，并且必须具有前缀"rs:"。  
  
## <a name="see-also"></a>请参阅  
 [以 XML 格式保留记录](../../../ado/guide/data/persisting-records-in-xml-format.md)
