---
title: 发布数据库 | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 38694dfd2eadb4b25c2606bc825f5388e48daf29
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770061"
---
# <a name="publication-database"></a>发布数据库
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  发布数据库是发布服务器上的数据库，它是要复制的数据和数据库对象的源。 必须启用复制操作中使用的每个发布数据库。 当 **sysadmin** 固定服务器角色成员执行以下任一操作时，即可启用相应的数据库：  
  
-   使用新建发布向导对该数据库创建发布。  
  
-   在 **“发布服务器属性”** 对话框中选择该数据库。  
  
-   执行 **sp_replicationdboption** ，并将 **publish** （对于快照发布或事务发布）或 **merge publish** （对于合并发布）选项设置为 **True**。  
  
## <a name="options"></a>选项  
 **数据库**  
 选择包含要发布的数据和数据库对象的数据库名称。  
  
## <a name="see-also"></a>另请参阅  
 [发布数据和数据库对象](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [查看和修改分发服务器和发布服务器属性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  
