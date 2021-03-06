---
title: log_shipping_primary_databases （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_primary_databases
- log_shipping_primary_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_primary_databases system table
ms.assetid: 56888756-a798-42be-9b5e-0f9aa05a2cc6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9c1dfefbc309e9ccc0f170461795c00a117247e2
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304983"
---
# <a name="log_shipping_primary_databases-transact-sql"></a>log_shipping_primary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在日志传送配置中为主数据库存储一条记录。 该表存储在**msdb**数据库中。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**primary_id**|**ssNoversion**|日志传送配置的主数据库 ID。|  
|**primary_database**|**sysname**|日志传送配置中主数据库的名称。|  
|**backup_directory**|**nvarchar(500)**|存储主服务器的事务日志备份文件的目录。|  
|**backup_share**|**nvarchar(500)**|备份目录的网络或 UNC 路径。|  
|**backup_retention_period**|**int**|日志备份文件在删除之前保留在备份目录中的时间长度（分钟）。|  
|**backup_job_id**|**ssNoversion**|与主服务器上的备份作业关联的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业 ID。|  
|**monitor_server**|**sysname**|在日志传送配置中用作监视服务器的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 实例的名称 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。|  
|**monitor_server_security_mode**|**bit**|用于连接到监视服务器的安全模式。<br /><br /> 1 = Windows 身份验证。<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。|  
|**last_backup_file**|**nvarchar(500)**|最近一次事务日志备份的绝对路径。|  
|**last_backup_date**|**datetime**|上一次日志备份操作的时间和日期。|  
|**user_specified_monitor**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> **sp_help_log_shipping_primary_database**和**sp_help_log_shipping_secondary_primary**使用此列控制 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的监视器设置的显示。<br /><br /> 0 = 调用这两个存储过程中的任意一个时，用户未指定 **\@monitor_server**参数的显式值。<br /><br /> 1 = 用户指定一个显式值。|  
|**backup_compression**|**tinyint**|指示日志传送配置是否覆盖服务器级的备份压缩行为。<br /><br /> 0 = 禁用。 永远不压缩日志备份，不管服务器配置的备份压缩设置是什么。<br /><br /> 1 = 已启用。 始终压缩日志备份，不管服务器配置的备份压缩设置是什么。<br /><br /> 2 = 使用视图的服务器配置，[或配置备份压缩默认服务器配置选项](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)服务器-配置选项。 这是默认值。<br /><br /> 仅在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Enterprise 版本中支持备份压缩。|  
  
## <a name="see-also"></a>另请参阅  
 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_help_log_shipping_primary_database (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql.md)   
 [系统表 (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
