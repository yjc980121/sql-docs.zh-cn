---
title: sp_repladdcolumn (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repladdcolumn_TSQL
- sp_repladdcolumn
helpviewer_keywords:
- sp_repladdcolumn
ms.assetid: d6220f9f-c738-4f9c-bcf8-419994e86c81
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75c66d1077b111837197957cc845b690b794ea24
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771053"
---
# <a name="sprepladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  将列添加到已发布的现有表项目中。 允许将新列添加到发布该表的所有发布服务器，或者只将新列添加到发布该表的特定发布中。 此存储过程在发布服务器上对发布数据库执行。  
  
> [!IMPORTANT]
>  已不推荐使用此存储过程，支持它是为了能够向后兼容。 它只能与[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]发布服务器和[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]重新发布订阅服务器一起使用。 不应对列将此过程与 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中引入的数据类型一起使用。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_repladdcolumn [ @source_object = ] 'source_object', [ @column = ] 'column' ]  
    [ , [ @typetext = ] 'typetext' ]  
    [ , [ @publication_to_add = ] 'publication_to_add' ]  
    [ , [ @from_agent = ] from_agent ]  
    [ , [ @schema_change_script = ] 'schema_change_script' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>参数  
 [ @source_object =] "*source_object*"  
 包含要添加的新列的表项目的名称。 *source_object*的值为**nvarchar (358**), 无默认值。  
  
 [ @column =] "*column*"  
 表中要为复制添加的列的名称。 *列*的值为**sysname**, 无默认值。  
  
 [ @typetext =] "*typetext*"  
 要添加的列的定义。 *typetext*的值为**nvarchar (3000)** , 无默认值。 例如, 如果正在添加列 order_filled, 并且它是一个字符字段, 而不是 NULL, 并且默认值为**N**, 则 order_filled 将为*column*参数, 而列的定义为**CHAR (1) not NULL 约束constraint_name 默认值 "N"** 将是*typetext*参数值。  
  
 [ @publication_to_add =] "*publication_to_add*"  
 要向其中添加新列的发布的名称。 *publication_to_add*的值为**nvarchar (4000)** , 默认值为**ALL**。 如果为**all**, 则包含此表的所有发布都会受到影响。 如果指定了*publication_to_add* , 则只有此发布添加了新列。  
  
 [ @from_agent =] *from_agent*  
 表示是否由复制代理执行该存储过程。 *from_agent*的默认值为 0, 默认值为**0**, 在复制代理执行此存储过程时, 将使用值**1** , 而在其他所有情况下, 都应使用默认值**0**。  
  
 [ @schema_change_script =] "*schema_change_script*"  
 指定用于修改系统生成的自定义存储过程的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本的名称和路径。 *schema_change_script*的值为**nvarchar (4000)** , 默认值为 NULL。 复制允许用户定义的自定义存储过程替换事务复制中使用的一个或多个默认过程。 使用 sp_repladdcolumn 对复制的表项目进行架构更改后, 将执行*schema_change_script* , 并可用于执行以下操作之一:  
  
-   如果自定义存储过程是自动重新生成的, 则可以使用*schema_change_script*来删除这些自定义存储过程, 并将其替换为支持新架构的用户定义的自定义存储过程。  
  
-   如果自定义存储过程不是自动重新生成的, 则可以使用*schema_change_script*来重新生成这些存储过程或创建用户定义的自定义存储过程。  
  
 [ @force_invalidate_snapshot =] *force_invalidate_snapshot*  
 启用或禁用使快照失效的功能。 *force_invalidate_snapshot*的值为**bit**, 默认值为**1**。  
  
 **1**指定对项目所做的更改可能会导致快照无效, 如果是这种情况, 则值**1**将为新快照提供权限。  
  
 **0**指定对项目所做的更改不会导致快照无效。  
  
 [ @force_reinit_subscription =] *force_reinit_subscription*  
 启用或禁用使订阅重新初始化的功能。 *force_reinit_subscription*为**位**, 默认值为**0**。  
  
 **0**指定对项目所做的更改不会导致重新初始化订阅。  
  
 **1**指定对项目所做的更改可能导致订阅重新初始化, 如果是这种情况, 则值**1**为重新初始化订阅提供权限。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="permissions"></a>权限  
 只有 sysadmin 固定服务器角色或 db_owner 固定数据库角色的成员才能执行 sp_repladdcolumn。  
  
## <a name="see-also"></a>请参阅  
 [SQL Server 复制中不推荐使用的功能](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
