---
title: SQL Server 代理属性（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 66a7b7cd9328f70e5b5ca374a04ad5e9dd6e079a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63245783"
---
# <a name="sql-server-agent-properties-general-page"></a>SQL Server 代理属性（“常规”页）
  使用此页可以查看和修改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的常规属性。  
  
## <a name="options"></a>选项  
 **服务状态**  
 显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的当前状态。  
  
 **SQL Server 意外停止时自动重新启动**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 意外停止，代理将重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
 **SQL Server 代理意外停止时自动重新启动**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理意外停止，将重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。  
  
 **Filename**  
 指定错误日志的文件名。  
  
 **...**  
 浏览至错误日志文件。  
  
 **包含执行跟踪消息**  
 在错误日志中包含执行跟踪消息。 跟踪消息提供了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理操作的详细信息。 因此，在选中此选项时，日志文件需要更多的磁盘空间。 只有在排除与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理有关的问题时才需要选中此选项。  
  
 **写入 OEM 文件**  
 以非 Unicode 文件的形式编写错误日志文件。 这可以减少日志文件占用的磁盘空间量。 不过，如果启用此选项，读取包含 Unicode 数据的消息时会有一定的难度。  
  
 **Net send 收件人**  
 键入操作员的名称，该操作员负责接收针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理写入日志文件的消息的 net send 通知。  
  
## <a name="see-also"></a>请参阅  
 [运算符](operators.md)   
 [SQL Server 代理错误日志](sql-server-agent-error-log.md)  
  
  
