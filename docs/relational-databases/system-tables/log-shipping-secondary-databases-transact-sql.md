---
title: log_shipping_secondary_databases (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary_databases_TSQL
- log_shipping_secondary_databases
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary_databases system table
ms.assetid: ba2374af-86b8-480c-a10c-51e7c4e3ae23
author: stevestein
ms.author: sstein
ms.openlocfilehash: ad6d61f4267e30c6c0b3f6cede9085cad5d39006
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68095777"
---
# <a name="logshippingsecondarydatabases-transact-sql"></a>log_shipping_secondary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在日志传送配置中为每个辅助数据库存储一条记录。 此表存储中**msdb**数据库。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**secondary_database**|**sysname**|日志传送配置中辅助数据库的名称。|  
|**secondary_id**|**uniqueidentifier**|日志传送配置中辅助服务器的 ID。|  
|**restore_delay**|**int**|时间，以分钟为单位的辅助服务器还原给定备份文件之前要等待的量。 默认为 0 分钟。|  
|**restore_all**|**bit**|如果设置为 1，则辅助服务器将在还原作业运行时还原所有可用的事务日志备份。 否则，在原还了一个文件之后它将停止。|  
|**restore_mode**|**bit**|辅助数据库的还原模式。<br /><br /> 0 = 使用 NORECOVERY 还原日志。<br /><br /> 1 = 使用 STANDBY 还原日志。|  
|**disconnect_users**|**bit**|如果设置为 1，则当执行还原操作时，将断开用户与辅助数据库的连接。 默认值 = 0。|  
|**block_size**|**int**|用作备份设备的块大小（字节）。|  
|**buffer_count**|**int**|备份或还原操作使用的缓冲区总数。|  
|**max_transfer_size**|**int**|大小，以字节为单位的最大输入或输出请求由颁发[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]向备份设备。|  
|**last_restored_file**|**nvarchar(500)**|上次还原到辅助数据库的备份文件的文件名。|  
|**last_restored_date**|**datetime**|上次对辅助数据库执行还原操作的时间和日期。|  
  
## <a name="see-also"></a>请参阅  
 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [log_shipping_secondary (Transact-SQL)](../../relational-databases/system-tables/log-shipping-secondary-transact-sql.md)   
 [系统表 (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
