---
title: 文件和版本号 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7a7d7e7dd9bf7e6d5ad6dfa5776d76892f96ad05
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148659"
---
# <a name="files-and-version-numbers"></a>文件和版本号
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  所有必需的 SQL Server 管理对象 (SMO) 组件都包含在 SqlManagementObjects NuGet 包中。 SMO 实现于几个托管程序集中。 您可以在客户端或服务器上开发 SMO 应用程序。  

> > [!Important]
> > SMO 程序集的文件版本显示为 "主要"。**0**。内部版本. 修订版本。 但嵌入的程序集版本是主要版本。**100**。内部版本. 修订版本。 这样做是为了使每个应用程序中使用的 SMO 版本保持独立, 使更新不会影响其他应用程序。
> > 
> > 因此,**不**应将这些版本的程序集安装到全局程序集缓存 (GAC)。 这样做可能会导致其他应用程序 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如 Management Studio) 中断。 
  
|文件|描述|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|包含对连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的支持。|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|包含对编写 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker 的支持。 这仅在访问 Service Broker 的程序中是必需的。|  
|Microsoft.SqlServer.Smo.dll|包含大多数 SMO 类。|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|包含对 SMO 类的支持。|  
|Microsoft.SqlServer.WmiEnum.dll|包含 Windows Management Instrumentation (WMI) 提供程序类。 这仅对使用 WMI 提供程序类的程序是必需的。|  
|Microsoft.SqlServer.RegSvrEnum.dll|包含注册服务器类。 这仅对使用注册服务器类的程序是必需的。|  
  
  
