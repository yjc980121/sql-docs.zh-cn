---
title: 显示数据库的数据和日志空间信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], space
- status information [SQL Server], space
- displaying space information
- disk space [SQL Server], displaying
- databases [SQL Server], space used
- viewing space information
- space allocation [SQL Server], displaying
- data space [SQL Server]
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4850be4c112f9c0b987d543873cb55af08372455
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62917323"
---
# <a name="display-data-and-log-space-information-for-a-database"></a>显示数据库的数据和日志空间信息
  本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中显示数据库的数据和日志空间信息。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [安全性](#Security)  
  
-   **若要显示的数据和日志空间信息对于数据库，使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 执行 **sp_spaceused** 的权限授予 **public** 角色。 只有 **db_owner** 固定数据库角色的成员可以指定 **@updateusage** 参数。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-display-data-and-log-space-information-for-a-database"></a>若要显示数据库的数据和日志空间信息  
  
1.  在对象资源管理器中，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，然后展开该实例。  
  
2.  展开 **“数据库”** 。  
  
3.  右键单击某数据库，依次指向“报表”  和“标准报表”  ，然后单击“磁盘使用情况”  。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-using-spspaceused"></a>使用 sp_spaceused 显示数据库的数据和日志空间信息  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。 该示例使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 系统存储过程报告 `Vendor` 表及其索引的磁盘空间信息。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabasefiles"></a>通过查询 sys.database_files 显示数据库的数据和日志空间信息  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。 此示例查询 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) 目录视图以便返回与 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中的数据和日志文件有关的特定信息。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a>请参阅  
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)   
 [sp_spaceused (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql)   
 [向数据库中添加数据文件或日志文件](add-data-or-log-files-to-a-database.md)   
 [删除数据库中的数据文件或日志文件](delete-data-or-log-files-from-a-database.md)  
  
  
