---
title: sp_helpqreader_agent (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea01bd3eb765a0a5f7a85245090b79579f347b3a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771424"
---
# <a name="sphelpqreaderagent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  返回队列读取器代理的属性。 此存储过程在分发服务器的分发数据库或发布服务器的任意数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>参数  
`[ @frompublisher = ] frompublisher`指定是在发布服务器还是分发服务器上调用该存储过程。 *frompublisher*的值为 bit, 默认值为0。 **1**表示从发布服务器调用该存储过程, **0**表示从分发服务器调用该存储过程。  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**id**|**int**|代理的 ID。|  
|**name**|**nvarchar(100)**|代理的名称。|  
|**job_id**|**uniqueidentifier**|代理作业的唯一 ID。|  
|**job_login**|**nvarchar(512)**|用于运行分发代理的 Windows 帐户, 以*域*\\*用户名*的格式返回。|  
|**job_password**|**sysname**|出于安全原因，值为 **\*\*\*\*\*\*\*\*\*\*** 始终返回。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** (成功) 或**1** (失败)  
  
## <a name="remarks"></a>备注  
 **sp_helpqreader_agent**用于事务复制。  
  
## <a name="permissions"></a>权限  
 当*frompublisher*的值为**1**时, 只有发布服务器上的**sysadmin**固定服务器角色的成员或发布数据库上的**db_owner**固定数据库角色的成员才能执行**sp_helpqreader_agent**。 否则, 只有分发服务器上**sysadmin**固定服务器角色的成员或分发数据库上的**db_owner**固定数据库角色的成员才能执行**sp_helpqreader_agent**。  
  
## <a name="see-also"></a>请参阅  
 [允许更新事务发布的订阅](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
