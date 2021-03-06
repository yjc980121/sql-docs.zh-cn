---
title: sp_dropdistpublisher （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistpublisher
- sp_dropdistpublisher_TSQL
helpviewer_keywords:
- sp_dropdistpublisher
ms.assetid: c0bdd3de-3be0-455c-898a-98d4660e7ce3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a15162774d3814e574735d8e1d5fd5e6b769327f
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278123"
---
# <a name="sp_dropdistpublisher-transact-sql"></a>sp_dropdistpublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  删除分发发布服务器。 此存储过程在分发服务器上的任何数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_dropdistpublisher [ @publisher = ] 'publisher'  
    [ , [ @no_checks = ] no_checks ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>参数  
`[ @publisher = ] 'publisher'` 是要删除的发布服务器。 *发布服务器*的**sysname**，无默认值。  
  
`[ @no_checks = ] no_checks` 指定**sp_dropdistpublisher**是否检查发布服务器是否已卸载服务器作为分发服务器。 *no_checks*为**bit**，默认值为**0**。  
  
 如果为**0**，则复制将验证远程发布服务器是否已卸载本地服务器作为分发服务器。 如果发布服务器是本地服务器，则复制将验证没有发布对象或分发对象保留在本地服务器上。  
  
 如果为**1**，则即使无法访问远程发布服务器，也将删除与分发发布服务器关联的所有复制对象。 执行此操作后，远程发布服务器必须使用 **\@ignore_distributor** = **1**的[sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)卸载复制。  
  
`[ @ignore_distributor = ] ignore_distributor` 指定在删除发布服务器时是否将分发对象保留在分发服务器上。 *ignore_distributor*是**bit** ，可以是下列值之一：  
  
 **1** =*发布*服务器上保留的分发对象。  
  
 **0** = 在分发服务器上清理*发布服务器*的分发对象。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>Remarks  
 **sp_dropdistpublisher**在所有类型的复制中使用。  
  
 删除 Oracle 发布服务器时，如果无法删除发布服务器**sp_dropdistpublisher**将返回错误，并且会删除发布服务器的分发服务器对象。  
  
## <a name="example"></a>示例  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistpublisher-tra_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 只有**sysadmin**固定服务器角色的成员才能**sp_dropdistpublisher**执行。  
  
## <a name="see-also"></a>另请参阅  
 [禁用发布和分发](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistpublisher &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [复制存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
