---
title: sys.sp_cdc_add_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_add_job_TSQL
- sys.sp_cdc_add_job
- sys.sp_cdc_add_job_TSQL
- sp_cdc_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_add_job
ms.assetid: c4458738-ed25-40a6-8294-a26ca5a05bd9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7dd10d28855cc4c10f5496c74f1f39a91826052f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106538"
---
# <a name="sysspcdcaddjob-transact-sql"></a>sys.sp_cdc_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在当前数据库中创建变更数据捕获清理或捕获作业。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sys.sp_cdc_add_job [ @job_type = ] 'job_type'  
    [ , [ @start_job = ] start_job ]   
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ , [ @threshold ] = 'delete_threshold' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @job_type = ] 'job\_type'` 要添加的作业的类型。 *job_type*是**nvarchar(20)** 且不能为 NULL。 有效输入包括 **'capture'** 并 **'cleanup'** 。  
  
`[ @start_job = ] start_job` 标志，指示是否应添加后立即启动作业。 *start_job*是**位**默认值为 1。  
  
`[ @maxtrans ] = max_trans` 事务中每个扫描循环要处理的最大数目。 *max_trans*是**int**默认值为 500。 如果指定值，则该值必须是一个正整数。  
  
 *max_trans*仅对捕获作业有效。  
  
`[ @maxscans ] = max\_scans_` 最大扫描循环要执行，以从日志提取所有行数。 *max_scans*是**int**默认值为 10。  
  
 *max_scan*仅对捕获作业有效。  
  
`[ @continuous ] = continuous_` 指示捕获作业是连续运行 (1)，或仅运行一次 (0)。 *持续*是**位**默认值为 1。  
  
 当*连续*= 1， [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md)作业将扫描日志并且最多可处理 (*max_trans* \* *max_scans*)事务。 然后，在等待中指定的秒数*polling_interval*开始下一次日志扫描之前。  
  
 当*连续*= 0， **sp_cdc_scan**最多执行作业*max_scans*扫描日志，最多处理*max_trans*事务在每个扫描以及然后退出。  
  
 *连续*仅对捕获作业有效。  
  
`[ @pollinginterval ] = polling\_interval_` 日志扫描循环之间相隔的秒数。 *polling_interval*是**bigint**默认值为 5。  
  
 *polling_interval*仅对捕获的有效作业*连续*设置为 1。 如果指定了此参数，则该值不能负数，且不能超过 24 小时。 如果指定的值为 0，则不会在两次日志扫描之间等待。  
  
`[ @retention ] = retention_` 更改表的更改的数据行中保留的分钟数。 *保留期*是**bigint**默认值为 4320 （72 小时）。 最大值为 52494800（100 年）。 如果指定值，则该值必须是一个正整数。  
  
 *保留期*仅对清除作业有效。  
  
`[ @threshold = ] 'delete\_threshold'` 可以通过清除上一条语句删除的删除项的最大数目。 *delete_threshold*是**bigint**默认值为 5000。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="remarks"></a>备注  
 当对数据库中的第一个表启用了变更数据捕获时，会使用默认值创建一个清理作业。 当对数据库中的第一个表启用了变更数据捕获并且该数据库不存在事务发布时，会使用默认值创建一个捕获作业。 如果存在事务发布，则可使用事务日志读取器来驱动捕获机制，此时既不需要也不允许独立的捕获作业。  
  
 因为清理和捕获作业是默认创建的，所以仅当显式删除某个作业并且必须重新创建它时才需要使用此存储过程。  
  
 作业的名称是**cdc。** _\<数据库\_名称\>_ **\_清理**或**cdc。** _\<数据库\_名称\>_ **\_捕获**，其中 *< 数据库名称 >* 名称当前数据库中。 如果已存在具有相同名称的作业，名称追加一个句点 ( **。** ) 跟的唯一标识符，例如： **cdc。AdventureWorks_capture。A1ACBDED-13FC-428C-8302-10100EF74F52**。  
  
 若要查看清除或捕获作业的当前配置，请使用[sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)。 若要更改作业的配置，请使用[sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)。  
  
## <a name="permissions"></a>权限  
 要求的成员身份**db_owner**固定的数据库角色。  
  
## <a name="examples"></a>示例  
  
### <a name="a-creating-a-capture-job"></a>A. 创建捕获作业  
 下例创建一个捕获作业。 本例假定已显式删除了现有清理作业并且必须重新创建它。 创建该作业时使用了默认值。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job @job_type = N'capture';  
GO  
```  
  
### <a name="b-creating-a-cleanup-job"></a>B. 创建清理作业  
 下例在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中创建一个清理作业。 参数 `@start_job` 设置为 0，`@retention` 设置为 5760 分钟（96 小时）。 本例假定已显式删除了现有清理作业并且必须重新创建它。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job  
     @job_type = N'cleanup'  
    ,@start_job = 0  
    ,@retention = 5760;  
```  
  
## <a name="see-also"></a>请参阅  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [关于变更数据捕获 (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
