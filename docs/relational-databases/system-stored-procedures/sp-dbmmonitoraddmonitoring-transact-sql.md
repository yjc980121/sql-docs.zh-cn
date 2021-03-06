---
title: sp_dbmmonitoraddmonitoring (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitoraddmonitoring
- sp_dbmmonitoraddmonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitoraddmonitoring
ms.assetid: 9489dc30-af29-4363-a172-4645947fc95e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ed53c6a72b201129cf9f75214261bbdd47d6fb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108149"
---
# <a name="spdbmmonitoraddmonitoring-transact-sql"></a>sp_dbmmonitoraddmonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  创建数据库镜像监视器作业，该作业可定期更新服务器实例上每个镜像数据库的镜像状态。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_dbmmonitoraddmonitoring [ update_period ]  
```  
  
## <a name="arguments"></a>参数  
 *update_period*  
 指定更新间隔（分钟）。 此值可以是介于 1 到 120 分钟之间的值。 默认值为 1 分钟。  
  
> [!NOTE]  
>  如果将更新持续时间设置得太低，客户端的响应时间可能会增加。  
  
## <a name="return-code-values"></a>返回代码值  
 无  
  
## <a name="result-sets"></a>结果集  
 None  
  
## <a name="remarks"></a>备注  
 此过程要求允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在服务器实例上运行，为了运行数据库镜像监视器作业，必须运行该代理。  
  
 如果从启动数据库镜像，并且[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，则**sp_dbmmonitoraddmonitoring**过程自动运行。 如果在开始镜像手动使用 ALTER DATABASE 语句，来监视镜像的数据库的服务器实例上，则必须运行**sp_dbmmonitoraddmonitoring**手动。  
  
> [!NOTE]  
>  如果在运行**sp_dbmmonitoraddmonitoring**设置数据库镜像之前，请监视作业将运行，但不是会更新状态表中的数据库镜像监视器历史记录存储。  
  
## <a name="permissions"></a>权限  
 要求具有 **sysadmin** 固定服务器角色的成员身份。  
  
## <a name="examples"></a>示例  
 以下示例将以 `3` 分钟为更新持续时间来启动监视。  
  
```  
EXEC sp_dbmmonitoraddmonitoring 3;  
```  
  
## <a name="see-also"></a>请参阅  
 [监视数据库镜像 (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
