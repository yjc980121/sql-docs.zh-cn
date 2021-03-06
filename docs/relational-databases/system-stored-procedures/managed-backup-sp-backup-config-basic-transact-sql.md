---
title: managed_backup sp_backup_config_basic （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_basic_TSQL
- sp_backup_config_basic
- managed_backup.sp_backup_config_basic
- managed_backup.sp_backup_config_basic_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_basic
- sp_backup_config_basic
ms.assetid: 3ad73051-ae9a-4e41-a889-166146e5508f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e3b3c547453c41dff6d32d1cafcd62746a2f194f
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305259"
---
# <a name="managed_backupsp_backup_config_basic-transact-sql"></a>managed_backup sp_backup_config_basic （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  为特定数据库或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 基本设置。  
  
> [!NOTE]  
>  可以自行调用此过程来创建基本的托管备份配置。 但是，如果你计划添加高级功能或自定义计划，请先使用 managed_backup 来配置这些设置。在使用此过程启用托管备份之前[ &#40;sp_backup_config_advanced transact-sql&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)和[managed_backup。 sp_backup_config_schedule &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md) 。  
   
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```Transact-SQL   
EXEC managed_backup.sp_backup_config_basic  
    [@enable_backup = ] { 0 | 1}    ,[@database_name = ] 'database_name'    ,[@container_url = ] 'Azure_Storage_blob_container  
    ,[@retention_days = ] 'retention_period_in_days'    ,[@credential_name = ] 'sql_credential_name'  
```  
  
##  <a name="Arguments"></a> 参数  
 @enable_backup  
 启用或禁用指定数据库的 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。 @enable_backup是 **位**。 为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的第一个实例配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 时，必需的参数。 如果要更改现有 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 配置，此参数是可选的。 在这种情况下，未指定的任何配置值都将保留其现有值。  
  
 @database_name  
 用于在特定数据库上启用托管备份的数据库名称。  
  
 @container_url  
 指示备份位置的 URL。 当 @credential_name 为 NULL 时，此 URL 是 Azure 存储中 blob 容器的共享访问签名（SAS） URL，备份使用新的备份来阻止 blob 功能。 有关详细信息，请参阅[了解 SAS](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/)。 指定 @credential_name 时，这是一个存储帐户 URL，备份使用不推荐使用的备份到页 blob 功能。  
  
> [!NOTE]  
>  目前此参数仅支持 SAS URL。  
  
 @retention_days  
 备份文件的保持期（以天为单位）。 @storage_url 是 INT。 这是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上首次配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 时必需的参数。 更改 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 配置时，此参数是可选的。 如果不指定，则会保留现有的配置值。  
  
 @credential_name  
 用于对 Azure 存储帐户进行身份验证的 SQL 凭据的名称。 @credentail_name **SYSNAME**。 指定时，备份将存储到页 blob。 如果此参数为 NULL，则备份将存储为块 blob。 备份到页 blob 已弃用，因此最好使用新的块 blob 备份功能。 当用于更改[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]配置时，此参数是可选参数。 如果未指定，则保留现有的配置值。  
  
> [!WARNING]
>  此时不支持 **\@credential_name**参数。 仅支持备份到块 blob，这需要此参数为 NULL。  
  
## <a name="return-code-value"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>Permissions  
 要求具有**db_backupoperator**数据库角色的成员身份，具有**ALTER ANY CREDENTIAL**权限以及对**sp_delete_backuphistory**存储过程的**EXECUTE**权限。  
  
## <a name="examples"></a>示例  
 可以使用最新的 Azure PowerShell 命令创建存储帐户容器和 SAS URL。 以下示例在 mystorageaccount 存储帐户中创建一个新容器 mycontainer，然后获取具有完全权限的 SAS URL。  
  
```powershell  
$context = New-AzureStorageContext -StorageAccountName mystorageaccount -StorageAccountKey (Get-AzureStorageKey -StorageAccountName mystorageaccount).Primary  
New-AzureStorageContainer -Name mycontainer -Context $context  
New-AzureStorageContainerSASToken -Name mycontainer -Permission rwdl -FullUri -Context $context  
```  
  
 以下示例对在其上执行 SQL Server 的实例启用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]，并将保留策略设置为30天，将目标设置为名为 "mystorageaccount" 的存储帐户中名为 "mycontainer" 的容器。  
  
```Transact-SQL 
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=1  
                ,@container_url = 'https://mystorageaccount.blob.core.windows.net/mycontainer'  
                ,@retention_days=30;   
GO  
  
```
  
 以下示例禁用在所在 SQL Server 实例上执行的[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。  
  
```Transact-SQL  
Use msdb;  
Go  
EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=0;  
GO  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
