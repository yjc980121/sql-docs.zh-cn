---
title: MStracer_history (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MStracer_history
- MStracer_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_history system table
ms.assetid: 97237a0c-d574-4b17-8a94-1a8730b31d98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e1683427057ac458e09bddde51dc70d8d402d38
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016456"
---
# <a name="mstracerhistory-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_history**表维护已在订阅服务器收到的所有跟踪令牌记录。 此表存储在分发数据库中，复制过程使用此表来监视性能。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|唯一地标识跟踪令牌。|  
|**agent_id**|**int**|标识处理跟踪令牌记录的代理。|  
|**subscriber_commit**|**datetime**|向订阅服务器提交跟踪令牌记录的日期和时间。|  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
