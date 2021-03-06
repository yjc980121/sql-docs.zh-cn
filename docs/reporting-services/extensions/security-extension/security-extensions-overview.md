---
title: 安全扩展插件概述 (SSRS) | Microsoft Docs
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c066c893833e1c8588be2460959ed298d6cf1b4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63225858"
---
# <a name="security-extensions-overview---reporting-services-ssrs"></a>安全扩展插件概述 - Reporting Services (SSRS)
  利用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全扩展插件，可以对用户或组进行身份验证和授权；这样，不同的用户便可登录至同一台报表服务器，并基于他们的标识执行不同的任务或操作。 默认情况下，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 使用基于 Windows 的身份验证扩展插件，该插件使用 Windows 帐户协议来验证声明在系统上拥有帐户的用户的标识。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 使用基于角色的安全系统为用户授权。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 基于角色的安全模型与其他技术的基于角色的安全模型类似。  
  
 因为安全扩展插件基于可扩展的开放式 API，所以您可以在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中创建新的身份验证和授权扩展插件。 下面的示例为使用基于窗体的身份验证和授权的典型安全扩展插件实现：  
  
 ![Reporting Services 安全扩展插件进程](../../../reporting-services/extensions/security-extension/media/rosettasecurityextensionflow.gif "Reporting Services security extension process")  
  
 如图所示，身份验证和授权将按以下所示发生：  
  
1.  用户尝试使用 URL 访问 Web 门户，然后被重定向至为客户端应用程序收集用户凭据的窗体。  
  
2.  用户向该窗体提交凭据。  
  
3.  用户凭据通过 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法提交至 Reporting Services Web 服务。  
  
4.  Web 服务调用客户提供的安全扩展插件，并验证相应的用户名称和密码是否存在于自定义安全机构中。  
  
5.  进行身份验证之后，Web 服务创建一个身份验证票证（称为“cookie”），管理票证，然后为 Web 门户的主页验证用户角色。  
  
6.  Web 服务将此 cookie 返回至浏览器，然后在 Web 门户中显示相应的用户界面。  
  
7.  对用户进行身份验证之后，在 HTTP 标头中传送此 cookie 的同时浏览器向 Web 门户发出请求。 这些请求用于响应 Web 门户中的用户操作。  
  
8.  此 cookie 在 HTTP 标头中与请求的用户操作一起传送至 Web 服务。  
  
9. 对此 cookie 进行验证，如果有效，则报表服务器从报表服务器数据库中返回安全描述符及与请求的操作有关的其他信息。  
  
10. 如果此 cookie 有效，报表服务器将调用安全扩展插件检查用户是否有权执行特定操作。  
  
11. 如果用户已有相应权限，则报表服务器将执行请求的操作，并将控制权返回调用方。  
  
12. 用户经过身份验证后，报表服务器进行 URL 访问都会使用此 cookie。 此 cookie 在 HTTP 标头中传送。  
  
13. 用户继续请求对报表服务器的操作，直到会话结束为止。  
  
## <a name="when-to-implement-a-security-extension"></a>使用安全扩展插件的条件  
 建议尽量使用 Windows 身份验证。 不过，在下列两种情况下，可能适合使用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的身份验证和授权：  
  
-   您具有无法使用 Windows 帐户的 Internet 或 Extranet 应用程序。  
  
-   您拥有自定义用户和角色并且需要在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中提供匹配的授权方案。  
  
## <a name="see-also"></a>另请参阅  
 [实现安全扩展插件](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)   
  
  
