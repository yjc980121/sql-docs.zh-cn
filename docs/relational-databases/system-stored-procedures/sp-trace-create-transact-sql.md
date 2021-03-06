---
title: sp_trace_create (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_create_TSQL
- sp_trace_create
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_create
ms.assetid: f3a43597-4c5a-4520-bcab-becdbbf81d2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d698932bb7ef7e0fd37a0ced8ab536eeb0d5d68
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096034"
---
# <a name="sptracecreate-transact-sql"></a>sp_trace_create (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  创建跟踪定义。 新的跟踪将处于停止状态。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 请改用扩展事件。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_trace_create [ @traceid = ] trace_id OUTPUT   
          , [ @options = ] option_value   
          , [ @tracefile = ] 'trace_file'   
     [ , [ @maxfilesize = ] max_file_size ]  
     [ , [ @stoptime = ] 'stop_time' ]  
     [ , [ @filecount = ] 'max_rollover_files' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @traceid = ] trace_id` 是分配的编号[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]于新的跟踪。 用户提供的任何输入都被忽略。 *trace_id*是**int**，默认值为 NULL。 用户使用*trace_id*值来标识、 修改和控制此存储过程定义的跟踪。  
  
`[ @options = ] option_value` 指定为跟踪设置的选项。 *option_value*是**int**，无默认值。 用户可以通过指定所选出选项之和来选择这些选项的组合。 例如，若要启用这两个选项 TRACE_FILE_ROLLOVER 和 SHUTDOWN_ON_ERROR，指定**6**有关*option_value*。  
  
 下表列出了选项、说明和选项值。  
  
|选项名|选项值|描述|  
|-----------------|------------------|-----------------|  
|TRACE_FILE_ROLLOVER|**2**|指定当*max_file_size*达到当前跟踪文件已关闭，并且创建一个新文件。 所有新记录都将写入新文件。 新文件将与前一个文件同名，但是在文件名后将附加一个整数以指示其序列。 例如，如果命名原始跟踪文件为 filename.trc，则命名下个跟踪文件为 filename_1.trc，命名再下一个跟踪文件为 filename_2.trc，等等。<br /><br /> 随着更多滚动更新跟踪文件的创建，附加到文件名的整数值继续增加。<br /><br /> SQL Server 使用的默认值*max_file_size* (5 MB) 如果此选项指定但未指定的值*max_file_size*。|  
|SHUTDOWN_ON_ERROR|**4**|指定无论任何原因，如果不能将跟踪写入文件，则 SQL Server 将关闭。 执行安全审核跟踪时，该选项很有用。|  
|TRACE_PRODUCE_BLACKBOX|**8**|指定服务器产生的最后 5 MB 跟踪信息记录将由服务器保存。 TRACE_PRODUCE_BLACKBOX 与所有其他选项不兼容。|  
  
`[ @tracefile = ] 'trace_file'` 指定的位置和跟踪将写入的文件名称。 *trace_file*是**nvarchar(245)** ，无默认值。 *trace_file*可以是本地目录 （如 N 'C:\MSSQL\Trace\trace.trc') 或共享或路径的 UNC (N'\\\\*Servername*\\*Sharename*\\ *Directory*\trace.trc')。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将追加 **.trc**扩展到所有跟踪文件的名称。 如果 TRACE_FILE_ROLLOVER 选项和一个*max_file_size*指定，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]创建新的跟踪文件，当原始跟踪文件达到其最大大小。 新的文件具有与原始文件，但 _ 同名*n*追加到表示从其序列**1**。 例如，如果第一个跟踪文件命名为**filename.trc**，第二个跟踪文件命名为**filename_1.trc**。  
  
 如果您使用 TRACE_FILE_ROLLOVER 选项，我们建议您在原始跟踪文件名中不要使用下划线字符。 如果您使用了下划线，则会发生以下行为：  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 不自动加载或者提示您加载滚动更新文件 （如果配置的任一文件滚动更新选项）。  
  
-   Fn_trace_gettable 函数不会加载滚动更新文件 (当指定为通过使用*number_files*参数) 的原始文件名称使用下划线和数字值的结束位置。 （这不适用于在文件滚动更新时自动追加的下划线和数字。）  
  
> [!NOTE]  
>  作为对这两个行为的解决方法，您可以重命名这些文件以便删除原始文件名中的下划线。 例如，如果原始文件被命名为**my_trace.trc**，并滚动更新文件名为**my_trace_1.trc**，您可以重命名的文件**mytrace.trc**和**mytrace_1.trc**打开中的文件之前[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]。  
  
 *trace_file*不能使用 TRACE_PRODUCE_BLACKBOX 选项时指定。  
  
`[ @maxfilesize = ] max_file_size` 指定的最大大小以兆字节 (MB) 的跟踪文件可以增长。 *max_file_size*是**bigint**，默认值为**5**。  
  
 如果不使用 TRACE_FILE_ROLLOVER 选项指定此参数，则跟踪将停止对文件的记录时使用的磁盘空间超过了指定的量*max_file_size*。  
  
`[ @stoptime = ] 'stop_time'` 指定的日期和时间跟踪将停止。 *stop_time*是**datetime**，默认值为 NULL。 如果为 NULL，该跟踪将一直运行，直到它被手动停止或服务器关闭。  
  
 如果这两个*stop_time*和*max_file_size*指定，并且 TRACE_FILE_ROLLOVER 不指定，则跟踪将时达到指定的停止时间或最大文件大小。 如果*stop_time*， *max_file_size*，并指定 TRACE_FILE_ROLLOVER，跟踪假设跟踪未填满驱动器在指定的停止时间停止。  
  
`[ @filecount = ] 'max_rollover_files'` 指定要使用同一基准文件名维护的最大数目或跟踪文件。 *max_rollover_files*是**int**，大于 1。 此参数仅在指定了 TRACE_FILE_ROLLOVER 选项时有效。 时*max_rollover_files*指定，则[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]尝试维护不超过*max_rollover_files*通过打开新的跟踪文件前删除最旧的跟踪文件来跟踪文件。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过向基准文件名追加数字来跟踪跟踪文件的新旧程度。  
  
 例如，当*trace_file*参数指定为"c:\mytrace"具有名为"c:\mytrace_123.trc"的文件是早于具有名称"c:\mytrace_124.trc"的文件。 如果*max_rollover_files*为设置为 2，则 SQL Server 中删除文件"c:\mytrace_123.trc"创建跟踪文件"c:\mytrace_125.trc"前。  
  
 请注意，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一次仅尝试删除一个文件，且不能删除另一进程正在使用的文件。 因此，如果在跟踪运行时另一应用程序正在使用跟踪文件，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会将这些跟踪文件保留在文件系统中。  
  
## <a name="return-code-values"></a>返回代码值  
 下表说明在存储过程完成后用户可能获得的代码值。  
  
|返回代码|描述|  
|-----------------|-----------------|  
|0|没有错误。|  
|1|未知错误。|  
|10|无效选项。 指定的选项不兼容时返回此代码。|  
|12|文件未创建。|  
|13|内存不足。 在没有足够内存执行指定的操作时返回此代码。|  
|14|无效停止时间。 在指定的停止时间已发生时返回此代码。|  
|15|参数无效。 在用户已提供不兼容的参数时返回此代码。|  
  
## <a name="remarks"></a>备注  
 **sp_trace_create**是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存储过程，它执行以前执行的操作的许多**xp_trace_\*** 扩展存储的过程的 SQL Server 的早期版本中提供。 使用**sp_trace_create**而不是：  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_setqueuecreateinfo**  
  
-   **xp_trace_setqueuedestination**  
  
 **sp_trace_create**仅创建跟踪定义。 该存储过程不能用于启动或更改跟踪。  
  
 参数的所有 SQL 跟踪存储过程 (**sp_trace_xx**) 已严格类型化。 如果没有用正确的输入参数数据类型（参数说明中指定的类型）来调用这些参数，则存储过程将返回错误。  
  
 有关**sp_trace_create**，则[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]服务帐户必须具有写入权限的跟踪文件文件夹。 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户不是跟踪文件所在计算机上的管理员，则必须将写入权限显式授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户。  
  
> [!NOTE]  
>  使用创建的跟踪文件可以自动进行负载**sp_trace_create**到表中使用**fn_trace_gettable**系统函数。 有关如何使用此系统函数的信息，请参阅[sys.fn_trace_gettable &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)。  
  
 有关使用跟踪存储过程的示例，请参阅[创建跟踪 (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)。  
  
 **TRACE_PRODUCE_BLACKBOX**具有以下特征：  
  
-   它属于滚动更新跟踪。 默认值*file_count*为 2，但可以由用户使用重写*filecount*选项。  
  
-   默认值*file_size*如与其他跟踪为 5 MB 并且可以更改。  
  
-   不能指定文件名。 该文件将另存为：**N'%SQLDIR%\MSSQL\DATA\blackbox.trc'**  
  
-   跟踪中仅包含以下事件和它们的列：  
  
    -   **RPC 正在启动**  
  
    -   **正在启动的批处理**  
  
    -   **Exception**  
  
    -   **注意**  
  
-   无法在此跟踪中添加或删除事件或列。  
  
-   不能为此跟踪指定筛选器。  
  
## <a name="permissions"></a>权限  
 用户必须拥有 ALTER TRACE 权限。  
  
## <a name="see-also"></a>请参阅  
 [sp_trace_generateevent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [SQL 跟踪](../../relational-databases/sql-trace/sql-trace.md)  
  
  
