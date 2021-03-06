---
title: sp_pdw_add_network_credentials
titleSuffix: Azure SQL Data Warehouse
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0729eeff-ac7e-43f0-80fa-ff5346a75985
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 88ddae78b3c866556edbd9e3026e3cb86c747f51
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844412"
---
# <a name="sp_pdw_add_network_credentials-sql-data-warehouse"></a>sp_pdw_add_network_credentials （SQL 数据仓库）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  这会在 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 中存储网络凭据，并将其与服务器关联。 例如，使用此存储过程为 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 提供相应的读/写权限，以便在目标服务器上执行数据库备份和还原操作，或创建用于 TDE 的证书的备份。  
  
 ![主题链接”图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_add_network_credentials 'target_server_name',  'user_name', ꞌpasswordꞌ  
```  
  
## <a name="arguments"></a>参数  
 "*target_server_name*"  
 指定目标服务器主机名或 IP 地址。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 将使用传递给此存储过程的用户名和密码凭据访问此服务器。  
  
 若要通过未使用的网络进行连接，请使用目标服务器的未使用的 IP 地址。  
  
 *target_server_name*定义为 nvarchar （337）。  
  
 'user_name'  
 指定有权访问目标服务器的 user_name。 如果目标服务器已有凭据，则这些凭据将更新为新凭据。  
  
 *user_name*定义为 nvarchar （513）。  
  
 '*password*"  
 指定*user_name*的密码。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="permissions"></a>权限  
 需要**ALTER SERVER STATE**权限。  
  
## <a name="error-handling"></a>错误处理  
 如果在控制节点和所有计算节点上添加凭据失败，则会发生错误。  
  
## <a name="general-remarks"></a>一般备注  
 此存储过程将网络凭据添加到 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]的 NetworkService 帐户。 NetworkService 帐户在控制节点和计算节点上运行 SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的每个实例。 例如，在运行备份操作时，控制节点和每个计算节点将使用 NetworkService 帐户凭据获取目标服务器的读取和写入权限。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-add-credentials-for-performing-a-database-backup"></a>A. 添加用于执行数据库备份的凭据  
 下面的示例将域用户 seattle\david 的用户名和密码凭据与 IP 地址为10.172.63.255 的目标服务器相关联。 用户 seattle\david 对目标服务器具有读/写权限。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 将存储这些凭据，并根据备份和还原操作的需要，使用这些凭据在目标服务器上进行读取和写入。  
  
```  
EXEC sp_pdw_add_network_credentials '10.172.63.255', 'seattle\david', '********';  
```  
  
 Backup 命令要求以 IP 地址的形式输入服务器名称。  
  
> [!NOTE]  
>  若要通过不受带宽执行数据库备份，请确保使用备份服务器的未受控制的 IP 地址。  
  
## <a name="see-also"></a>另请参阅  
 [sp_pdw_remove_network_credentials &#40;SQL 数据仓库&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
  

