---
title: 有日志记录的修改与无日志记录的修改 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c722d5360ad01e7e95508c2219ceb674de381286
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63195142"
---
# <a name="logged-vs-unlogged-modifications"></a>有日志记录的修改与无日志记录的修改
  应用程序可以请求的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驱动程序不记录**文本**， **ntext**，并且**映像**的修改。 但应慎用此选项。 它应仅用于下列情况其中**文本**， **ntext**，或**图像**数据并不重要，并且数据所有者愿意放弃恢复数据的能力更高的性能。  
  
 日志记录**文本**， **ntext**，并**图像**通过调用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)与*特性*参数设置为 SQL_SOPT_SS_ TEXTPTR_LOGGING 以及*ValuePtr*设置为 SQL_TL_ON 或 SQL_TL_OFF。  
  
## <a name="see-also"></a>请参阅  
 [管理 Text 和 Image 列](managing-text-and-image-columns.md)  
  
  
