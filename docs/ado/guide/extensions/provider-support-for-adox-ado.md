---
title: ADOX (ADO) 的提供程序支持 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b07f4563d54254310c08c8c132d0729b8ccdc6b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923218"
---
# <a name="provider-support-for-adox-ado"></a>ADOX 的提供程序支持 (ADO)
ADOX 的某些功能不受支持，具体取决于 OLE DB 数据访问接口。 完全支持 ADOX [OLE DB Provider for Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)。 不支持的功能与[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)，则[Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)，或[Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)是下表中列出。 ADOX 不支持的任何其他 Microsoft OLE DB 提供程序。  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>SQL Server 的 Microsoft OLE DB 提供程序  
  
|对象或集合|使用限制|  
|--------------------------|-----------------------|  
|**表**集合|引用现有对象时，属性是读/写对象的创建过程之前，只读的。|  
|**视图**集合|**视图**不受支持。|  
|**过程**集合|**追加**并**删除**不支持的方法。|  
|**过程**对象|**命令**不支持属性。|  
|**密钥**集合|**追加**并**删除**不支持的方法。|  
|**用户**集合|**用户**不受支持。|  
|**组**集合|**组**不受支持。|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Microsoft OLE DB Provider for ODBC  
  
|对象或集合|使用限制|  
|--------------------------|-----------------------|  
|**目录**对象|**创建**不支持方法。|  
|**表**集合|**追加**并**删除**不支持的方法。 引用现有对象时，属性是读/写对象的创建过程之前，只读的。|  
|**过程**集合|**追加**并**删除**不支持的方法。|  
|**过程**对象|**命令**不支持属性。|  
|**索引**集合|**追加**并**删除**不支持的方法。|  
|**密钥**集合|**追加**并**删除**不支持的方法。|  
|**用户**集合|**用户**不受支持。|  
|**组**集合|**组**不受支持。|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Microsoft OLE DB Provider for Oracle  
  
|对象或集合|使用限制|  
|--------------------------|-----------------------|  
|**目录**对象|**创建**不支持方法。|  
|**表**集合|**追加**并**删除**不支持的方法。 引用现有对象时，属性是读/写对象的创建过程之前，只读的。|  
|**视图**集合|**追加**并**删除**不支持的方法。|  
|**视图**对象|**命令**不支持属性。|  
|**过程**对象|**追加**并**删除**不支持的方法。|  
|**过程**对象|**命令**不支持属性。|  
|**索引**集合|**追加**并**删除**不支持的方法。|  
|**密钥**集合|**追加**并**删除**不支持的方法。|  
|**用户**集合|**用户**不受支持。|  
|**组**集合|**组**不受支持。|
