---
title: 更改凭据向导（SSRS 本机模式） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 07ca904ab8f98dd4dcbdba3f18f4a6fc6469f26a
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952319"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>更改凭据向导（SSRS 本机模式）
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器提供了更改凭据向导，可引导您完成重新配置报表服务器用于连接到报表服务器数据库的帐户的步骤。 更改凭据时，配置管理器将为报表服务器当前使用的报表服务器数据库更新数据库服务器的所有权限和数据库登录信息。  
  
 若要启动此向导，请在 **配置管理器中的“数据库”页上单击** “更改凭据” [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。 有关如何启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager 的说明，请参阅[ &#40;Reporting Services 配置管理器本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式。  
  
## <a name="options"></a>“常规”  
 **数据库服务器**  
 指定运行报表服务器数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的名称。  
  
 若要连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，必须使用有权登录到服务器并更新数据库信息的凭据。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器使用您当前的 Windows 凭据，但如果您没有登录名或数据库权限，可以指定一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名。  
  
 您不能指定其他 Windows 凭据。 如果您希望以其他 Windows 用户身份连接，请以该用户身份登录，然后启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器。  
  
 **凭据**  
 指定用于将报表服务器连接到报表服务器数据库的帐户。 有效值包括报表服务器 Web 服务的服务帐户、在您要用来承载报表服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上定义的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 数据库登录名，或 Windows 帐户。 如果你使用的是 Windows 帐户，则如果\>和数据库位于同一台计算机上，则可以指定本地帐户（ *\<computername >\\< username Report Server* ），或者如果域用户帐户位于同一域中的不同计算机上，则可以指定域用户帐户（ *\<域 >\\< 用户名\>* ）。  
  
 报表服务器将创建一个数据库登录名，并为您指定的帐户分配数据库权限。  
  
 报表服务器自身不创建帐户。 您指定的帐户必须已经存在，并且对于部署配置而言必须是有效的。 具体来说，如果数据库位于远程计算机上并且您希望使用 Windows 帐户，则您必须指定对该计算机拥有登录权限的帐户。  
  
 如果计算机位于其他域或不可信域中，请考虑使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库登录名。 有关选择帐户的详细信息，请参阅[配置报表服务器数据库&#40;连接 SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。  
  
 **摘要**  
 在向导运行之前验证设置。  
  
 **进度和完成**  
 监视每个任务的进度。  
  
## <a name="see-also"></a>另请参阅  
 [数据库&#40;SSRS 本机模式&#41; ](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [更改数据库向导&#40;SSRS 本机模式&#41; ](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [创建本机模式报表服务器数据库（SSRS 配置管理器）](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services 配置管理器 F1 帮助主题&#40;SSRS 本机模式&#41; ](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [配置报表服务器数据库连接（SSRS 配置管理器）](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
