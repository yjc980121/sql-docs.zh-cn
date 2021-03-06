---
title: sp_validatelogins (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_validatelogins
- sp_validatelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validatelogins
ms.assetid: 6ac52e21-e20d-469b-ad40-5aa091e06b61
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: bd29100f8f7c54906b8aeafa98a7cf67f526db8b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68021047"
---
# <a name="spvalidatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  报告有关映射到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主体但不再存在于 Windows 环境中的 Windows 用户和组的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_validatelogins  
```  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**SID**|**varbinary(85)**|Windows 用户或组的 Windows 安全性标识符 (SID)。|  
|**NT 登录名**|**sysname**|Windows 用户或组的名称。|  
  
## <a name="remarks"></a>备注  
 如果孤立的服务器级主体拥有数据库用户，则必须在删除孤立的服务器主体之前首先删除该数据库用户。 若要删除的数据库用户，请使用[DROP USER](../../t-sql/statements/drop-user-transact-sql.md)。 如果服务器级主体在数据库中拥有安全对象，则必须转移安全对象的所有权，或删除这些安全对象。 若要转移数据库安全对象的所有权，请使用[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)。  
  
 若要删除映射到 Windows 用户和组不再存在，请使用[DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)。  
  
## <a name="permissions"></a>权限  
 要求的成员身份**sysadmin**或**securityadmin**固定的服务器角色。  
  
## <a name="examples"></a>示例  
 以下示例显示不存在但仍被授权访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的 Windows 用户和组。  
  
```  
EXEC sp_validatelogins;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [安全存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP USER (Transact-SQL)](../../t-sql/statements/drop-user-transact-sql.md)   
 [DROP LOGIN (Transact-SQL)](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
