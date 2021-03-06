---
title: 修改作业的目标服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a97fd3892e74b16c844867f88bc7d72fedc46d20
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62720380"
---
# <a name="modify-the-target-servers-for-a-job"></a>Modify the Target Servers for a Job
  本主题说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中更改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的目标服务器。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [安全性](#Security)  
  
-   **若要修改作业的目标服务器，请使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 默认情况下，只有 sysadmin 固定服务器角色的成员才可以执行此存储过程。 其他用户必须被授予 msdb 数据库中下列 SQL Server 代理固定数据库角色的权限之一：  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  SQLAgentOperatorRole  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>修改作业的目标服务器  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。  
  
2.  展开“SQL Server 代理”  ，再展开“作业”  ，右键单击某个作业，然后单击“属性”  。  
  
3.  在“作业属性  ”对话框中，选择“目标”  页，然后单击“目标为本地服务器”  或“目标为多台服务器”  。  
  
     如果选择 **“目标为多台服务器”** ，请选中服务器名称左边的框将其指定为作业的目标服务器。 验证未选中不作为作业的目标服务器旁的复选框。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>修改作业的目标服务器  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。 此示例将“每周销售备份”多服务器作业分配给服务器 SEATTLE2。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 有关详细信息，请参阅[sp_add_jobserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)。  
  
## <a name="see-also"></a>请参阅  
 [企业范围的自动化管理](automated-administration-across-an-enterprise.md)  
  
  
