---
title: sys. dm_os_sys_info （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_sys_info_TSQL
- dm_os_sys_info
- dm_os_sys_info_TSQL
- sys.dm_os_sys_info
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_info dynamic management view
- time [SQL Server], instance started
- starting time
ms.assetid: 20f6bc9c-839a-4fa4-b3f3-a6c47d1b69af
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ddc70ef475eb5e4ddc91095ce251c383ca4cdbf
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983164"
---
# <a name="sysdm_os_sys_info-transact-sql"></a>sys.dm_os_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  返回一组有关计算机和有关 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 可用资源及其已占用资源的有用杂项信息。  
  
> **注意：** 若要从 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 或 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]中调用此名称，请使用名称**sys.databases. dm_pdw_nodes_os_sys_info**。  
  
|列名|数据类型|说明和版本特定说明 |  
|-----------------|---------------|-----------------|  
|**cpu_ticks**|**bigint**|指定当前的 CPU 时钟周期计数。 CPU 时钟周期数是从处理器的 RDTSC 计数器获得的。 它是一个仅增加的数字。 不可为 Null。|  
|**ms_ticks**|**bigint**|指定自从计算机启动以来的毫秒数。 不可为 Null。|  
|**cpu_count**|**int**|指定系统中的逻辑 CPU 数。 不可为 Null。|  
|**hyperthread_ratio**|**int**|指定一个物理处理器包公开的逻辑内核数与物理内核数的比。 不可为 Null。|  
|**physical_memory_in_bytes**|**bigint**|适用范围：**到**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。<br /><br /> 指定计算机上的物理内存总量。 不可为 Null。|  
|**physical_memory_kb**|**bigint**|**适用于**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本。<br /><br /> 指定计算机上的物理内存总量。 不可为 Null。|  
|**virtual_memory_in_bytes**|**bigint**|适用范围：**到**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。<br /><br /> 对用户模式进程可用的虚拟内存的数量。 通过使用 3 GB 开关，可以用它来确定是否 SQL Server 已启动。|  
|**virtual_memory_kb**|**bigint**|**适用于**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本。<br /><br /> 指定对用户模式进程可用的虚拟地址空间的总量。 不可为 Null。|  
|**bpool_commited**|**int**|适用范围：**到**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。<br /><br /> 表示内存管理器中的已提交内存 (KB)。 不包括内存管理器中的保留内存。 不可为 Null。|  
|**committed_kb**|**int**|**适用于**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本。<br /><br /> 表示内存管理器中的已提交内存 (KB)。 不包括内存管理器中的保留内存。 不可为 Null。|  
|**bpool_commit_target**|**int**|适用范围：**到**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。<br /><br /> 表示 SQL Server 内存管理器可以占用的内存量 (KB)。|  
|**committed_target_kb**|**int**|**适用于**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本。<br /><br /> 表示 SQL Server 内存管理器可以占用的内存量 (KB)。 使用类似如下的不同输入计算目标量：<br /><br /> -包括其负载的系统的当前状态<br /><br /> -当前进程请求的内存<br /><br /> -计算机上安装的内存量<br /><br /> -配置参数<br /><br /> 如果**committed_target_kb**大于**committed_kb**，则内存管理器将尝试获得额外内存。 如果**committed_target_kb**小于**committed_kb**，则内存管理器将尝试减少提交的内存量。 **Committed_target_kb**始终包括盗用内存和保留内存。 不可为 Null。|  
|**bpool_visible**|**int**|适用范围：**到**[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。<br /><br /> 在进程虚拟地址空间中可直接访问的缓冲池中的 8 KB 缓冲区数。 当未使用地址窗口化扩展插件 (AWE)，缓冲区池已获取其内存目标 (bpool_committed = bpool_commit_target) 时，bpool_visible 的值与 bpool_committed 的值相等。当在 32 位版本的 SQL Server 上使用 AWE 时，bpool_visible 表示用于访问由缓冲池区分配的物理内存的 AWE 映射窗口的大小。 此映射窗口的大小由进程地址空间绑定，因此，可见数量将小于提交数量，并且通过为数据库页之外的其他用途而消耗内存的内部组件会进一步减少可见数量。 如果 bpool_visible 的值太低，则可能收到内存不足错误。|  
|**visible_target_kb**|**int**|**适用于**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本。<br /><br /> 与**committed_target_kb**相同。 不可为 Null。|  
|**stack_size_in_bytes**|**int**|指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建的每个线程的调用堆栈的大小。 不可为 Null。|  
|**os_quantum**|**bigint**|表示非抢先任务的量程（以毫秒数度量）。 量程（秒） = **os_quantum** /CPU 时钟速度。 不可为 Null。|  
|**os_error_mode**|**int**|指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的错误模式。 不可为 Null。|  
|**os_priority_class**|**int**|指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的优先级类。 可以为 NULL。<br /><br /> 32 = 正常（错误日志将指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正以正常的优先级基数 (=7) 启动）。<br /><br /> 128 = 高（错误日志将指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正以高优先级基数启动）。  (=13)。）<br /><br /> 有关详细信息，请参阅 [Configure the priority boost Server Configuration Option](../../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md)。|  
|**max_workers_count**|**int**|表示可以创建的最大工作线程数。 不可为 Null。|  
|**scheduler_count**|**int**|表示在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程中配置的用户计划程序数。 不可为 Null。|  
|**scheduler_total_count**|**int**|表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的计划程序总数。 不可为 Null。|  
|**deadlock_monitor_serial_number**|**int**|指定当前死锁监视序列的 ID。 不可为 Null。|  
|**sqlserver_start_time_ms_ticks**|**bigint**|表示上次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时的**ms_tick**数字。 与当前 ms_ticks 列进行比较。 不可为 Null。|  
|**sqlserver_start_time**|**datetime**|指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上次启动时的日期和时间。 不可为 Null。|  
|**affinity_type**|**int**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 指定当前使用中的服务器 CPU 进程关联的类型。 不可为 Null。 有关详细信息，请参阅[ALTER SERVER &#40;CONFIGURATION transact-sql&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)。<br /><br /> 1 = MANUAL<br /><br /> 2 = AUTO|  
|**affinity_type_desc**|**varchar(60)**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 介绍**affinity_type**列。 不可为 Null。<br /><br /> MANUAL = 已为至少一个 CPU 设置关联。<br /><br /> AUTO = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以自由地在 CPU 之间移动线程。|  
|**process_kernel_time_ms**|**bigint**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 内核模式下所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 线程所用的总时间（毫秒）。 该值可能会大于单处理器时钟，因为它包括服务器上所有处理器的时间。 不可为 Null。|  
|**process_user_time_ms**|**bigint**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 用户模式下所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 线程所用的总时间（毫秒）。 该值可能会大于单处理器时钟，因为它包括服务器上所有处理器的时间。 不可为 Null。|  
|**time_source**|**int**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于检索时钟时间的 API。 不可为 Null。<br /><br /> 0 = QUERY_PERFORMANCE_COUNTER<br /><br /> 1 = MULTIMEDIA_TIMER|  
|**time_source_desc**|**nvarchar(60)**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 介绍**time_source**列。 不可为 Null。<br /><br /> QUERY_PERFORMANCE_COUNTER = [QueryPerformanceCounter](https://go.microsoft.com/fwlink/?LinkId=163095) API 检索时钟时间。<br /><br /> MULTIMEDIA_TIMER = 用于检索时钟时间的[多媒体计时器](https://go.microsoft.com/fwlink/?LinkId=163094)API。|  
|**virtual_machine_type**|**int**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否正在虚拟环境下运行。  不可为 Null。<br /><br /> 0 = NONE<br /><br /> 1 = HYPERVISOR<br /><br /> 2 = OTHER|  
|**virtual_machine_type_desc**|**nvarchar(60)**|**适用于**：[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 及更高版本。<br /><br /> 介绍**virtual_machine_type**列。 不可为 Null。<br /><br /> 无 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未在虚拟机中运行。<br /><br /> 虚拟机监控程序 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在运行虚拟机监控程序的 OS （使用硬件辅助虚拟化的主机操作系统）中运行的虚拟机中运行。<br /><br /> 其他 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在由不使用硬件助理（如 Microsoft Virtual PC）的 OS 托管的虚拟机中运行。|  
|**softnuma_configuration**|**int**|**适用于**：[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 及更高版本。<br /><br /> 指定 NUMA 节点的配置方式。 不可为 Null。<br /><br /> 0 = OFF 表示硬件默认值<br /><br /> 1 = 自动软件 NUMA<br /><br /> 2 = 通过注册表手动进行软件 NUMA|  
|**softnuma_configuration_desc**|**nvarchar(60)**|**适用于**：[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 及更高版本。<br /><br /> OFF = 软 NUMA 功能已关闭<br /><br /> ON = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自动确定 NUMA 节点大小的软件 NUMA<br /><br /> 手动 = 手动配置的软件 NUMA|
|**process_physical_affinity**|**nvarchar(3072)** |**适用于：** 从 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]开始。<br /><br />信息有待提供。 |
|**sql_memory_model**|**int**|**适用于：** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 及更高版本。<br /><br />指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用来分配内存的内存模型。 不可为 Null。<br /><br />1 = 常规内存模型<br />2 = 锁定内存页<br /> 3 = 内存中的大型页面|
|**sql_memory_model_desc**|**nvarchar(120)**|**适用于：** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 及更高版本。<br /><br />指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用来分配内存的内存模型。 不可为 Null。<br /><br />**传统** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用常规内存模型来分配内存。 这是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户在启动过程中没有锁定页面的内存特权时，这是默认的 sql 内存模型。<br />**LOCK_PAGES** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用锁定内存页来分配内存。 这是默认的 sql 内存管理器，在 SQL Server 启动期间 SQL Server 服务帐户拥有 "锁定内存页" 特权。<br /> **LARGE_PAGES** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在内存中使用较大的页来分配内存。 SQL Server 使用大型页面分配器仅 SQL Server 在服务器启动期间和跟踪标志834打开时，将内存分配给 Enterprise edition。|
|pdw_node_id|**int**|**适用于：** [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分发所在的节点的标识符。|  
|**socket_count** |**int** | **适用于：** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 及更高版本。<br /><br />指定系统上可用的处理器插槽数。 |  
|**cores_per_socket** |**int** | **适用于：** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 及更高版本。<br /><br />指定系统上每个套接字可用的处理器数。 |  
|**numa_node_count** |**int** | **适用于：** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 及更高版本。<br /><br />指定系统上可用的 numa 节点数。 此列包括物理 numa 节点以及软 numa 节点。 |  
  
## <a name="permissions"></a>Permissions

在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上，需要 `VIEW SERVER STATE` 权限。   
在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 高级层上，需要数据库中的 `VIEW DATABASE STATE` 权限。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   

## <a name="see-also"></a>另请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与操作系统相关的动态管理视图&#40;SQL Server transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  



