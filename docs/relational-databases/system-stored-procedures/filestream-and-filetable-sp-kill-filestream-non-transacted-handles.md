---
title: sp_kill_filestream_non_transacted_handles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98c986c26c8d0d0cc6e2b8ff3573f0a20d938975
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942262"
---
# <a name="spkillfilestreamnontransactedhandles-transact-sql"></a>sp_kill_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  关闭 FileTable 数据的非事务性文件句柄。  
  
## <a name="syntax"></a>语法  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] 'table_name', [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>参数  
 *table_name*  
 要关闭其中的非事务性句柄的表的名称。  
  
 可以将传递*table_name*而无需*handle_id*以关闭所有打开的非事务性句柄为 FileTable。  
  
 可以将 NULL 传递的值*table_name*以关闭所有打开的非事务性句柄当前数据库中的所有 Filetable 的。 NULL 是默认值。  
  
 *handle_id*  
 要关闭的各个句柄的可选 ID。 可以获取*handle_id*从[sys.dm_filestream_non_transacted_handles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)动态管理视图。 每个 ID 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中都是唯一的。 如果指定*handle_id*，则还必须提供的值*table_name*。  
  
 可以将 NULL 传递的值*handle_id*以关闭所有打开的非事务性句柄由指定的 filetable *table_name*。 NULL 是默认值。  
  
## <a name="return-code-value"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="result-set"></a>结果集  
 无。  
  
## <a name="general-remarks"></a>一般备注  
 *Handle_id*按照要求**sp_kill_filestream_non_transacted_handles** session_id 或使用其他的工作单元无关**终止**命令。  
  
 有关详细信息，请参阅 [管理 FileTables](../../relational-databases/blob/manage-filetables.md)。  
  
## <a name="metadata"></a>元数据  
 有关打开的非事务性文件句柄的信息，请查询动态管理视图[sys.dm_filestream_non_transacted_handles &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)。  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>权限  
 您必须具有**VIEW DATABASE STATE**权限，以获取文件句柄从**sys.dm_FILESTREAM_non_transacted_handles**动态管理视图和运行**sp_kill_filestream_non_transacted_handles**。  
  
## <a name="examples"></a>示例  
 下面的示例说明如何调用**sp_kill_filestream_non_transacted_handles**以关闭 FileTable 数据的非事务性文件句柄。  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable'  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable', @handle_id = 0xFFFAAADD  
```  
  
 下面的示例演示如何使用脚本来获取*handle_id*并将其关闭。  
  
```sql  
DECLARE @handle_id varbinary(16);  
DECLARE @table_name sysname;  
  
SELECT TOP 1 @handle_id = handle_id, @table_name = Object_name(table_id)  
FROM sys.dm_FILESTREAM_non_transacted_handles;  
  
EXEC sp_kill_filestream_non_transacted_handles @dbname, @table_name, @handle_id;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [管理 FileTable](../../relational-databases/blob/manage-filetables.md)  
 [Filestream 和 FileTable 动态管理视图 (Transact SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
 <br>[Filestream 和 FileTable 目录视图 (Transact SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
 <br>[sp_filestream_force_garbage_collection (TRANSACT-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
