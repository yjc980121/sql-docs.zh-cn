---
title: MSmerge_errorlineage (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c3191191a9830a38a177ba3a3c353e5c34dedba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044758"
---
# <a name="msmergeerrorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_errorlineage**表包含已删除在订阅服务器上，但不是会删除传播到发布服务器的行。 此表存储在发布和订阅数据库中。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|分配给为合并复制发布的表的整数值。 对应于别名字段**sysmergearticles**表。|  
|**rowguid**|**uniqueidentifier**|行标识符。|  
|**沿袭**|**varbinary(501)**|存储订阅服务器和发布服务器对行进行更新的历史记录列表。 用于检测和解决冲突情况。|  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
