---
title: 连接字符串 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f68a87db729df2f4a27e2766a9de60e8c75a71a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036422"
---
# <a name="connection-strings"></a>连接字符串
连接字符串包含用于建立的连接信息。 完整的连接字符串包含建立连接所需的所有信息。 连接字符串是一系列由分号分隔的关键字/值对。 (连接字符串的完整语法，请参阅[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)函数说明。)通过使用的连接字符串：  
  
-   **SQLDriverConnect**，这通过与用户交互来完成的连接字符串。  
  
-   **SQLBrowseConnect**，这将完成以迭代方式与数据源的连接字符串。  
  
 **SQLConnect**不使用连接字符串; 使用**SQLConnect**类似于连接的连接字符串中使用三个关键字/值对 (数据源名称和 （可选） 用户 ID 和密码).
