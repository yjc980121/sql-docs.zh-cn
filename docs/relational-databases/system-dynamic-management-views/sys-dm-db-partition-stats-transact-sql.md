---
title: "sys.dm_db_partition_stats (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_partition_stats
- dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_partition_stats dynamic management view
ms.assetid: 9db9d184-b3a2-421e-a804-b18ebcb099b7
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b58fb8b2933e99f2eb77dc03ed7fdfbb132375a6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbpartitionstats-transact-sql"></a>sys.dm_db_partition_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回当前数据库中每个分区的页和行计数信息。  
  
> [!NOTE]  
>  若要从我们称之为[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名称**sys.dm_pdw_nodes_db_partition_stats**。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|分区 ID。 在数据库中是唯一的。 这是相同的值**partition_id**中**sys.partitions**目录视图|  
|**object_id**|**int**|包含该分区的表或索引视图的对象 ID。|  
|**index_id**|**int**|包含该分区的堆或索引的 ID。<br /><br /> 0 = 堆<br /><br /> 1 = 聚集索引。<br /><br /> > 1 = 非聚集索引|  
|**partition_number**|**int**|索引或堆中从 1 开始的分区号。|  
|**in_row_data_page_count**|**bigint**|分区中存储行内数据所用的页数。 如果分区是堆的一部分，则该值为堆中的数据页数。 如果分区是索引的一部分，则该值为叶级别中的页数。 （未计入 B 树中非叶页的数目。）以上两种情况都未计入 IAM（索引分配映射）页。 对于 xVelocity 内存优化列存储索引，始终为 0。|  
|**in_row_used_page_count**|**bigint**|用于存储和管理分区中的行内数据的总页数。 此计数包括非叶 B 树页、 IAM 页和包含的全部页**in_row_data_page_count**列。 对列存储索引始终为 0。|  
|**in_row_reserved_page_count**|**bigint**|为存储和管理该分区中的行内数据而保留的总页数，包括已使用的和未使用的页。 对列存储索引始终为 0。|  
|**lob_used_page_count**|**bigint**|用于存储和管理扩展的行中的页面数量**文本**， **ntext**，**映像**， **varchar （max)**， **nvarchar(max)**， **varbinary （max)**，和**xml**分区内的列。 包含 IAM 页。<br /><br /> 用于存储和管理分区中的列存储索引的 LOB 总数。|  
|**lob_reserved_page_count**|**bigint**|保留用于存储和管理扩展的行的页的总数**文本**， **ntext**，**映像**， **varchar （max)**， **nvarchar (max)**， **varbinary （max)**，和**xml**分区，而不考虑页是否正在使用或不内的列。 包含 IAM 页。<br /><br /> 为存储和管理分区中的列存储索引而保留的 LOB 总数。|  
|**row_overflow_used_page_count**|**bigint**|中用于存储和管理行溢出的页数**varchar**， **nvarchar**， **varbinary**，和**sql_variant**列内分区。 包含 IAM 页。<br /><br /> 对列存储索引始终为 0。|  
|**row_overflow_reserved_page_count**|**bigint**|保留以供存储和管理行溢出的页的总数**varchar**， **nvarchar**， **varbinary**，和**sql_variant**在分区，而不考虑页是否正在使用或不内的列。 包含 IAM 页。<br /><br /> 对列存储索引始终为 0。|  
|**used_page_count**|**bigint**|用于分区的总页数。 计算为**in_row_used_page_count** + **lob_used_page_count** + **row_overflow_used_page_count**。|  
|**reserved_page_count**|**bigint**|为分区保留的总页数。 计算为**in_row_reserved_page_count** + **lob_reserved_page_count** + **row_overflow_reserved_page_count**。|  
|**row_count**|**bigint**|分区中的大约行数。|  
|**pdw_node_id**|**int**|**适用于**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]，[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分布的节点标识符。|  
|**distribution_id**|**int**|**适用于**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]，[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 分发与关联的唯一数字 id。|  
  
## <a name="remarks"></a>注释  
 **sys.dm_db_partition_stats**显示有关用于存储和管理行内数据 LOB 数据和数据库中的所有分区的行溢出数据的空间的信息。 每个分区对应一行。  
  
 作为输出数据依据的计数缓存在内存中，或存储在磁盘中的各种系统表中。  
  
 行内数据、LOB 数据以及行溢出数据表示构成分区的三个分配单元。 [Sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)目录视图可查询的有关数据库中每个分配单元的元数据。  
  
 如果堆或索引未分区，则它由一个分区（分区号为 1）组成，因而只会为该堆或索引返回一行。 [Sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)目录视图可查询的有关每个分区的所有表和数据库中的索引的元数据。  
  
 可以通过求全部相关分区计数的和来获取单个表或单个索引的总计数。  
  
## <a name="permissions"></a>Permissions  
 要求对查询的 VIEW DATABASE STATE 权限**sys.dm_db_partition_stats**动态管理视图。 有关动态管理视图权限的详细信息，请参阅[动态管理视图和函数 &#40;Transact SQL &#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-all-counts-for-all-partitions-of-all-indexes-and-heaps-in-a-database"></a>A. 返回数据库中全部索引和堆的全部分区的所有计数  
 以下示例演示了 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中全部索引和堆的全部分区的所有计数。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats;  
GO  
```  
  
### <a name="b-returning-all-counts-for-all-partitions-of-a-table-and-its-indexes"></a>B. 返回表及其索引的全部分区的所有计数  
 以下示例演示了 `HumanResources.Employee` 表及其索引的全部分区的所有计数。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats   
WHERE object_id = OBJECT_ID('HumanResources.Employee');  
GO  
```  
  
### <a name="c-returning-total-used-pages-and-total-number-of-rows-for-a-heap-or-clustered-index"></a>C. 返回堆或聚集索引使用的总页数和总行数  
 以下示例返回 `HumanResources.Employee` 表的堆或聚集索引使用的总页数和总行数。 因为默认情况不对 `Employee` 表分区，请注意和仅包含一个分区。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT SUM(used_page_count) AS total_number_of_used_pages,   
    SUM (row_count) AS total_number_of_rows   
FROM sys.dm_db_partition_stats  
WHERE object_id=OBJECT_ID('HumanResources.Employee')    AND (index_id=0 or index_id=1);  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与数据库相关的动态管理视图 &#40;Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  

