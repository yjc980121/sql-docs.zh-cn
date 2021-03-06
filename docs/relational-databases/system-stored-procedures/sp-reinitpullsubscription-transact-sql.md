---
title: sp_reinitpullsubscription （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitpullsubscription_TSQL
- sp_reinitpullsubscription
helpviewer_keywords:
- sp_reinitpullsubscription
ms.assetid: 7d9abe49-ce92-47f3-82c9-aea749518c91
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f9021ec9b71694fc6567db5edf79965e09fd3c0
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304911"
---
# <a name="sp_reinitpullsubscription-transact-sql"></a>sp_reinitpullsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  将事务请求订阅或匿名订阅标记为在下次运行分发代理时重新初始化。 此存储过程在订阅服务器上对请求订阅数据库执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_reinitpullsubscription [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>参数  
`[ @publisher = ] 'publisher'` 为发布服务器的名称。 *发布服务器*的**sysname**，无默认值。  
  
`[ @publisher_db = ] 'publisher_db'` 为发布服务器数据库的名称。 *publisher_db* **sysname**，无默认值。  
  
`[ @publication = ] 'publication'` 为发布的名称。 *发布*为**sysname**，默认值为 all，表示将所有订阅标记为要重新初始化。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>Remarks  
 **sp_reinitpullsubscription**用于事务复制。  
  
 对等事务复制不支持**sp_reinitpullsubscription** 。  
  
 在下一次运行分发代理期间，可从订阅服务器调用**sp_reinitpullsubscription**以重新初始化订阅。  
  
 不能从订阅服务器重新初始化使用值为**false**的 **\@immediate_sync**创建的发布的订阅。  
  
 您可以通过在订阅服务器上执行**sp_reinitpullsubscription**或在发布服务器上执行**sp_reinitsubscription**来重新初始化请求订阅。  
  
## <a name="example"></a>示例  
 [!code-sql[HowTo#sp_reinitpullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitpullsubscriptio_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 只有**sysadmin**固定服务器角色的成员或**db_owner**固定数据库角色的成员才能执行**sp_reinitpullsubscription**。  
  
## <a name="see-also"></a>另请参阅  
 [重新初始化订阅](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [重新初始化订阅](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
