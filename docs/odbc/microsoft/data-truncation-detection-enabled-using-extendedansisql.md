---
title: 使用 ExtendedAnsiSQL 启用的数据截断检测 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d7fb67171a796755bf8d6229b9d562f69bd588ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096512"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>使用 ExtendedAnsiSQL 启用的数据截断检测
当启用 ExtendedAnsiSQL 标志和应用程序将数据插入到字符或二进制列和数据将被截断时，将检测截断。 时 ExtendedAnsiSQL 标志处于关闭状态，因为它在以前版本的 ODBC 桌面数据库驱动程序而不发出警告，截断的数据。
