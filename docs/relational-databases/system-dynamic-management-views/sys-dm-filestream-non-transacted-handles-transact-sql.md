---
title: sys.dm_filestream_non_transacted_handles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_filestream_non_transacted_handles_TSQL
- dm_filestream_non_transacted_handles
- dm_filestream_non_transacted_handles_TSQL
- sys.dm_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_non_transacted_handles dynamic management view
ms.assetid: 507ec125-67dc-450a-9081-94cde5444a92
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dda607ace977be539dbed096a3d83ac5f220ea0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950984"
---
# <a name="sysdmfilestreamnontransactedhandles-transact-sql"></a>sys.dm_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  显示当前打开的与 FileTable 数据关联的非事务性文件句柄。  
  
 此视图为每个打开的文件句柄都包含一行。 由于此视图中的数据与服务器的实时内部状态相对应，因此该数据会经常随着句柄的打开和关闭而更改。 此视图不包含历史信息。  
  
 有关详细信息，请参阅 [管理 FileTables](../../relational-databases/blob/manage-filetables.md)。  
  
|**列**|**类型**|**说明**|  
|----------------|--------------|---------------------|  
|database_id|INT|与句柄关联的数据库的 ID。|  
|object_id|INT|与句柄关联的 FileTable 的对象 ID。|  
|handle_id|INT|唯一的句柄上下文标识符。 通过使用[sp_kill_filestream_non_transacted_handles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)存储过程来终止特定句柄。|  
|file_object_type|INT|句柄的类型。 此类型指示句柄针对其打开的层次结构的级别，即：数据库或项。|  
|file_object_type_desc|nvarchar(120)|"未定义"<br />"SERVER_ROOT"<br />"DATABASE_ROOT"<br />"TABLE_ROOT"<br />"TABLE_ITEM"|  
|correlation_process_id|varbinary(8)|包含发起请求的进程的唯一标识符。|  
|correlation_thread_id|varbinary(8)|包含发起请求的线程的唯一标识符。|  
|file_context|varbinary(8)|指向此句柄使用的文件对象的指针。|  
|state|INT|句柄的当前状态。 可处于活动、已关闭或已终止状态。|  
|state_desc|nvarchar(120)|"活动"，<br />"已关闭"<br />"终止"|  
|current_workitem_type|INT|此句柄当前正在由哪一状态处理。|  
|current_workitem_type_desc|nvarchar(120)|"NoSetWorkItemType"<br />"FFtPreCreateWorkitem"<br />"FFtGetPhysicalFileNameWorkitem"<br />"FFtPostCreateWorkitem"<br />"FFtPreCleanupWorkitem"<br />"FFtPostCleanupWorkitem"<br />"FFtPreCloseWorkitem"<br />"FFtQueryDirectoryWorkItem"<br />"FFtQueryInfoWorkItem"<br />"FFtQueryVolumeInfoWorkItem"<br />"FFtSetInfoWorkitem"<br />"FFtWriteCompletionWorkitem"|  
|fcb_id|BIGINT|FileTable 文件控制块 ID。|  
|item_id|varbinary(892)|文件或目录的项 ID。 对于服务器根句柄可能为 Null。|  
|is_directory|bit|这是一个目录。|  
|item_name|nvarchar(512)|项的名称。|  
|opened_file_name|nvarchar(512)|最初请求要打开的路径。|  
|database_directory_name|nvarchar(512)|opened_file_name 中表示数据库目录名称的部分。|  
|table_directory_name|nvarchar(512)|opened_file_name 中表示表目录名称的部分。|  
|remaining_file_name|nvarchar(512)|opened_file_name 中表示其余目录名称的部分。|  
|open_time|DATETIME|打开句柄的时间。|  
|flags|INT|ShareFlagsUpdatedToFcb = 0x1、<br />DeleteOnClose = 0x2、<br />NewFile = 0x4、<br />PostCreateDoneForNewFile = 0x8、<br />StreamFileOverwritten = 0x10、<br />RequestCancelled = 0x20、<br />NewFileCreationRolledBack = 0x40|  
|login_id|INT|打开句柄的主体的 ID。|  
|login_name|nvarchar(512)|打开句柄的主体的名称。|  
|login_sid|varbinary(85)|打开句柄的主体的 SID。|  
|read_access|bit|打开以供读取。|  
|write_access|bit|打开以供写入。|  
|delete_access|bit|打开以供删除。|  
|share_read|bit|打开并允许 share_read。|  
|share_write|bit|打开并允许 share_write。|  
|share_delete|bit|打开并允许 share_delete。|  
  
## <a name="see-also"></a>请参阅  
 [管理 FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
