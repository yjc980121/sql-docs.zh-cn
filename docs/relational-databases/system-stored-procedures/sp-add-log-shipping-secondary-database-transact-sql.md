---
title: sp_add_log_shipping_secondary_database (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_database
- sp_add_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_database
ms.assetid: d29e1c24-3a3c-47a4-a726-4584afa6038a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e26fa9b22578d91636eb554c75a55f184869d529
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046210"
---
# <a name="spaddlogshippingsecondarydatabase-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  为日志传送设置辅助数据库。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_add_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>参数  
`[ @secondary_database = ] 'secondary_database'` 为辅助数据库的名称。 *secondary_database*是**sysname**，无默认值。  
  
`[ @primary_server = ] 'primary_server'` 主实例的名称[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]日志传送配置中。 *primary_server*是**sysname**且不能为 NULL。  
  
`[ @primary_database = ] 'primary_database'` 是主服务器上的名称。 *primary_database*是**sysname**，无默认值。  
  
`[ @restore_delay = ] 'restore_delay'` 在辅助服务器还原给定备份文件之前等待的分钟的时间量。 *restore_delay*是**int**且不能为 NULL。 默认值为 0。  
  
`[ @restore_all = ] 'restore_all'` 如果设置为 1，辅助服务器还原所有可用的事务日志备份还原作业运行时。 否则，辅助服务器将在还原一个文件后停止。 *restore_all*是**位**且不能为 NULL。  
  
`[ @restore_mode = ] 'restore_mode'` 辅助数据库的还原模式。  
  
 0 = 使用 NORECOVERY 还原日志。  
  
 1 = 使用 STANDBY 还原日志。  
  
 *还原*是**位**且不能为 NULL。  
  
`[ @disconnect_users = ] 'disconnect_users'` 如果设置为 1，用户断开连接从辅助数据库执行还原操作时。 默认值 = 0。 *断开*用户是**位**且不能为 NULL。  
  
`[ @block_size = ] 'block_size'` 大小 （字节），用作备份设备的块大小。 *block_size*是**int**与默认值为-1。  
  
`[ @buffer_count = ] 'buffer_count'` 使用备份或还原操作的缓冲区的总数。 *buffer_count*是**int**与默认值为-1。  
  
`[ @max_transfer_size = ] 'max_transfer_size'` 大小，以字节为单位的最大输入或输出请求发出[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]向备份设备。 *max_transfersize*是**int** ，可以为 NULL。  
  
`[ @restore_threshold = ] 'restore_threshold'` 之间允许等待的分钟数还原操作，就会生成警报。 *restore_threshold*是**int**且不能为 NULL。  
  
`[ @threshold_alert = ] 'threshold_alert'` 是要超过备份阈值时引发的警报。 *threshold_alert*是**int**，默认值为 14,420。  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` 指定是否引发警报时*backup_threshold*超出。 默认值一 (1) 表示要引发警告。 *threshold_alert_enabled*是**位**。  
  
`[ @history_retention_period = ] 'history_retention_period'` 是以分钟为单位历史记录保留在其中长度。 *history_retention_period*是**int**，默认值为 NULL。 如果不指定值，则使用值 14420。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
 None  
  
## <a name="remarks"></a>备注  
 **sp_add_log_shipping_secondary_database**必须从运行**主**辅助服务器上的数据库。 此存储过程执行以下操作：  
  
1.  **sp_add_log_shipping_secondary_primary**主日志传送辅助服务器上的数据库信息进行初始化，该存储过程之前，应调用。  
  
2.  添加辅助数据库中的条目**log_shipping_secondary_databases**使用所提供的参数。  
  
3.  添加本地监视记录在**log_shipping_monitor_secondary**辅助服务器上使用提供的参数。  
  
4.  如果监视服务器不同于辅助服务器时，监视器中添加记录**log_shipping_monitor_secondary**监视器服务器使用提供的参数。  
  
## <a name="permissions"></a>权限  
 只有的成员**sysadmin**固定的服务器角色可以运行此过程。  
  
## <a name="examples"></a>示例  
 此示例演示如何使用**sp_add_log_shipping_secondary_database**存储过程来将数据库添加**LogShipAdventureWorks**日志传送配置中的辅助数据库与主数据库[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]位于主服务器 tribeca 中时。  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_database   
@secondary_database = N'LogShipAdventureWorks'   
,@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks2012'   
,@restore_delay = 0   
,@restore_mode = 1   
,@disconnect_users = 0   
,@restore_threshold = 45     
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440 ;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
