---
title: sys. dm_exec_query_profiles （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 10/25/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_profiles_TSQL
- sys.dm_exec_query_profiles_TSQL
- dm_exec_query_profiles
- sys.dm_exec_query_profiles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_profiles dynamic management view
ms.assetid: 54efc6cb-eea8-4f6d-a4d0-aa05eeb54081
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cd30a6c07bccde04bb38189fab00f688dd763356
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165502"
---
# <a name="sysdm_exec_query_profiles-transact-sql"></a>sys.dm_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

正执行查询时监视实时查询进度。 例如，使用此 DMV 确定运行缓慢的查询部分。 可使用说明字段中标识的列，将此 DMV 与其他系统 DMV 相联接。 或者，使用时间戳列，将此 DMV 与其他性能计数器（如性能计数器 xperf）相联接。  
  
## <a name="table-returned"></a>返回的表  
返回的计数器基于每个运算符和每个线程。 结果是动态的，并且不匹配现有选项（如 `SET STATISTICS XML ON`）的结果，这些选项仅在查询完成后才会创建输出。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|session_id|**int**|标识运行此查询的会话。 引用 dm_exec_sessions.session_id。|  
|request_id|**int**|确定目标请求。 引用 dm_exec_sessions.request_id。|  
|sql_handle|**varbinary(64)**|是唯一标识查询所属的批处理或存储过程的标记。 引用 dm_exec_query_stats.sql_handle。|  
|plan_handle|**varbinary(64)**|是一个标记，用于唯一标识已执行并且其计划驻留在计划缓存中或当前正在执行的批处理的查询执行计划。 引用 dm_exec_query_stats plan_handle。|  
|physical_operator_name|**nvarchar(256)**|物理运算符名称。|  
|node_id|**int**|标识查询树中的运算符节点。|  
|thread_id|**int**|区分属于同一个查询运算符节点的线程（针对并行查询）。|  
|task_address|**varbinary(8)**|确定此线程正在使用的 SQLOS 任务。 引用 dm_os_tasks.task_address。|  
|row_count|**bigint**|运算符迄今返回的行数。|  
|rewind_count|**bigint**|迄今为止的重绕数。|  
|rebind_count|**bigint**|迄今为止的重新绑定数。|  
|end_of_scan_count|**bigint**|迄今为止的扫描结束次数。|  
|estimate_row_count|**bigint**|估计的行数。 可用于将 estimated_row_count 与实际 row_count 进行比较。|  
|first_active_time|**bigint**|首次调用运算符的时间（毫秒）。|  
|last_active_time|**bigint**|上次调用运算符的时间（毫秒）。|  
|open_time|**bigint**|打开时的时间戳（毫秒）。|  
|first_row_time|**bigint**|打开第一行时的时间戳（毫秒）。|  
|last_row_time|**bigint**|打开最后一行时的时间戳（毫秒）。|  
|close_time|**bigint**|关闭时的时间戳（毫秒）。|  
|elapsed_time_ms|**bigint**|到目前为止，目标节点的操作所用的总运行时间（毫秒）。|  
|cpu_time_ms|**bigint**|到目前为止，目标节点的操作使用的总 CPU 时间（毫秒）。|  
|database_id|**int**|包含要对其进行读写的对象的数据库的 ID。|  
|object_id|**int**|要对其进行读写的对象的标识符。 引用 sys.objects.object_id。|  
|index_id|**int**|打开其行级的索引（如果有）。|  
|scan_count|**bigint**|迄今为止的表/索引扫描数。|  
|logical_read_count|**bigint**|迄今为止的逻辑读取数。|  
|physical_read_count|**bigint**|迄今为止的物理读取数。|  
|read_ahead_count|**bigint**|迄今为止的预读数。|  
|write_page_count|**bigint**|迄今为止由于溢出而导致的页写入数。|  
|lob_logical_read_count|**bigint**|迄今为止的 LOB 逻辑读取数。|  
|lob_physical_read_count|**bigint**|迄今为止的 LOB 物理读取数。|  
|lob_read_ahead_count|**bigint**|迄今为止的 LOB 预读数。|  
|segment_read_count|**int**|迄今为止的段预读数。|  
|segment_skip_count|**int**|迄今为止跳过的段数。| 
|actual_read_row_count|**bigint**|应用驻留谓词之前由运算符读取的行数。| 
|estimated_read_row_count|**bigint**|**适用于：** 从 [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] SP1 开始。 <br/>在应用残留谓词之前估计要由运算符读取的行数。|  
  
## <a name="general-remarks"></a>一般备注  
 如果查询计划节点没有任何 i/o，则所有与 i/o 相关的计数器都将设置为 NULL。  
  
 此 DMV 报告的与 i/o 相关的计数器比通过以下两种方式 `SET STATISTICS IO` 报告的计数器更精细：  
  
-   `SET STATISTICS IO` 将所有 i/o 的计数器一起组合在一起。 对于此 DMV，你将为查询计划中针对表执行 i/o 的每个节点获取单独的计数器。  
  
-   如果存在并行扫描，则此 DMV 将报告处理扫描的每个并行线程的计数器。
 
从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始，*标准查询执行统计信息分析基础结构*与*轻型查询执行统计分析基础结构*并存。 `SET STATISTICS XML ON` 和 `SET STATISTICS PROFILE ON` 始终使用*标准查询执行统计信息分析基础结构*。 对于要填充的 `sys.dm_exec_query_profiles`，必须启用其中一个查询分析基础结构。 有关详细信息，请参阅[查询分析基础结构](../../relational-databases/performance/query-profiling-infrastructure.md)。    

>[!NOTE]
> 正在调查的查询必须在启用了查询分析基础结构**后**开始，在查询开始后启用它将不会产生 `sys.dm_exec_query_profiles`结果。 有关如何启用查询分析基础结构的详细信息，请参阅[查询分析基础结构](../../relational-databases/performance/query-profiling-infrastructure.md)。

## <a name="permissions"></a>Permissions  
在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 托管实例上，需要 `VIEW DATABASE STATE` 权限和 `db_owner` 数据库角色的成员身份。   
在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 高级层上，需要数据库中的 `VIEW DATABASE STATE` 权限。 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   
   
## <a name="examples"></a>示例  
 步骤1：登录到计划运行查询的会话，你将使用 `sys.dm_exec_query_profiles`进行分析。 若要配置用于分析的查询 `SET STATISTICS PROFILE ON`。 在同一会话中运行你的查询。  
  
```sql  
--Configure query for profiling with sys.dm_exec_query_profiles  
SET STATISTICS PROFILE ON;  
GO  

--Or enable query profiling globally under SQL Server 2016 SP1 or above (not needed in SQL Server 2019)  
DBCC TRACEON (7412, -1);  
GO 
  
--Next, run your query in this session, or in any other session if query profiling has been enabled globally 
```  
  
 步骤2：登录到与运行查询的会话不同的第二个会话。  
  
 以下语句总结当前在会话 54 中运行的查询的进度。 为此，它基于每个节点的所有线程计算输出行的总数，然后将其与该节点的输出行的估算数目进行比较。  
  
```sql  
--Run this in a different session than the session in which your query is running. 
--Note that you may need to change session id 54 below with the session id you want to monitor.
SELECT node_id,physical_operator_name, SUM(row_count) row_count, 
  SUM(estimate_row_count) AS estimate_row_count, 
  CAST(SUM(row_count)*100 AS float)/SUM(estimate_row_count)  
FROM sys.dm_exec_query_profiles   
WHERE session_id=54
GROUP BY node_id,physical_operator_name  
ORDER BY node_id;  
```  
  
## <a name="see-also"></a>另请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与执行相关的动态管理视图和函数 (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
 
