---
title: 系统配置检查器的检查参数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a1d08730c8fd4ec5a750c0cf2c70e0498be602e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62779440"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>系统配置检查器的检查参数
  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程中，系统配置检查器 (SCC) 会对将要安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机进行扫描。 SCC 将检查会使安装无法成功 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的情况。 在安装程序启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导之前，SCC 会检索每个项的状态。 然后，将检索结果与所需条件进行比较并提供如何排除妨碍性问题的指导。  
  
 系统配置检查器将会生成一个报告，该报告包含有关每个执行规则的简短说明以及执行状态。 系统配置检查报告位于 %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\。  
  
## <a name="see-also"></a>请参阅  
 [硬件和软件要求安装 SQL Server 2014 的](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [安装 SQL Server 的安全注意事项](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [支持的版本升级](supported-version-and-edition-upgrades.md)  
  
  
