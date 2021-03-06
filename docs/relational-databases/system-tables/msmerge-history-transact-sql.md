---
title: MSmerge_history (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7de3f8de87804facf6670cf0dd261464143c2aeb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017688"
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_history**表包含历史记录行的前几个合并代理作业会话结果的详细说明。 代理输出的每一行都在表中对应一行。 此表用在分发数据库和每个订阅数据库中。 在分发数据库中，该表包含使用分发服务器的所有合并发布和订阅的历史记录。 在每个订阅数据库中，该表包含将订阅服务器对齐进行了订阅的发布的历史记录。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|合并代理作业的 ID。|  
|**agent_id**|**int**|合并代理的 ID。|  
|**注释**|**nvarchar(255)**|消息文本。|  
|**error_id**|**int**|中的错误的 ID [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md)系统表。|  
|**timestamp**|**timestamp**|该表的时间戳列。|  
|**updatable_row**|**bit**|设置为**1**如果可以覆盖历史记录行。|  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
