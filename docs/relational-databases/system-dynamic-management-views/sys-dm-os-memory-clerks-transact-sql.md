---
title: sys. dm_os_memory_clerks （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_memory_clerks
- sys.dm_os_memory_clerks
- dm_os_memory_clerks_TSQL
- sys.dm_os_memory_clerks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_clerks dynamic management view
ms.assetid: 1d556c67-5c12-46d5-aa8c-7ec1bb858df7
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 97805251e309132892fb94db63a308b10657daff
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983102"
---
# <a name="sysdm_os_memory_clerks-transact-sql"></a>sys.dm_os_memory_clerks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中当前处于活动状态的全部内存分配器的集合。  
  
> [!NOTE]  
>  若要从 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 或 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]中调用此名称，请使用名称**sys.databases. dm_pdw_nodes_os_memory_clerks**。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**memory_clerk_address**|**varbinary(8)**|指定内存分配器的唯一内存地址。 这是主键列。 不可为 null。|  
|**type**|**nvarchar(60)**|指定内存分配器的类型。 每个分配器都具有特定类型，例如，CLR Clerks MEMORYCLERK_SQLCLR。 不可为 null。|  
|**名称**|**nvarchar(256)**|指定在内部为此内存分配器分配的名称。 一个组件可拥有多个特定类型的内存分配器。 组件可选择使用特定名称来标识相同类型的内存分配器。 不可为 null。|  
|**memory_node_id**|**int**|指定内存节点的 ID。 不可为 Null。|  
|**single_pages_kb**|**bigint**|**适用于**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。|  
|**pages_kb**|**bigint**|**适用于**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本。<br /><br /> 指定为此内存分配器分配的页内存量 (KB)。 不可为 null。|  
|**multi_pages_kb**|**bigint**|**适用于**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。<br /><br /> 分配的多页内存量 (KB)。 这是使用内存节点的多页分配器分配的内存量。 此内存在缓冲池外面分配，利用了内存节点虚拟分配器的优势。 不可为 null。|  
|**virtual_memory_reserved_kb**|**bigint**|指定内存分配器保留的虚拟内存量。 不可为 null。|  
|**virtual_memory_committed_kb**|**bigint**|指定内存分配器提交的虚拟内存量。 提交的内存量应始终小于保留的内存量。 不可为 null。|  
|**awe_allocated_kb**|**bigint**|指定在物理内存中锁定且未由操作系统调出的内存量 (KB) 。 不可为 null。|  
|**shared_memory_reserved_kb**|**bigint**|指定内存分配器保留的共享内存量。 保留以供共享内存和文件映射使用的内存量。 不可为 null。|  
|**shared_memory_committed_kb**|**bigint**|指定内存分配器提交的共享内存量。 不可为 null。|  
|**page_size_in_bytes**|**bigint**|指定此内存分配器的页分配粒度。 不可为 null。|  
|**page_allocator_address**|**varbinary(8)**|指定页分配器的地址。 此地址对内存分配器是唯一的，可在**sys. dm_os_memory_objects**中用于查找绑定到此职员的内存对象。 不可为 null。|  
|**host_address**|**varbinary(8)**|指定用于此内存分配器的主机的内存地址。 有关详细信息，请参阅[sys. &#40;dm_os_hosts transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md)。 组件（如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client）通过主机接口访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存资源。<br /><br /> 0x00000000 = 属于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的内存分配器。<br /><br /> 不可为 null。|  
|pdw_node_id|**int**|**适用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分发所在的节点的标识符。|  
  
## <a name="permissions"></a>Permissions 

在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上，需要 `VIEW SERVER STATE` 权限。   
在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 高级层上，需要数据库中的 `VIEW DATABASE STATE` 权限。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存管理器由一个三层的层次结构组成。 该层次结构的底层为内存节点。 中间层由内存分配器、内存缓存和内存池组成。 顶层由内存对象组成。 这些对象通常用于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中分配内存。  
  
 内存节点提供低级分配器的界面和实现。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，只有内存内存分配器可访问内存节点。 内存分配器访问内存节点界面以分配内存。 内存节点还会跟踪 Clerk 分配的内存以进行诊断。 分配大量内存的每个组件，都必须使用分配器界面来创建其自己的内存分配器并分配其全部内存。 各组件会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动时频繁创建其相应的分配器。  
  
## <a name="see-also"></a>另请参阅  

 [与操作系统相关的&#40;&#41;动态管理视图 SQL Server transact-sql](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)   
 [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)  
  
  


