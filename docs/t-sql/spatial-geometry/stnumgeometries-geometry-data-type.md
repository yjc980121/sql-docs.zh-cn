---
title: STNumGeometries（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5a0c123b367fa2a85a1a3732200452a474b032c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088926"
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回构成 **geometry** 实例的几何图形的数目。
  
## <a name="syntax"></a>语法  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：int  
  
 CLR 返回类型：**SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 如果 geometry 实例不是 MultiPoint、MultiLineString、MultiPolygon 或 GeometryCollection 实例，则此方法返回 1；如果 geometry 实例为空，则返回 0。  
  
> [!NOTE]  
>  如果 GeometryCollection 嵌套了空元素，则 `STNumGeometries()` 不会返回 0。 虽然 GeometryCollection 实例中的元素为空，但该实例本身不是空集。  
  
  

