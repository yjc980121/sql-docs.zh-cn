---
title: 日志文件查看器 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7c587edde597b3b1dffeb60675a1c3c5cb886bc7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084076"
---
# <a name="log-file-viewer"></a>日志文件查看器
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的日志文件查看器用于访问有关在日志文件中捕获的错误和事件的信息。  
  
## <a name="benefits-of-using-log-file-viewer"></a>使用日志文件查看器的优点  
 目标实例处于脱机状态或无法启动时，可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地或远程实例查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件。 您可以从注册的服务器访问脱机日志文件，或者以编程方式通过 WMI 和 WQL（WMI 查询语言）查询访问这些文件。 有关详细信息，请参阅 [查看脱机日志文件](../../relational-databases/logs/view-offline-log-files.md)。 以下是您可以使用日志文件查看器访问的日志文件的类型：  
  
-   审核集合  
  
-   “数据收集”  
  
-   数据库邮件  
  
-   作业历史记录  
  
-   维护计划  
  
-   远程维护计划  
  
-   SQL Server  
  
-   SQL Server 代理  
  
-   Windows NT（这些是还可以从事件查看器访问的 Windows 事件。）  
  
## <a name="log-file-viewer-tasks"></a>日志文件查看器任务  
  
|任务说明|主题|  
|----------------------|-----------|  
|介绍如何根据您要查看的信息来打开日志文件查看器。|[打开日志文件查看器](../../relational-databases/logs/open-log-file-viewer.md)|  
|介绍如何通过注册的服务器来查看脱机日志文件以及如何验证 WMI 权限。|[查看脱机日志文件](../../relational-databases/logs/view-offline-log-files.md)|  
|提供日志文件查看器的 F1 帮助。|[日志文件查看器 F1 帮助](../../relational-databases/logs/log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Audit（数据库引擎）](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [SQL Server 代理错误日志](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
