---
title: sp_pdw_remove_network_credentials
titleSuffix: Azure SQL Data Warehouse
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.subservice: design
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: c12696a2-5939-402b-9866-8a837ca4c0a3
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7068beee49260db17e7b8f704e5aba316deb6ea3
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844440"
---
# <a name="sp_pdw_remove_network_credentials-sql-data-warehouse"></a>sp_pdw_remove_network_credentials （SQL 数据仓库）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  这会删除 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 中存储的网络凭据以访问网络文件共享。 例如，使用此存储过程可删除 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 在驻留在自己的网络中的服务器上执行备份和还原操作的权限。  
  
 ![主题链接”图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_remove_network_credentials 'target_server_name'  
```  
  
## <a name="arguments"></a>参数  
 "*target_server_name*"  
 指定目标服务器主机名或 IP 地址。 将从 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]中删除用于访问此服务器的凭据。 这不会更改或删除你自己的团队管理的实际目标服务器上的任何权限。  
  
 *target_server_name*定义为 nvarchar （337）。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="permissions"></a>权限  
 需要**ALTER SERVER STATE**权限。  
  
## <a name="error-handling"></a>错误处理  
 如果在控制节点和所有计算节点上删除凭据不成功，则会发生错误。  
  
## <a name="general-remarks"></a>一般备注  
 此存储过程从 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]的 NetworkService 帐户中删除网络凭据。 NetworkService 帐户在控制节点和计算节点上运行 SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的每个实例。 例如，在运行备份操作时，控制节点和每个计算节点将使用 NetworkService 帐户凭据来访问目标服务器。  
  
## <a name="metadata"></a>元数据  
 若要列出所有凭据并验证是否已删除凭据，请使用[sys. dm_pdw_network_credentials &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md)。  
  
 若要添加凭据，请使用[sp_pdw_add_network_credentials &#40;SQL&#41;数据仓库](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-remove-credentials-for-performing-a-database-backup"></a>A. 删除用于执行数据库备份的凭据  
 下面的示例将删除用于访问 IP 地址为10.192.147.63 的目标服务器的用户名和密码凭据。  
  
```  
EXEC sp_pdw_remove_network_credentials '10.192.147.63';  
```  
  
  

