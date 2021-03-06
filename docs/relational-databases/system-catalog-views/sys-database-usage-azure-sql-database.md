---
title: sys. database_usage （Azure SQL Database） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0a0789ebd9a5aa4bd10605d69afa59a586ce75b2
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155536"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **注意：这仅适用于 Azure SQL 数据库 V11。**  
  
 列出 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 服务器上数据库的数量、类型和持续时间。  
  
 **Sys. database_usage**视图包含以下列。  
  
|Column Name|描述|  
|-----------------|-----------------|  
|time|使用事件发生的日期。|  
|sku|数据库的服务层类型： **Web**、 **Business**、 **Basic**、 **Standard**、 **Premium**|  
|数量|指定当天存在的 SKU 类型的数据库的最大数量。|  
  
## <a name="permissions"></a>Permissions  
 对此视图的只读访问权限可用于具有连接到**master**数据库的权限的所有用户。  
  
## <a name="remarks"></a>Remarks  
 对于订阅的每一天， **sys.databases database_usage**视图都返回一行。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Database 定价详细信息](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Azure SQL Database 中的帐户和计费](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
