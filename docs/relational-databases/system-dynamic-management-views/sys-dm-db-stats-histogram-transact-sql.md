---
title: sys.dm_db_stats_histogram (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_stats_histogram
- sys.dm_db_stats_histogram_TSQL
- dm_db_stats_histogram
- dm_db_stats_histogram_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_stats_histogram dynamic management function
ms.assetid: 1897fd4a-8d51-461e-8ef2-c60be9e563f2
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e5a79a4ab38fd1cb7d118624fd170219aa90a94
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096256"
---
# <a name="sysdmdbstatshistogram-transact-sql"></a>sys.dm_db_stats_histogram (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

返回指定的数据库对象 （表或索引的视图） 的统计信息直方图中当前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库。 类似于`DBCC SHOW_STATISTICS WITH HISTOGRAM`。

> [!NOTE] 
> 此 DMF 是从开始提供[!INCLUDE[ssSQL15](../../includes/ssSQL15-md.md)]SP1 CU2

## <a name="syntax"></a>语法  
  
```  
sys.dm_db_stats_histogram (object_id, stats_id)  
```  
  
## <a name="arguments"></a>参数  
 *object_id*  
 当前数据库中您要请求其某个统计信息属性的对象的 ID。 *object_id* 是 **int**。  
  
 *stats_id*  
 指定 *object_id*的统计信息 ID。 可以从 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) 动态管理视图获取该统计信息 ID。 *stats_id* 是 **int**。  
  
## <a name="table-returned"></a>返回的表  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|object_id |**int**|要返回统计信息对象属性的对象（表或索引视图）的 ID。|  
|stats_id |**int**|统计信息对象的 ID。 在表或索引视图中是唯一的。 有关详细信息，请参阅 [sys.stats (Transact-SQL)](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)。|  
|step_number |**int** |在直方图中的步数。 |
|range_high_key |**sql_variant** |直方图梯级的上限列值。 列值也称为键值。|
|range_rows |**real** |其列值位于直方图梯级内（不包括上限）的行的估算数目。 |
|equal_rows |**real** |其列值等于直方图梯级的上限的行的估算数目。 |
|distinct_range_rows |**bigint** |非重复列值位于直方图梯级内（不包括上限）的行的估算数目。 |
|average_range_rows |**real** |平均重复列值位于直方图梯级，不包括上限内的行数 (`RANGE_ROWS / DISTINCT_RANGE_ROWS`为`DISTINCT_RANGE_ROWS > 0`)。 |
  
 ## <a name="remarks"></a>备注  
 
 结果集`sys.dm_db_stats_histogram`返回的信息类似于`DBCC SHOW_STATISTICS WITH HISTOGRAM`并且还包括`object_id`， `stats_id`，和`step_number`。

 因为该列`range_high_key`为 sql_variant 数据类型，您可能需要使用`CAST`或`CONVERT`如果谓词与非字符串常量进行比较。

### <a name="histogram"></a>直方图
  
 直方图度量数据集中每个非重复值的出现频率。 查询优化器根据统计信息对象第一个键列中的列值来计算直方图，它选择列值的方法是以统计方式对行进行抽样或对表或视图中的所有行执行完全扫描。 如果直方图是根据一组抽样行创建的，存储的总行数和非重复值总数则为估计值，且不必为整数。  
  
 若要创建直方图，查询优化器将对列值进行排序，计算与每个非重复列值匹配的值数，然后将列值聚合到最多 200 个连续直方图梯级中。 每个梯级都包含一个列值范围，后跟上限列值。 该范围包括介于两个边界值之间的所有可能列值，但不包括边界值自身。 最小排序列值是第一个直方图梯级的上限值。  
  
 下面的关系图显示包含六个梯级的直方图。 第一个上限值左侧的区域是第一个梯级。  
  
 ![](../../relational-databases/system-dynamic-management-views/media/histogram_2.gif "直方图")  
  
 对于每个直方图梯级：  
  
-   粗线表示上限值 (range_high_key  ) 和上限值的出现次数 (equal_rows  )  
  
-   range_high_key  左侧的纯色区域表示列值范围和每个列值的平均出现次数 (average_range_rows  )。 第一个直方图梯级的 average_range_rows  始终是 0。  
  
-   点线表示用于估计范围中的非重复值总数 (distinct_range_rows  ) 和范围中的总指数 (range_rows  )。 查询优化器使用 range_rows  和 distinct_range_rows  计算 average_range_rows  ，且不存储抽样值。  
  
 查询优化器按照直方图梯级的统计重要性来定义直方图梯级。 它使用最大差异算法使直方图中的梯级减至最少，并同时最大化边界值之间的差异。 最大梯级数为 200。 直方图梯级数可以少于非重复值的数目，即使对于边界点少于 200 的列也是如此。 例如，具有 100 个非重复值的列所具有的直方图的边界点可以少于 100。  
  
## <a name="permissions"></a>权限  

要求用户对统计信息列拥有 select 权限，或用户拥有表，或用户是 `sysadmin` 固定服务器角色、`db_owner` 固定数据库角色或 `db_ddladmin` 固定数据库角色的成员。

## <a name="examples"></a>示例  

### <a name="a-simple-example"></a>A. 简单示例    
下面的示例创建并填充一个简单的表。 然后上创建统计信息`Country_Name`列。

```sql
CREATE TABLE Country
(Country_ID int IDENTITY PRIMARY KEY,
Country_Name varchar(120) NOT NULL);
INSERT Country (Country_Name) VALUES ('Canada'), ('Denmark'), ('Iceland'), ('Peru');

CREATE STATISTICS Country_Stats  
    ON Country (Country_Name) ;  
```   
主键占用`stat_id`编号为 1，因此请调用`sys.dm_db_stats_histogram`有关`stat_id`两种模式，返回的统计信息直方图`Country`表。    
```sql     
SELECT * FROM sys.dm_db_stats_histogram(OBJECT_ID('Country'), 2);
```

### <a name="b-useful-query"></a>B. 有用的查询：   
```sql  
SELECT hist.step_number, hist.range_high_key, hist.range_rows, 
    hist.equal_rows, hist.distinct_range_rows, hist.average_range_rows
FROM sys.stats AS s
CROSS APPLY sys.dm_db_stats_histogram(s.[object_id], s.stats_id) AS hist
WHERE s.[name] = N'<statistic_name>';
```

### <a name="c-useful-query"></a>C. 有用的查询：
下面的示例从表中选择`Country`通过在列上谓词`Country_Name`。

```sql  
SELECT * FROM Country 
WHERE Country_Name = 'Canada';
```

下面的示例在表上查看以前创建的统计信息`Country`和列`Country_Name`直方图梯级匹配上述查询中的谓词。

```sql  
SELECT ss.name, ss.stats_id, shr.steps, shr.rows, shr.rows_sampled, 
    shr.modification_counter, shr.last_updated, sh.range_rows, sh.equal_rows
FROM sys.stats ss
INNER JOIN sys.stats_columns sc 
    ON ss.stats_id = sc.stats_id AND ss.object_id = sc.object_id
INNER JOIN sys.all_columns ac 
    ON ac.column_id = sc.column_id AND ac.object_id = sc.object_id
CROSS APPLY sys.dm_db_stats_properties(ss.object_id, ss.stats_id) shr
CROSS APPLY sys.dm_db_stats_histogram(ss.object_id, ss.stats_id) sh
WHERE ss.[object_id] = OBJECT_ID('Country') 
    AND ac.name = 'Country_Name'
    AND sh.range_high_key = CAST('Canada' AS CHAR(8));
```
  
## <a name="see-also"></a>请参阅  
[DBCC SHOW_STATISTICS (Transact SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
[与对象相关的动态管理视图和函数 (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
