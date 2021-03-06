---
title: sp_add_log_file_recover_suspect_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_file_recover_suspect_db_TSQL
- sp_add_log_file_recover_suspect_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_file_recover_suspect_db
ms.assetid: b41ca3a5-7222-4c22-a012-e66a577a82f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f951aaee96bccf0c2876c781aaebdd2a009b51d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140480"
---
# <a name="spaddlogfilerecoversuspectdb-transact-sql"></a>sp_add_log_file_recover_suspect_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  如果由于数据库上日志空间不足（错误 9002）而造成恢复不能完成，请将日志文件添加到文件组中。 添加文件后， **sp_add_log_file_recover_suspect_db**将关闭可疑设置并完成数据库的恢复。 参数是相同的 ALTER DATABASE *database_name*添加日志文件。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_add_log_file_recover_suspect_db [ @dbName= ] 'database' ,   
    [ @name = ] 'logical_file_name' ,   
    [ @filename= ] 'os_file_name' ,   
    [ @size = ] 'size' ,   
    [ @maxsize = ] 'max_size' ,   
    [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>参数  
`[ @dbName = ] 'database'` 是数据库的名称。 *数据库*是**sysname**，无默认值。  
  
`[ @name = ] 'logical_file_name'` 名称中使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]引用该文件时。 名称在服务器中必须是唯一的。 *logical_file_name*是**nvarchar(260)** ，无默认值。  
  
`[ @filename = ] 'os_file_name'` 是的路径和文件名称用于由操作系统文件。 该文件必须驻留在安装[!INCLUDE[ssDE](../../includes/ssde-md.md)]的服务器上。 *os_file_name*是**nvarchar(260)** ，无默认值。  
  
`[ @size = ] 'size_ '` 是该文件的初始大小。 *大小*是**nvarchar(20)** ，默认值为 NULL。 指定一个整数，不包含小数位。 可以使用 MB 和 KB 后缀指定兆字节或千字节。 默认值为 MB。 最小值为 512 KB。 如果*大小*未指定，默认值为 1 MB。  
  
`[ @maxsize = ] 'max_size_ '` 是该文件可增长到的最大大小。 *max_size*是**nvarchar(20)** ，默认值为 NULL。 指定一个整数，不包含小数位。 可以使用 MB 和 KB 后缀指定兆字节或千字节。 默认值为 MB。  
  
 如果*max_size*未指定，则文件将增长到磁盘变满为止。 当磁盘将满时，[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 应用程序日志会向管理员发出警告。  
  
`[ @filegrowth = ] 'growth_increment_ '` 每次需要新空间时添加到该文件的空间量。 *growth_increment*是**nvarchar(20)** ，默认值为 NULL。 0 值表示不增长。 指定一个整数，不包含小数位。 该值可按 MB、KB 或百分比 (%) 形式指定。 如果指定百分比 (%)，则增量大小为发生增长时文件大小的指定百分比。 如果未在数量后面指定 MB、KB 或 %，则默认值为 MB。  
  
 如果*growth_increment*为 NULL，默认值是 10%，最小值为 64 KB。 指定的大小舍入为最接近的 64 KB 的倍数。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="permissions"></a>权限  
 执行权限默认授予的成员**sysadmin**固定的服务器角色。 这些权限是不可传递的。  
  
## <a name="examples"></a>示例  
 在以下示例中，数据库 `db1` 在恢复期间由于日志空间不足（错误 9002）而标记为可疑。  
  
```  
USE master;  
GO  
EXEC sp_add_log_file_recover_suspect_db db1, logfile2,  
'C:\Program Files\Microsoft SQL  
    Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_logfile2.ldf',   
    '1MB';  
```  
  
## <a name="see-also"></a>请参阅  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_data_file_recover_suspect_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-data-file-recover-suspect-db-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
