---
title: sp_addsubscriber （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscriber
- sp_addsubscriber_TSQL
helpviewer_keywords:
- sp_addsubscriber
ms.assetid: b8a584ea-2a26-4936-965b-b84f026e39c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 278af2ca1bd6abdb84cdf2371628c6b95662e46e
ms.sourcegitcommit: eae9efe2a2d3758685e85039ffb8fa698aa47f9b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73962411"
---
# <a name="sp_addsubscriber-transact-sql"></a>sp_addsubscriber (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  向发布服务器添加新的订阅服务器，使其能够接收发布。 对于快照和事务发布，此存储过程在发布服务器的发布数据库中执行；对于使用远程分发服务器的合并发布，此存储过程在分发服务器执行。  
  
> [!IMPORTANT]  
>  已不推荐使用此存储过程。 你不再需要在发布服务器上显式注册订阅服务器。  
  
 ![“主题链接”图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_addsubscriber [ @subscriber = ] 'subscriber'  
    [ , [ @type = ] type ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @commit_batch_size = ] commit_batch_size ]  
    [ , [ @status_batch_size = ] status_batch_size ]  
    [ , [ @flush_frequency = ] flush_frequency ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @description = ] 'description' ]  
    [ , [ @security_mode = ] security_mode ]  
    [ , [ @encrypted_password = ] encrypted_password ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @subscriber = ] 'subscriber'` 是要作为有效订阅服务器添加到此服务器上的发布的服务器名称。 *订阅服务器*的**sysname**，无默认值。  
  
`[ @type = ] type` 是订阅服务器的类型。 *类型*为**tinyint**，可以是下列值之一。  
  
|“值”|描述|  
|-----------|-----------------|  
|**0** （默认值）|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器|  
|**1**|ODBC 数据源服务器|  
|**2**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet 数据库|  
|**3**|OLE DB 访问接口|  
  
`[ @login = ] 'login'` 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的登录 ID。 login 的数据类型为 sysname，默认值为 NULL。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @password = ] 'password'` 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的密码。 *password*为**nvarchar （524）** ，默认值为 NULL。  
  
> [!IMPORTANT]  
>  不要使用空密码。 请使用强密码。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @commit_batch_size = ] commit_batch_size` 此参数已被弃用，并且保持为脚本的向后兼容性。  
  
> [!NOTE]  
>  在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @status_batch_size = ] status_batch_size` 此参数已被弃用，并且保持为脚本的向后兼容性。  
  
> [!NOTE]  
>  在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @flush_frequency = ] flush_frequency` 此参数已被弃用，并且保持为脚本的向后兼容性。  
  
> [!NOTE]  
>  在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @frequency_type = ] frequency_type` 是计划复制代理的频率。 *frequency_type*为**int**，可以是下列值之一。  
  
|“值”|描述|  
|-----------|-----------------|  
|**1**|一次|  
|**2**|“按需”|  
|**4**|每天|  
|**8**|每周|  
|**16**|每月|  
|**32**|与“每月”选项相关|  
|**64** （默认值）|自动启动|  
|**128**|重复执行|  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @frequency_interval = ] frequency_interval` 是应用于*frequency_type*设置的频率的值。 *frequency_interval*的值为**int**，默认值为1。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` 是复制代理的日期。 如果*frequency_type*设置为**32** （每月相对），则使用此参数。 *frequency_relative_interval*为**int**，可以是下列值之一。  
  
|“值”|描述|  
|-----------|-----------------|  
|**1** （默认值）|第一个|  
|**2**|第二个|  
|**4**|第三个|  
|**8**|第四个|  
|**16**|上一次|  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 是*frequency_type*使用的重复因子。 *frequency_recurrence_factor*的值为**int**，默认值为**0**。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @frequency_subday = ] frequency_subday` 是在定义的时间段内重新计划的频率。 *frequency_subday*为**int**，可以是下列值之一。  
  
|“值”|描述|  
|-----------|-----------------|  
|**1**|一次|  
|**2**|第二个|  
|**4** （默认值）|Minute|  
|**8**|Hour|  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 是*frequency_subday*的间隔。 *frequency_subday_interval*的值为**int**，默认值为**5**。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` 是第一次安排复制代理的时间，格式为 HHMMSS。 *active_start_time_of_day*的值为**int**，默认值为**0**。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` 是停止安排复制代理的时间，格式为 HHMMSS。 *active_end_time_of_day*的值为**int**, 默认值为 235959, 这意味着 11:59:59 P.M。 以24小时制计量。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @active_start_date = ] active_start_date` 是第一次安排复制代理的日期，格式为 YYYYMMDD。 *active_start_date*的值为**int**，默认值为0。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @active_end_date = ] active_end_date` 是停止安排复制代理的日期，格式为 YYYYMMDD。 *active_end_date*的值为**int**，默认值为99991231，表示9999年12月31日。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @description = ] 'description'` 是订阅服务器的文本说明。 *description*的值为**nvarchar （255）** ，默认值为 NULL。  
  
`[ @security_mode = ] security_mode` 是实现的安全模式。 *security_mode*的值为**int**，默认值为1。 **0**指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。 **1**指定 Windows 身份验证。  
  
> [!NOTE]  
>  不推荐使用此参数，保留它是为了让脚本能够向后兼容。 现在，在执行[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)时，将基于每个订阅指定属性。 在指定值后，该值将用作在此订阅服务器上创建订阅时的默认值，同时返回一条警告消息。  
  
`[ @encrypted_password = ] encrypted_password` 此参数已被弃用，并且为向后兼容性而提供，则将*Encrypted_password*设置为任何值，但**0**会导致错误。  
  
`[ @publisher = ] 'publisher'` 指定不 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器。 *发布服务器*的**sysname**，默认值为 NULL。  
  
> [!NOTE]  
>  从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器进行发布时，不应使用*publisher* 。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>Remarks  
 **sp_addsubscriber**用于快照复制、事务复制和合并复制。  
  
 如果订阅服务器将仅具有合并发布的匿名订阅，则不需要**sp_addsubscriber** 。  
  
 **sp_addsubscriber**写入**分发**数据库中的[MSsubscriber_info](../../relational-databases/system-tables/mssubscriber-info-transact-sql.md)表。  
  
## <a name="permissions"></a>Permissions  
 只有**sysadmin**固定服务器角色的成员才能**sp_addsubscriber**执行。  
  
## <a name="see-also"></a>另请参阅  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [sp_changesubscriber &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)  
  
  
