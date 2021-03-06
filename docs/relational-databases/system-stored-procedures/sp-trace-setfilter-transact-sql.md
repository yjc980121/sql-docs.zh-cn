---
title: sp_trace_setfilter (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f48f7e8dd6e7d8fa57868994f9bcabb66777e90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68095942"
---
# <a name="sptracesetfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  将筛选应用于跟踪。 **sp_trace_setfilter**可能仅在已停止的现有跟踪上执行 (*状态*是**0**)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果不存在的跟踪或其执行此存储的过程返回错误*状态*不是**0**。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 请改用扩展事件。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_trace_setfilter [ @traceid = ] trace_id   
          , [ @columnid = ] column_id  
          , [ @logical_operator = ] logical_operator  
          , [ @comparison_operator = ] comparison_operator  
          , [ @value = ] value  
```  
  
## <a name="arguments"></a>参数  
`[ @traceid = ] trace_id` 是向其设置的筛选器的 ID。 *trace_id*是**int**，无默认值。 用户采用该*trace_id*值来标识、 修改和控制跟踪。  
  
`[ @columnid = ] column_id` 是在其应用筛选器的 ID。 *column_id*是**int**，无默认值。 如果*column_id*为 NULL，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]清除指定的跟踪的所有筛选器。  
  
`[ @logical_operator = ] logical_operator` 指定是否 AND (**0**) 或 OR (**1**) 运算符应用。 *logical_operator*是**int**，无默认值。  
  
`[ @comparison_operator = ] comparison_operator` 指定要进行比较的类型。 *comparison_operator*是**int**，无默认值。 下表包含比较运算符及其代表的值。  
  
|ReplTest1|比较运算符|  
|-----------|-------------------------|  
|**0**|= （等于）|  
|**1**|<> （不等于）|  
|**2**|> （大于）|  
|**3**|< (小于)|  
|**4**|> = (大于或等于)|  
|**5**|< = （小于或等于）|  
|**6**|LIKE|  
|**7**|不类似于|  
  
`[ @value = ] value` 指定对其进行筛选的值。 数据类型*值*必须匹配要筛选的列的数据类型。 例如，如果是对对象 ID 列设置的筛选器**int**数据类型*值*必须是**int**。如果*值*是**nvarchar**或**varbinary**，它可以具有最大长度为 8000。  
  
 比较运算符为 LIKE 或 NOT LIKE 时，逻辑运算符可以包括“%”或其他适合 LIKE 运算的筛选器。  
  
 可以指定为空，*值*筛选出其列值的事件。 仅**0** （= 等于） 和**1** (<> 不等于) 运算符才有效为 NULL。 在这种情况下，这些运算符等同于 [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL 和 IS NOT NULL 运算符。  
  
 应用之间的列的值，范围筛选器**sp_trace_setfilter**必须执行两次-一次更高版本比-或者-等于 ('> =) 比较运算符和一次用小于-或者-等于 ('< =') 运算符.  
  
 有关数据列数据类型的详细信息，请参阅[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)。  
  
## <a name="return-code-values"></a>返回代码值  
 下表说明在存储过程完成后用户可能获得的代码值。  
  
|返回代码|描述|  
|-----------------|-----------------|  
|0|没有错误。|  
|1|未知错误。|  
|2|本跟踪当前正在运行。 更改跟踪，在此时间会导致错误。|  
|4|指定的列不是有效的。|  
|5|不允许筛选指定的列。 只能从返回此值**sp_trace_setfilter**。|  
|6|指定的比较运算符无效。|  
|7|指定的逻辑运算符无效。|  
|9|指定的跟踪句柄无效。|  
|13|内存不足。 在没有足够内存执行指定的操作时返回此代码。|  
|16|该函数对此跟踪无效。|  
  
## <a name="remarks"></a>备注  
 **sp_trace_setfilter**是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存储过程，它执行以前由早期版本中可用的扩展存储过程执行的操作的许多[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 使用**sp_trace_setfilter**而不是**xp_trace_set\*筛选器**扩展存储的过程来创建，将应用、 删除或操作上跟踪的筛选器。 有关详细信息，请参阅[筛选跟踪](../../relational-databases/sql-trace/filter-a-trace.md)。  
  
 中的一个执行必须一起启用特定列的所有筛选器**sp_trace_setfilter**。 例如，如果用户想对应用程序名称列应用两个筛选器，对用户名列应用一个筛选器，则用户必须按顺序对应用程序名称指定筛选器。 如果用户试图在一次存储过程调用中先对应用程序名称指定一个筛选器，接着对用户名指定筛选器，然后对应用程序名称指定另一个筛选器，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将返回错误。  
  
 参数的所有 SQL 跟踪存储过程 (**sp_trace_xx**) 已严格类型化。 如果这些参数不是使用正确的输入参数数据类型（正如参数说明中指定的一样）调用的，则存储过程会返回错误。  
  
## <a name="permissions"></a>权限  
 用户必须拥有 ALTER TRACE 权限。  
  
## <a name="examples"></a>示例  
 以下示例对 Trace `1` 设置三个筛选器。 筛选器 `N'SQLT%'` 和 `N'MS%'` 使用“`AppName`”比较运算符对一列（`10`，其值为 `LIKE`）进行操作。 筛选器 `N'joe'` 使用“`UserName`”比较运算符对另一列（`11`，其值为 `EQUAL`）进行操作。  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>请参阅  
 [sys.fn_trace_getfilterinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_getinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [SQL 跟踪](../../relational-databases/sql-trace/sql-trace.md)  
  
  
