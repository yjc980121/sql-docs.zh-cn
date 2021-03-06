---
title: 允许为事务发布使用备份进行初始化 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1ce1e95ef182ef119dee8ea666ae0955e4ab625
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128139"
---
# <a name="enable-initialization-with-backup-for-transactional-publications"></a>允许为事务发布使用备份进行初始化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  若要使用备份初始化对事务发布的订阅，请启用发布以允许使用备份进行初始化，然后指定创建订阅时的备份信息：  
  
-   在“发布属性 - \<发布>”对话框的“订阅选项”页中启用发布。 有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)。  
  
-   使用存储过程 [sp_addsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) 指定备份信息。 有关 **sp_addsubscription** 所需的参数的详细信息，请参阅[使用备份初始化事务订阅（复制 Transact-SQL 编程）](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)。  
  
### <a name="to-enable-initialization-with-a-backup"></a>启用使用备份来初始化  
  
1.  在“发布属性 - \<发布>”对话框的“订阅选项”页上，为“允许从备份文件初始化”选项选择“True”值。  
  
## <a name="see-also"></a>另请参阅  
 [初始化事务订阅（不使用快照）](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
