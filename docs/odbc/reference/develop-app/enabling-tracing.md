---
title: 启用跟踪 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 24f80e0e81e4be8895d59256492b868c53aab7b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046790"
---
# <a name="enabling-tracing"></a>启用跟踪
可以启用跟踪，在以下三种方式：  
  
-   设置**跟踪**并**TraceFile** Odbc.ini 注册表项中的关键字。 此启用或禁用跟踪何时**SQLAllocHandle**与*HandleType*设为 SQL_HANDLE_ENV 调用。 在数据源安装过程中显示的 ODBC 数据源管理器对话框的跟踪选项卡中设置这些选项。 有关详细信息，请参阅[数据源的注册表项](../../../odbc/reference/install/registry-entries-for-data-sources.md)。  
  
-   调用**SQLSetConnectAttr**将 SQL_ATTR_TRACE 连接属性设置为 SQL_OPT_TRACE_ON。 这使或连接的持续时间内禁用跟踪。 有关详细信息，请参阅[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)函数说明。  
  
-   使用**ODBCSharedTraceFlag**若要打开或关闭跟踪动态。 (有关详细信息，请参阅下一主题[动态跟踪](../../../odbc/reference/develop-app/dynamic-tracing.md)。)
