---
title: sys.syscolumns (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-enginel, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscolumns
- sys.syscolumns_TSQL
- syscolumns_TSQL
- syscolumns
dev_langs:
- TSQL
helpviewer_keywords:
- syscolumns system table
- sys.syscolumns compatibility view
ms.assetid: 863fd87b-ff33-4ac5-9aa9-df21140681da
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c158533188db7e3d72235a69bff1b14546a1a1a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089242"
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  为每个表和视图中的每列返回一行，并为数据库中的存储过程的每个参数返回一行。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|列或过程参数的名称。|  
|**id**|**int**|此列所属表的对象 ID，或者与此参数关联的存储过程的 ID。|  
|**xtype**|**tinyint**|物理存储类型**sys.types**。|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|用户定义的扩展的数据类型的 ID。 如果数据类型的数字超过 32,767，则溢出或返回 NULL。|  
|**length**|**smallint**|从最大物理存储长度**sys**。**类型**。|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**列 id**|**smallint**|列 ID 或参数 ID。|  
|**xoffset**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**保留**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|此列的默认值的 ID。|  
|**域**|**int**|此列的规则或 CHECK 约束的 ID。|  
|**number**|**smallint**|过程分组时的子过程号。<br /><br /> 0 = 非过程项|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary(8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**smallint**|此列所在行的偏移量。|  
|**collationid**|**int**|列的排序规则的 ID。 对于非字符列，此值为 NULL。|  
|**status**|**tinyint**|用于说明列或参数的属性的位图：<br /><br /> 0x08 = 列允许空值。<br /><br /> 0x10 = ANSI 填充生效时**varchar**或**varbinary**已将列添加。 尾随空格会保留，以便**varchar**并保留尾部零**varbinary**列。<br /><br /> 0x40 = 参数为 OUTPUT 参数。<br /><br /> 0x80 = 列为标识列。|  
|**type**|**tinyint**|物理存储类型**sys**。**类型**。|  
|**usertype**|**smallint**|从用户定义数据类型的 ID **sys.types**。 如果数据类型的数字超过 32,767，则溢出或返回 NULL。|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|此列的精度级别。<br /><br /> -1 = **xml**或大值类型。|  
|**scale**|**int**|此列的小数位数。<br /><br /> NULL = 数据类型不是数值。|  
|**iscomputed**|**int**|指示列是否为计算列的标志：<br /><br /> 0 = 非计算列。<br /><br /> 1 = 计算列。|  
|**isoutparam**|**int**|指示过程参数是否为输出参数：<br /><br /> 1 = True<br /><br /> 0 = False|  
|**isnullable**|**int**|指示列是否允许空值：<br /><br /> 1 = True<br /><br /> 0 = False|  
|**排序规则**|**sysname**|列的排序规则的名称。 如果不是基于字符的列，则为 NULL。|  
  
## <a name="see-also"></a>请参阅  
 [系统表映射到系统视图&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
