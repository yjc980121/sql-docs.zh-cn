---
title: sp_replmonitorhelpmergesession (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1781e22e97870e7b9c26e7de397d77600ecbe1ce
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771240"
---
# <a name="spreplmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  返回给定复制合并代理的以前会话的信息，并为每个符合筛选条件的会话返回一行。 此用于监视合并复制的存储过程在分发服务器的分发数据库上执行，或在订阅服务器的订阅数据库上执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_replmonitorhelpmergesession [ [ @agent_name = ] 'agent_name' ]  
    [ , [ @hours = ] hours ]  
    [ , [ @session_type = ] session_type ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]   
```  
  
## <a name="arguments"></a>参数  
`[ @agent_name = ] 'agent_name'`代理的名称。 *agent_name*的值为**nvarchar (100)** , 无默认值。  
  
`[ @hours = ] hours`返回历史代理会话信息的时间范围 (以小时为单位)。 *小时数*为**int**, 可以是下列范围之一。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|< **0**|返回代理过去运行的信息，最多返回 100 条运行信息。|  
|**0** （默认值）|返回代理过去运行的所有信息。|  
|> **0**|返回在过去几*小时*内发生的代理运行的信息。|  
  
`[ @session_type = ] session_type`根据会话最终结果筛选结果集。 *session_type*的数据值为**int**, 可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**1** （默认值）|具有重试或成功结果的代理会话。|  
|**0**|具有失败结果的代理会话。|  
  
`[ @publisher = ] 'publisher'`发布服务器的名称。 *发布服务器*的**sysname**, 默认值为 NULL。 在订阅服务器上执行**sp_replmonitorhelpmergesession**时使用此参数。  
  
`[ @publisher_db = ] 'publisher_db'`发布数据库的名称。 *publisher_db*的值为**sysname**, 默认值为 NULL。 在订阅服务器上执行**sp_replmonitorhelpmergesession**时使用此参数。  
  
`[ @publication = ] 'publication'`发布的名称。 *发布*为**sysname**, 默认值为 NULL。 在订阅服务器上执行**sp_replmonitorhelpmergesession**时使用此参数。  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|代理作业会话的 ID。|  
|**“状态”**|**int**|代理运行状态：<br /><br /> **1** = 启动<br /><br /> **2** = 成功<br /><br /> **3** = 正在进行<br /><br /> **4** = 空闲<br /><br /> **5** = 重试<br /><br /> **6** = 失败|  
|**StartTime**|**datetime**|时间代理作业会话开始。|  
|**EndTime**|**datetime**|时间代理作业会话已完成。|  
|**Duration**|**int**|此作业会话的累计时间（以秒为单位）。|  
|**UploadedCommands**|**int**|在代理会话过程中上载的命令的数目。|  
|**DownloadedCommands**|**int**|在代理会话过程中下载的命令的数目。|  
|**ErrorMessages**|**int**|在代理会话过程中生成的错误消息的数目。|  
|**ErrorID**|**int**|发生的错误的 ID。|  
|**PercentageDone**|**decimal**|已经在活动会话中传递的全部更改的估计百分比。|  
|**TimeRemaining**|**int**|估计的活动会话所剩秒数。|  
|**CurrentPhase**|**int**|活动会话的当前阶段，可以是以下内容之一。<br /><br /> **1** = 上载<br /><br /> **2** = 下载|  
|**LastMessage**|**nvarchar(500)**|合并代理在会话过程中记录的最后一个消息。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** (成功) 或**1** (失败)  
  
## <a name="remarks"></a>备注  
 **sp_replmonitorhelpmergesession**用于监视合并复制。  
  
 在订阅服务器上执行时, **sp_replmonitorhelpmergesession**仅返回最近5个合并代理会话的信息。  
  
## <a name="permissions"></a>权限  
 只有分发服务器上的分发数据库或订阅服务器上的订阅数据库中的**db_owner**或**replmonitor**固定数据库角色的成员才能执行**sp_replmonitorhelpmergesession**。  
  
## <a name="see-also"></a>请参阅  
 [以编程方式监视复制](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
