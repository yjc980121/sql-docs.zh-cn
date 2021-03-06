---
title: 获取有关事件通知的信息 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fefdced57d611d241dbb96b71a0b220139683243
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083835"
---
# <a name="get-information-about-event-notifications"></a>获取有关事件通知的信息
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  下列目录视图可用于查询有关事件通知的元数据。  
  
 **获取有关非服务器级别事件通知的信息**  
  
-   [sys.event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  若要查看 sys.event_notifications 中在数据库级别创建的任意事件通知的元数据，至少必须满足下列条件  ：在数据库上具有 CONTROL、ALTER、TAKE OWNERSHIP 或 VIEW DEFINITION 权限，是事件通知的所有者，或者具有 ALTER ANY DATABASE EVENT NOTIFICATION 权限。 对于针对特定队列创建的事件通知，至少必须满足下列条件：在对象上具有 CONTROL、ALTER、TAKE OWNERSHIP 或 VIEW DEFINITION 权限，是事件通知的所有者，或者具有 ALTER ANY DATABASE EVENT NOTIFICATION 权限。  
  
 **获取有关服务器级别事件通知的信息**  
  
-   [sys.server_event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  至少必须满足下列条件：在服务器上具有 CONTROL 或 VIEW ANY DEFINITION 权限，是事件通知的登录者或所有者，或者具有查看 sys.server_event_notifications 中的任何事件通知的元数据的 ALTER ANY EVENT NOTIFICATION 权限  。  
  
 **获取有关可以激发事件通知的所有事件的信息**  
  
-   [sys.event_notification_event_types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  此目录视图不返回事件组。  
  
## <a name="see-also"></a>另请参阅  
 [事件通知](../../relational-databases/service-broker/event-notifications.md)  
  
  
