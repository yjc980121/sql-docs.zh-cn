---
title: sp_can_tlog_be_applied (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_can_tlog_be_applied_TSQL
- sp_can_tlog_be_applied
dev_langs:
- TSQL
helpviewer_keywords:
- sp_can_tlog_be_applied
ms.assetid: 9c143b6c-27ac-4ab7-98d1-3b7b265f3963
author: stevestein
ms.author: sstein
ms.openlocfilehash: 279492503ba8ce31e3c5d4027d8fd184c4a81587
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045957"
---
# <a name="spcantlogbeapplied-transact-sql"></a>sp_can_tlog_be_applied (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  验证事务日志备份是否可应用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。 **sp_can_tlog_be_applied**要求数据库处于 Restoring 状态。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_can_tlog_be_applied [ @backup_file_name = ] 'backup_file_name'   
        , [ @database_name = ] 'database_name'   
        , [ @result = ] result OUTPUT  
```  
  
## <a name="arguments"></a>参数  
`[ @backup_file_name = ] 'backup_file_name'` 是备份文件的名称。 *backup_file_name*是**nvarchar （128)** 。  
  
`[ @database_name = ] 'database_name'` 是数据库的名称。 database_name 的数据类型为 sysname   。  
  
`[ @result = ] _result_ OUTPUT` 指示是否可以对数据库应用事务日志。 *结果*是**位**。  
  
 1 = 日志可以应用  
  
 0= 日志不能应用。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="permissions"></a>权限  
 只有的成员**sysadmin**固定的服务器角色可以执行**sp_can_tlog_be_applied**。  
  
## <a name="examples"></a>示例  
 以下示例将声明一个本地变量 `@MyBitVar`，用于存储结果。  
  
```  
USE master;  
GO  
DECLARE @MyBitVar BIT;  
EXEC sp_can_tlog_be_applied  
     @backup_file_name =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\AdventureWorks2012.bak',  
     @database_name = N'AdventureWorks2012',  
     @result = @MyBitVar OUTPUT;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
