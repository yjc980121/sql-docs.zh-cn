---
title: 值列表自变量 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 646d2724489140080a673f31e22429cc7ca39d4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022115"
---
# <a name="value-list-arguments"></a>值列表自变量
值列表自变量包含的逗号分隔值用于匹配列表。 ODBC 目录函数中没有只有一个值列表自变量： *TableType*中的参数**SQLTables**。 设置*TableType*到 null 指针如是否都设置为 SQL_ALL_TABLE_TYPES，枚举的值列表的所有可能成员。 此参数不受 SQL_ATTR_METADATA_ID 语句属性。 有关详细信息，请参阅[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)函数说明。
