---
title: 配置“默认全文语言”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d98194f5dead58b738c39503445923d9df49be06
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62787034"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a>配置 default full-text language 服务器配置选项
  本主题介绍如何配置`default full-text language`中的服务器配置选项[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]通过使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或[!INCLUDE[tsql](../../includes/tsql-md.md)]。 `default full-text language`选项指定全文索引的默认语言值。 语言分析将对全文索引的所有数据执行，并且取决于数据的语言。 该选项的默认值为服务器的语言。 本地化版本的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安装程序集`default full-text language`选项为服务器的语言，如果存在合适的匹配项。 对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的非本地化版本，`default full-text language` 选项为“英语”。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [建议](#Recommendations)  
  
     [安全性](#Security)  
  
-   **配置 default full-text language 选项，使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **跟进：** [在配置默认全文语言选项之后](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
  
-   值`default full-text language`时通过语言为列不指定任何语言，全文索引中使用的选项**language_term** CREATE FULLTEXT INDEX 或 ALTER FULLTEXT INDEX 语句中的选项。 如果不支持默认全文语言，或者语言分析包不可用，则 CREATE 或 ALTER 操作将失败，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将返回说明指定语言无效的错误消息。  
  
###  <a name="Recommendations"></a> 建议  
  
-   此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。  
  
-   `default full-text language`选项需要 LCID 值。 有关支持的 LCID 及其相关语言的列表，请参阅 [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)。 例如，独立的软件供应商还可提供其他语言。 如果找不到特定区域语言，则全文引擎将自动切换到主要语言。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。 若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。 ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>配置 default full-text language 选项  
  
1.  在对象资源管理器中，右键单击服务器并选择 **“属性”** 。  
  
2.  单击 **“高级”** 节点。  
  
3.  在“杂项”下，使用 **“默认全文语言”** 指定全文索引列的默认语言值。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>配置 default full-text language 选项  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。 此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `default full-text` 选项的值设置为荷兰语 (`1043`)。  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。  
  
##  <a name="FollowUp"></a> 跟进：在配置默认全文语言选项之后  
 该设置将立即生效，无需重新启动服务器。  
  
## <a name="see-also"></a>请参阅  
 [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
