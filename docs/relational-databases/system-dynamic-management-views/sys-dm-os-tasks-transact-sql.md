---
title: sys. dm_os_tasks （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 086065aa79ca6fba7ad84e5b7e7f99f6f462f7dd
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164906"
---
# <a name="sysdm_os_tasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的每个活动任务返回一行。 任务是 SQL Server 中的基本执行单位。 任务的示例包括查询、登录、注销和系统任务（例如虚影清除活动、检查点活动、日志编写器、并行重做活动）。 有关任务的详细信息，请参阅[线程和任务体系结构指南](../../relational-databases/thread-and-task-architecture-guide.md)。
  
> [!NOTE]  
> 若要从 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 或 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]中调用此名称，请使用名称**sys.databases. dm_pdw_nodes_os_tasks**。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|对象的内存地址。|  
|**task_state**|**nvarchar(60)**|任务的状态。 可以是下列选项之一：<br /><br /> PENDING：正在等待工作线程。<br /><br /> RUNNABLE：可运行，但正在等待接收量程。<br /><br /> RUNNING：当前正在计划程序中运行。<br /><br /> SUSPENDED：具有工作线程，但正在等待事件。<br /><br /> DONE：已完成。<br /><br /> SPINLOOP：陷入自旋锁。|  
|**context_switches_count**|**int**|此任务完成的计划程序上下文切换数。|  
|**pending_io_count**|**int**|此任务执行的物理 I/O 数。|  
|**pending_io_byte_count**|**bigint**|此任务执行的总 I/O 字节数。|  
|**pending_io_byte_average**|**int**|此任务执行的平均 I/O 字节数。|  
|**scheduler_id**|**int**|父计划程序的 ID。 这是此任务的计划程序信息的句柄。 有关详细信息，请参阅[sys. &#40;dm_os_schedulers transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)。|  
|**session_id**|**int**|与任务关联的会话 ID。|  
|**exec_context_id**|**int**|与任务关联的执行上下文 ID。|  
|request_id|**int**|此任务的请求的 ID。 有关详细信息，请参阅[sys. &#40;dm_exec_requests transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)。|  
|**worker_address**|**varbinary(8)**|运行任务的工作线程的内存地址。<br /><br /> NULL = 任务正在等待工作线程以便运行，或者任务刚刚完成运行。<br /><br /> 有关详细信息，请参阅[sys. &#40;dm_os_workers transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)。|  
|**host_address**|**varbinary(8)**|主机的内存地址。<br /><br /> 0 = 不使用宿主创建任务。 这有助于标识用于创建此任务的主机。<br /><br /> 有关详细信息，请参阅[sys. &#40;dm_os_hosts transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md)。|  
|**parent_task_address**|**varbinary(8)**|作为该对象的父对象的任务的内存地址。|  
|pdw_node_id|**int**|**适用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分发所在的节点的标识符。|  
  
## <a name="permissions"></a>Permissions
在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上，需要 `VIEW SERVER STATE` 权限。   
在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 高级层上，需要数据库中的 `VIEW DATABASE STATE` 权限。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   

## <a name="examples"></a>示例  
  
### <a name="a-monitoring-parallel-requests"></a>A. 监视并行请求  
 对于并行执行的请求，您将看到同一组合的多个行（\<**session_id**>，\<**request_id**>）。 使用以下查询来查找为所有活动请求[配置最大并行度服务器配置选项](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)。  
  
> [!NOTE]  
>  **Request_id**在会话中是唯一的。  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>B. 使会话 ID 与 Windows 线程关联  
 可以使用以下查询将会话 ID 值与 Windows 线程 ID 相关联。 然后可以在 Windows 性能监视器中监视线程的性能。 以下查询不返回正在睡眠的会话的信息。  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
[与操作系统相关的&#40;&#41;动态管理视图 SQL Server transact-sql](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
[线程和任务体系结构指南](../../relational-databases/thread-and-task-architecture-guide.md)     
  


