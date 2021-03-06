---
title: 备份文件必须位于与数据库文件分开的设备 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 09c54c8229351cf27e0f42c8895f2633b8aa7ccb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62812621"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>备份文件必须位于与数据库文件分开的设备上
  此规则检查数据库文件是否位于与备份文件分开的设备上。 如果数据库文件和备份文件位于同一台设备上并且该设备出现故障，数据库和备份都将不可用。 此外，将数据库和备份文件放到不同的设备上还可以优化使用数据库和写入备份时的 I/O 性能。  
  
## <a name="best-practices-recommendations"></a>最佳做法建议  
 强烈建议您将数据库和备份放到不同的备份设备上。  
  
> [!NOTE]  
>  此策略无法通过装入点检测分开的物理设备。  
  
## <a name="for-more-information"></a>有关详细信息  
 [备份设备 (SQL Server)](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [SQL Server 数据库的备份和还原](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a>请参阅  
 [使用基于策略的管理来监视和强制执行最佳实践](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
