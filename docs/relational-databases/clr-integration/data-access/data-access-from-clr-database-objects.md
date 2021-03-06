---
title: 从 CLR 数据库对象的数据访问 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
author: rothja
ms.author: jroth
ms.openlocfilehash: 29110ecb83493ec95fbc594d0f743c3c4cb07a68
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68216399"
---
# <a name="data-access-from-clr-database-objects"></a>从 CLR 数据库对象进行数据访问
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  公共语言运行时 (CLR) 例程可以轻松地访问的实例中存储的数据[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中它运行所在，以及在远程实例中存储的数据。 该例程可以访问的特定数据由代码正在其中运行的用户上下文确定。 通过使用用于.NET Framework 数据提供程序访问数据从 CLR 数据库对象内的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，也称为**SqlClient**。 这是由从托管客户端和中间层应用程序访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据的开发人员使用的相同访问接口。 因此，您可以利用您的 ADO.NET 知识并**SqlClient**客户端和中间层应用程序中。  
  
> [!NOTE]  
>  默认情况下，不允许用户定义类型方法和用户定义函数执行数据访问。 必须设置**DataAccess**的属性**SqlMethodAttribute**或**SqlFunctionAttribute**到**DataAccessKind.Read**启用从用户定义类型 (UDT) 方法或用户定义的函数的只读数据访问。 不允许从 UDT 或用户定义函数执行数据修改操作，否则，将在执行时引发异常。  
  
 本节只讨论当从 CLR 数据库对象中访问数据时特定的功能差异和行为差异。 有关 ADO.NET 的特性和功能的详细信息，请参阅 .NET Framework SDK 随附的 ADO.NET 文档。  
  
 下表列出了本节的主题。  
  
 [上下文连接](../../../relational-databases/clr-integration/data-access/context-connection.md)  
 介绍与 SQL Server 之间的上下文连接。  
  
 [模拟和连接凭据](../../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
 介绍模拟连接和连接凭据。  
  
 [SQL Server 进程内专用的 ADO.NET 扩展](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 讨论进程内特定**SqlPipe**， **SqlContext**， **SqlTriggerContext**，以及**SqlDataRecord**对象。  
  
 [CLR 集成和事务](../../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
 介绍 System.Transactions 命名空间中提供的新事务框架如何与 ADO.NET 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 集成相集成。  
  
 [从 CLR 数据库对象进行 XML 序列化](https://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344)  
 说明如何对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 CLR 数据库对象启用 XML 序列化方案。  
  
  
