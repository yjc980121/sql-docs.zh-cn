---
title: sys.sysfilegroups (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysfilegroups_TSQL
- sys.sysfilegroups
- sysfilegroups
- sys.sysfilegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysfilegroups system table
- sys.sysfilegroups compatibility view
ms.assetid: e567fa07-31cd-43cc-b8c7-ba6108baca80
author: rothja
ms.author: jroth
ms.openlocfilehash: 5388533ed665548eaaac3c25976271750d1348c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053483"
---
# <a name="syssysfilegroups-transact-sql"></a>sys.sysfilegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  数据库中的每个文件组都在表中占一行。 在该表中至少有一项用于主文件组。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**groupid**|**smallint**|每个数据库的唯一组标识号。|  
|**allocpolicy**|**smallint**|保留|  
|**status**|**int**|0x8 = 只读<br /><br /> 0x10 = 默认|  
|**groupname**|**sysname**|文件组的名称。|  
  
## <a name="see-also"></a>请参阅  
 [系统表映射到系统视图&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
