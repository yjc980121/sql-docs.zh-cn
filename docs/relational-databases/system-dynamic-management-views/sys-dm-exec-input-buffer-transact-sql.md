---
title: sys. dm_exec_input_buffer （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 11/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_input_buffer
- sys.dm_exec_input_buffer _tsql
- dm_exec_input_buffer
- dm_exec_input_buffer_tsql
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_input_buffer dynamic management function
ms.assetid: fb34a560-bde9-4ad9-aa96-0d4baa4fc104
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4e18f635b7bbdd8fa96a565fef6aef5be5bde87f
ms.sourcegitcommit: 0c40843c13f67ba7d975f4fedb9d20d70747f66d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74097869"
---
# <a name="sysdm_exec_input_buffer-transact-sql"></a>sys.dm_exec_input_buffer (Transact-SQL)

[!INCLUDE[tsql-appliesto-2014sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2014sp2-asdb-xxxx-xxx-md.md)]

返回有关提交到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的语句的信息。

## <a name="syntax"></a>语法

```
sys.dm_exec_input_buffer ( session_id , request_id )
```

## <a name="arguments"></a>参数

*session_id*要查找的批处理的会话 ID。 *session_id*为**smallint**。 可以从以下动态管理对象中获取*session_id* ：

- [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
- [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)
- [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)

*request_id*从[dm_exec_requests sys.databases](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)request_id。 *request_id*是**int**。

## <a name="table-returned"></a>返回的表

|列名|数据类型|描述|
|-----------------|---------------|-----------------|
|event_type|**nvarchar(256)**|给定 spid 在输入缓冲区中的事件类型。|
|**参数**|**int**|为语句提供的所有参数。|
|**event_info**|**nvarchar(max)**|给定 spid 的输入缓冲区中的语句文本。|

## <a name="permissions"></a>Permissions

在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上，如果用户具有 VIEW SERVER STATE 权限，则用户将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例上看到所有正在执行的会话;否则，用户将只看到当前会话。

> [!IMPORTANT]
> 在不使用 VIEW SERVER STATE 权限 SQL Server Management Studio 的情况下（例如在触发器、存储过程或函数中）对 SQL Server 运行此 DMV 会引发对 master 数据库的权限错误。

在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]上，如果用户是数据库所有者，则用户将看到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]上所有正在执行的会话;否则，用户将只看到当前会话。

> [!IMPORTANT]
> 在不带所有者权限的 Azure SQL 数据库 SQL Server Management Studio （如触发器、存储过程或函数）中运行此 DMV 会引发对 master 数据库的权限错误。

## <a name="remarks"></a>Remarks

此动态管理函数可与 sys.databases 结合使用，dm_exec_sessions 或**dm_exec_requests。**

## <a name="examples"></a>示例

### <a name="a-simple-example"></a>A. 简单示例

下面的示例演示如何将会话 ID （SPID）和请求 ID 传递到函数。

```sql
SELECT * FROM sys.dm_exec_input_buffer (52, 0);
GO
```

### <a name="b-using-cross-apply-to-additional-information"></a>B. 使用跨应用的其他信息

下面的示例列出会话 ID 大于50的会话的输入缓冲区。

```sql
SELECT es.session_id, ib.event_info
FROM sys.dm_exec_sessions AS es
CROSS APPLY sys.dm_exec_input_buffer(es.session_id, NULL) AS ib
WHERE es.session_id > 50;
GO
```

## <a name="see-also"></a>另请参阅

- [与执行相关的动态管理视图和函数 (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
- [sys.dm_exec_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)
- [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
- [DBCC INPUTBUFFER (Transact-SQL)](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)
