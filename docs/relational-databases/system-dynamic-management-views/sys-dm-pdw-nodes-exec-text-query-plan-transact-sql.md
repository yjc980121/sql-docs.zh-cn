---
title: sys.databases _pdw_nodes_exec_text_query_plan （Transact-sql） |Microsoft Docs
description: 动态管理视图，以文本格式返回针对 TSQL 批处理或批处理中的特定语句的显示计划。
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 45f26c9569950c2450318abf546a838632e06f20
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145662"
---
# <a name="sysdm_pdw_nodes_exec_text_query_plan--transact-sql"></a>sys.databases _pdw_nodes_exec_text_query_plan （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理或批处理中的特定语句返回文本格式的显示计划。

## <a name="table-returned"></a>返回的表  
  
|列名|“名称”|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_ID**|**smallint**|与节点关联的唯一数字 ID。|
|**dbid**|**int**|在编译对应于此计划的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句时有效的上下文数据库的 ID。 对于临时和预定义 SQL 语句，指编译这些语句时所在的数据库的 ID。<br /><br /> 此列可为空值。|  
|**objectid**|**smallint**|此查询计划的对象（如存储过程或用户定义函数）的 ID。 对于即席和已准备批处理，此列为**null**。<br /><br /> 此列可为空值。|  
|**number**|**int**|为存储过程编号的整数。 对于即席和已准备批处理，此列为**null**。<br /><br /> 此列可为空值。| 
|**过**|**bit**|指示对应的存储过程是否已加密。<br /><br /> 0 = 未加密<br /><br /> 1 = 已加密<br /><br /> 此列不可为空值。|  
|**query_plan**|**nvarchar(max)**|包含用*plan_handle*指定的查询执行计划的编译时显示计划表示形式。 显示计划采用文本格式。 为包含即席 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句、存储过程调用以及用户定义函数调用等内容的每个批查询生成一个计划。<br /><br /> 此列可为空值。|  

## <a name="remarks"></a>注释  
[_Exec_text_query_plan](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql?view=sql-server-ver15)中的相同备注适用。  

## <a name="permissions"></a>Permissions  
 要求具有服务器上的**sysadmin**服务器角色或 `VIEW SERVER STATE` 权限。  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>后续步骤
 有关更多开发技巧，请参阅[SQL 数据仓库开发概述](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop)。