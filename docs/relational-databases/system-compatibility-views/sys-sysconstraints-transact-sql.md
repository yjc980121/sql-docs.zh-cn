---
title: sys.sysconstraints (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
author: rothja
ms.author: jroth
ms.openlocfilehash: dfd88dec92d2707b72c829aa53f2798d3d64fee3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089187"
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  包含约束映射，映射到数据库中拥有该约束的对象。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|约束号。|  
|**id**|**int**|拥有该约束的表 ID。|  
|**列 id**|**smallint**|在其中定义约束的列 ID。<br /><br /> 0 = 表约束|  
|**spare1**|**tinyint**|保留|  
|**status**|**int**|Pseudo-bit-mask 指示状态。 可能的值包括：<br /><br /> 1 = PRIMARY KEY 约束<br /><br /> 2 = UNIQUE KEY 约束<br /><br /> 3 = FOREIGN KEY 约束<br /><br /> 4 = CHECK 约束<br /><br /> 5 = DEFAULT 约束<br /><br /> 16 = 列级约束<br /><br /> 32 = 表级约束|  
|**操作**|**int**|保留|  
|**error**|**int**|保留|  
  
## <a name="see-also"></a>请参阅  
 [系统表映射到系统视图&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
