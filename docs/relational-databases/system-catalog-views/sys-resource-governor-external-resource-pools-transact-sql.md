---
title: sys.resource_governor_external_resource_pools (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_external_resource_pools
- sys.resource_governor_external_resource_pools_TSQL
- resource_governor_external_resource_pools
- resource_governor_external_resource_pools_TSQL
helpviewer_keywords:
- sys.resource_governor_external_resource_pools
- resource_governor_external_resource_pools
ms.assetid: 75063e36-a91b-496f-9936-88f3d57bd447
author: stevestein
ms.author: sstein
ms.openlocfilehash: 379dae51b913fc02a16a562037776620b1e0433c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904477"
---
# <a name="sysresourcegovernorexternalresourcepools-transact-sql"></a>sys.resource_governor_external_resource_pools (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
适用范围：[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] 和 [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] 

返回存储的外部资源池配置中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 视图的每一行都确定了一个池的配置。
  
|列名|数据类型|描述|
|-----------------|---------------|-----------------|
|pool_id|**int**|资源池的唯一 ID。 不可为 null。<br /><br /> **注意：** 可能会重命名在将来。|
|name|**sysname**|资源池的名称。 不可为 null。|
|max_cpu_percent|**int**|出现 CPU 争用时资源池中的所有请求可获得的最大 CPU 带宽。 不可为 null。|
|max_memory_percent|**int**|此资源池中的请求可使用的总服务器内存量的百分比。 不可为 null。 有效的最大值取决于池的最小值。 例如，可将 max_memory_percent 设置为 100，但有效的最大值会更低一些。|
|max_processes|**int**|最大并发外部进程数。 默认值为 0，指定没有限制。 不可为 null。|
|version|**bigint**|内部版本号。|
  
## <a name="permissions"></a>权限

需要 VIEW SERVER STATE 权限。

## <a name="see-also"></a>请参阅

[SQL Server 中机器学习的资源调控](../../advanced-analytics/r/resource-governance-for-r-services.md)

[资源调控器目录视图&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)

[sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)

[资源调控器](../../relational-databases/resource-governor/resource-governor.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[“已启用外部脚本”服务器配置选项](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
