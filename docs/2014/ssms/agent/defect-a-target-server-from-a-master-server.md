---
title: 将目标服务器与主服务器脱离 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f51e8f62a6be442c123c5a1309293e204caf08f
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783222"
---
# <a name="defect-a-target-server-from-a-master-server"></a>将目标服务器从主服务器脱离
  本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 SQL Server 管理对象 (SMO) 从 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的主服务器脱离目标服务器。 从目标服务器运行此过程。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [安全性](#Security)  
  
-   **若要脱离目标服务器，请使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 权限  
 若要执行此存储过程，用户必须为 `sysadmin` 固定服务器角色的成员。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>将目标服务器从主服务器脱离  
  
1.  在 **对象资源管理器**中，展开配置为目标服务器的服务器。  
  
2.  右键单击 **“SQL Server 代理”** ，指向 **“多服务器管理”** ，然后单击 **“脱离”** 。  
  
3.  单击 **“是”** 确认要从主服务器脱离此目标服务器。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>将目标服务器从主服务器脱离  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”。  
  
```sql
sp_msx_defect ;  
```  
  
 有关详细信息，请[参阅&#40;sp_msx_defect transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql)。  
  
##  <a name="PowerShellProcedure"></a>使用 SQL Server 管理对象（SMO）  
 使用 `MsxDefect Method`。  
  
## <a name="see-also"></a>另请参阅  
 [创建多服务器环境](create-a-multiserver-environment.md)   
 [企业范围的自动化管理](automated-administration-across-an-enterprise.md)   
 [使多台目标服务器脱离主服务器](defect-multiple-target-servers-from-a-master-server.md)  
