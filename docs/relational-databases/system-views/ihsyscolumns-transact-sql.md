---
title: IHsyscolumns (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: a432685809676f997049940ea5aa1ce43dc38a60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029636"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHsyscolumns**视图显示从非 SQL Server 发布服务器的项目的列信息。 此视图存储在分发数据库中。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|列名或过程参数的名称。|  
|**id**|**int**|此列所属的表的对象 ID，或与此参数关联的存储过程的 ID。|  
|**xtype**|**tinyint**|将物理存储类型从[sys.systypes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)。|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|扩展的用户定义数据类型的 ID。|  
|**length**|**bigint**|从最大物理存储长度[sys.systypes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)。|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**列 id**|**int**|列或参数 id。|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**保留**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|此列的默认值的 ID。|  
|**域**|**int**|此列的规则的 ID 或 CHECK 约束的 ID。|  
|**number**|**int**|过程分组时的子过程号 (**0**表示非过程项)。|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|此列将显示的行中的偏移量。|  
|**collationid**|**int**|列的排序规则的 ID。 对于基于非字符的列为 NULL。|  
|**language**|**int**|列的语言标识符。|  
|**status**|**int**|用于描述列或参数的属性的位图：<br /><br /> **0x08** = 列允许 null 值。<br /><br /> **0x10** = ANSI 填充生效时**varchar**或**varbinary**已将列添加。 尾随空格会保留，以便**varchar**并保留尾部零**varbinary**列。<br /><br /> **0x40** = 参数是输出参数。<br /><br /> **0x80** = 列是标识列。|  
|**type**|**int**|将物理存储类型从[sys.systypes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)。|  
|**usertype**|**tinyint**|从用户定义数据类型的 ID [sys.systypes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)。|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**int**|此列的精度级别。|  
|**scale**|**int**|此列的小数位数。|  
|**iscomputed**|**int**|指示该列是否为计算列的标志：<br /><br /> **0** = 非计算。<br /><br /> **1** = 计算。|  
|**isoutparam**|**int**|指示过程参数是否为输出参数：<br /><br /> **1** = true。<br /><br /> **0** = false。|  
|**isnullable**|**int**|指示列是否允许空值：<br /><br /> **1** = true。<br /><br /> **0** = false。|  
|**排序规则**|**int**|列的排序规则的名称。 对于基于非字符的列为 NULL。|  
|**tdscollation**|**int**|在表格格式数据流 (TDS) 中返回的列的排序规则的名称。|  
  
## <a name="see-also"></a>请参阅  
 [异类数据库复制](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图&#40;Transact SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
