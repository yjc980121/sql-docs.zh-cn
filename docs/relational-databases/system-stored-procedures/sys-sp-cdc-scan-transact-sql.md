---
title: sys.sp_cdc_scan (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
author: rothja
ms.author: jroth
ms.openlocfilehash: a064b49df3f45d9cbc4b148b8d78c3661f9a2bcc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066728"
---
# <a name="sysspcdcscan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  执行变更数据捕获日志扫描操作。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>参数  
`[ @maxtrans = ] max_trans` 事务中每个扫描循环要处理的最大数目。 *max_trans*是**int**默认值为 500。  
  
`[ @maxscans = ] max_scans` 最大扫描循环要执行，以从日志提取所有行数。 *max_scans*是**int**默认值为 10。  
  
`[ @continuous = ] continuous` 指示存储的过程是否应结束之后执行一次扫描循环 (0) 或连续运行，暂停指定的时间*polling_interval*继续重新执行扫描循环 (1)。 *持续*是**tinyint**默认值为 0。  
  
`[ @pollinginterval = ] polling_interval` 日志扫描循环之间相隔的秒数。 *polling_interval*是**bigint**默认值为 0。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="result-sets"></a>结果集  
 None  
  
## <a name="remarks"></a>备注  
 如果变更数据捕获正在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理捕获作业，则 sys.sp_MScdc_capture_job 将内部调用 sys.sp_cdc_scan。 如果变更数据捕获日志扫描操作已经处于活动状态，或数据库启用了事务复制，则无法显式执行此过程。 此存储过程应当由需要自定义自动配置的捕获作业的行为的管理员使用。  
  
## <a name="permissions"></a>权限  
 要求具有 db_owner 固定数据库角色中的成员资格。  
  
## <a name="see-also"></a>请参阅  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
