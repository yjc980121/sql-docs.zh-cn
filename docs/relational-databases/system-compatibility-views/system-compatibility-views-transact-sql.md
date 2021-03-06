---
title: 系统兼容性视图 (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- compatibility views [SQL Server]
- system tables [SQL Server], compatibility views
- type IDs [SQL Server]
- system views [SQL Server], compatibility
- metadata [SQL Server], views
- backward compatibility [SQL Server], compatibility views
- compatibility [SQL Server], compatibility views
- backward compatibility [SQL Server], system tables
- compatibility [SQL Server], system tables
- user IDs [SQL Server]
ms.assetid: 8e4624f5-9d36-4ce7-9c9e-1fe010fa2122
author: rothja
ms.author: jroth
ms.openlocfilehash: 466dc68da1c5cef56a7debe3953ba38956bb2993
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018032"
---
# <a name="system-compatibility-views-transact-sql"></a>系统兼容性视图 (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 早期版本中的许多系统表现在都作为一组视图实现。 这些视图称为兼容性视图，仅用于向后兼容。 兼容性视图公开的元数据在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中也提供。 但是，兼容性视图不公开与在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本中引入的功能有关的任何元数据。 因此，当您使用新功能（例如 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 或分区）时，必须切换到使用目录视图。  
  
 升级到目录视图的另一个原因是，存储用户 ID 和类型 ID 的兼容性视图列可能返回 NULL 或触发算术溢出。 这是因为您可以创建超过 32,767 个用户、组和角色，以及超过 32,767 种数据类型。 例如，如果要创建 32,768 个用户，然后运行以下查询： `SELECT * FROM sys.sysusers`。 如果 ARITHABORT 设置为 ON，则查询会失败，并出现算术溢出错误。 如果 ARITHABORT 设置为 OFF， **uid**列返回 NULL。  
  
 若要避免这些问题，建议您使用新增的目录视图，这些视图可以处理增加的用户 ID 和类型 ID 数目。 下表列出了会出现此溢出的列。  
  
|列名|兼容性视图|SQL Server 2005 视图|  
|-----------------|------------------------|--------------------------|  
|**xusertype**|**syscolumns**|**sys.columns**|  
|**usertype**|**syscolumns**|**sys.columns**|  
|**memberuid**|**sysmembers**|**sys.database_role_members**|  
|**groupuid**|**sysmembers**|**sys.database_role_members**|  
|**uid**|**sysobjects**|**sys.objects**|  
|**uid**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**grantor**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**xusertype**|**systypes**|**sys.types**|  
|**uid**|**systypes**|**sys.types**|  
|**uid**|**sysusers**|**sys.database_principals**|  
|**altuid**|**sysusers**|**sys.database_principals**|  
|**gid**|**sysusers**|**sys.database_principals**|  
|**uid**|**syscacheobjects**|**sys.dm_exec_plan_attributes**|  
|**uid**|**sysprocesses**|**sys.dm_exec_requests**|  
  
 当引用用户数据库中，系统表中曾宣布为 SQL Server 2000 中不推荐使用 (如**syslanguages**或**syscacheobjects**)，现在绑定到的后兼容性视图中**sys**架构。 因为多个版本均已不推荐使用 SQL Server 2000 系统表，此更改不被视为重大更改。  
  
 例如：如果用户创建名为的用户表**syslanguages**用户的数据库，在 SQL Server 2008 中，该语句中`SELECT * from dbo.syslanguages;`该数据库中将返回值表中的用户。 从 SQL Server 2012 开始，这种做法将返回的数据从系统视图**sys.syslanguages**。  
  
## <a name="see-also"></a>请参阅  
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [系统表映射到系统视图&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
