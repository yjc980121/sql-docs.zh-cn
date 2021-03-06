---
title: sys.databases _pdw_request_steps （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/01/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 260b822d111f94fc567704cd908cb5632e3bdcaf
ms.sourcegitcommit: 27c267bf2a3cfaf2abcb5f3777534803bf4cffe5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2019
ms.locfileid: "73240772"
---
# <a name="sysdm_pdw_request_steps-transact-sql"></a>sys.databases _pdw_request_steps （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  保存有关 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]中组成给定请求或查询的所有步骤的信息。 每个查询步骤在表中各占一行。  
  
|Column Name|数据类型|Description|范围|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|request_id 和 step_index 构成了此视图的密钥。<br /><br /> 与请求关联的唯一数字 id。|请参阅 request_id 中的[_pdw_exec_requests &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)。|  
|step_index|**smallint**|request_id 和 step_index 构成了此视图的密钥。<br /><br /> 此步骤在组成请求的步骤序列中的位置。|对于包含 n 个步骤的请求，为0到（n-1）。|  
|operation_type|**nvarchar(35)**|此步骤表示的操作类型。|**DMS 查询计划操作：** "ReturnOperation"、"PartitionMoveOperation"、"MoveOperation"、"BroadcastMoveOperation"、"ShuffleMoveOperation"、"TrimMoveOperation"、"CopyOperation"、"DistributeReplicatedTableMoveOperation"<br /><br /> **SQL 查询计划操作：** "OnOperation"、"RemoteOperation"<br /><br /> **其他查询计划操作：** 'MetaDataCreateOperation', 'RandomIDOperation'<br /><br /> **读取的外部操作：** 'HadoopShuffleOperation', 'HadoopRoundRobinOperation', 'HadoopBroadcastOperation'<br /><br /> **MapReduce 的外部操作：** 'HadoopJobOperation', 'HdfsDeleteOperation'<br /><br /> **写入的外部操作：** 'ExternalExportDistributedOperation', 'ExternalExportReplicatedOperation', 'ExternalExportControlOperation'<br /><br /> 有关详细信息，请参阅 [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]中的 "了解查询计划"。 <br /><br />  查询计划还可能会受数据库设置的影响。  有关详细信息，请参阅[ALTER DATABASE SET 选项](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql-set-options?toc=/azure/sql-data-warehouse/toc.json&bc=/azure/sql-data-warehouse/breadcrumb/toc.json&view=azure-sqldw-latest)。|  
|distribution_type|**nvarchar(32)**|此步骤将经历的分发类型。|"AllNodes"、"AllDistributions"、"AllComputeNodes"、"ComputeNode"、"分发"、"SubsetNodes"、"SubsetDistributions"、"未指定"|  
|location_type|**nvarchar(32)**|步骤的运行位置。|"Compute"、"Control"、"DMS"|  
|status|**nvarchar(32)**|此步骤的状态。|挂起、正在运行、已完成、失败、UndoFailed、PendingCancel、已取消、已中止|  
|error_id|**nvarchar （36）**|与此步骤关联的错误的唯一 id （如果有）。|请参阅 error_id of [sys.databases _pdw_errors &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md)。 如果未发生错误，则为 NULL。|  
|start_time|**datetime**|步骤开始执行的时间。|小于或等于当前时间，大于或等于此步骤所属的查询的 end_compile_time。 有关查询的详细信息，请参阅[_pdw_exec_requests &#40;&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)。|  
|end_time|**datetime**|此步骤完成执行、已取消或失败的时间。|小于或等于当前时间，大于或等于 start_time。 对于当前正在执行或已排队的步骤，将设置为 NULL。|  
|total_elapsed_time|**smallint**|查询步骤已运行的总时间（以毫秒为单位）。|介于0与 end_time 与 start_time 之间的差异之间。 对于排队步骤，为0。<br /><br /> 如果 total_elapsed_time 超出了整数的最大值，则 total_elapsed_time 将继续作为最大值。 此条件将生成警告 "已超过最大值。"<br /><br /> 最大值（以毫秒为单位）等效于24.8 天。|  
|row_count|**bigint**|此请求更改或返回的总行数。|0表示未更改或返回数据的步骤。 否则，受影响的行数。|  
|command|**nvarchar(4000)**|保存此步骤的命令的完整文本。|步骤的任何有效请求字符串。 如果操作的类型为 MetaDataCreateOperation，则为 NULL。 如果长度超过4000个字符，则截断。|  
  
 有关此视图保留的最大行数的信息，请参阅 [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]中 "最小值和最大值" 中 "系统视图值的最大值" 部分。  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
