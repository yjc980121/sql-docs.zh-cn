---
title: Microsoft SQL Server Reporting Services SharePoint 共享服务并行安装（升级顾问） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 529e07dc7beed8dc37741f6c9dab0b0b080d4898
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952694"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>并行安装 Microsoft SQL Server Reporting Services SharePoint 共享服务（升级顾问）
  升级顾问检测到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共享服务与以前版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]并行安装。  
  
||  
|-|  
|SharePoint 模式[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **[!INCLUDE[applies](../../includes/applies-md.md)]** 。|  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>描述  
 升级顾问检测到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 与不基于 SharePoint 共享服务体系结构的旧版本 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 并排安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共享服务。 因为计算机同时并行安装了新旧两种 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 相关技术，所以阻止升级。  
  
## <a name="corrective-action"></a>纠正措施  
 若要继续升级，必须卸载现有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装之一。 删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装之后，重新运行升级顾问以确认没有任何其他升级问题。  
  
  
