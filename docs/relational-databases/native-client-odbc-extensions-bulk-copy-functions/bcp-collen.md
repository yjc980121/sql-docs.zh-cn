---
title: bcp_collen |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_collen
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d26efd0d7ebd395dd4453e773bc5bb089ae3792
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783203"
---
# <a name="bcp_collen"></a>bcp_collen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  为目标为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的当前大容量复制设置程序变量中的数据长度。  
  
## <a name="syntax"></a>语法  
  
```  
  
RETCODE bcp_collen (  
        HDBC hdbc,  
        DBINT cbData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>参数  
 *hdbc*  
 是启用大容量复制的 ODBC 连接句柄。  
  
 *cbData*  
 程序变量中数据的长度，不包括任何长度指示器或终止符的长度。 将*cbData*设置为 SQL_NULL_DATA 指示复制到服务器的所有行都包含该列的 NULL 值。 设置为 SQL_VARLEN_DATA 则指示使用字符串终止符或其他方法确定复制的数据的长度。 如果同时提供长度指示器和终止符，系统将使用二者中复制数据量较少的一个。  
  
 *idxServerCol*  
 数据复制到的表中的列的序号位置。 第一列为 1。 列的序号位置由[SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)报告。  
  
## <a name="returns"></a>返回  
 SUCCEED 或 FAIL。  
  
## <a name="remarks"></a>注释  
 使用**bcp_collen**函数，可以在将数据复制到[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，更改特定列的程序变量中的数据长度。  
  
 最初，数据长度是在调用[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)时确定的。 如果数据长度在对**bcp_sendrow**的调用之间发生更改，并且没有使用长度前缀或终止符，则可以调用**bcp_collen**来重置长度。 对**bcp_sendrow**的下一次调用使用由对**bcp_collen**的调用设置的长度。  
  
 您必须对要修改其数据长度的表中的每一列调用一次**bcp_collen** 。  
  
## <a name="see-also"></a>另请参阅  
 [大容量复制函数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
