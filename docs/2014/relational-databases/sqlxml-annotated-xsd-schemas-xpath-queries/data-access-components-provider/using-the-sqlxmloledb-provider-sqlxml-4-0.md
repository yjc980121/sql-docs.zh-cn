---
title: 使用 sqlxmloledb 访问接口 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 67a5486816f5af652e111372c9cb492ba3cdb3c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66012952"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>使用 SQLXMLOLEDB 访问接口 (SQLXML 4.0)
  本节中的主题提供 ADO 示例应用程序，这些应用程序说明 SQLXMLOLEDB 访问接口特有的属性的用法。  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>SQLXMLOLEDB 4.0 访问接口的应用程序要求  
 若要创建使用 SQLXMLOLEDB 4.0 的工作示例，必须执行以下操作：  
  
1.  创建 Microsoft Visual Basic .exe 应用程序，并添加以下引用之一：  
  
    -   Microsoft ActiveX 数据对象 2.6 库  
  
    -   Microsoft ActiveX 数据对象 2.7 库  
  
    -   Microsoft ActiveX Data Objects 2.8 Library  
  
2.  部署和安装 SQLXML 4.0 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。  
  
     有关详细信息，请参阅上[SQLXML 4.0 编程概念](../../sqlxml/sqlxml-4-0-programming-concepts.md)并[安装 SQL Server Native Client](../../native-client/applications/installing-sql-server-native-client.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [执行 SQL 查询&#40;sqlxmloledb 访问接口&#41;](executing-sql-queries-sqlxmloledb-provider.md)  
 演示如何使用 ClientSideXML 和 xml 根属性，以执行 SQL 查询。  
  
 [执行包含 SQL 查询的模板&#40;sqlxmloledb 访问接口&#41;](executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 演示如何使用 ClientSideXML 属性。  
  
 [执行 XPath 查询&#40;sqlxmloledb 访问接口&#41;](executing-xpath-queries-sqlxmloledb-provider.md)  
 演示如何使用 ClientSideXML、 基路径和映射架构属性。  
  
 [执行带命名空间的 XPath 查询&#40;sqlxmloledb 访问接口&#41;](executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 说明如何针对已限定命名空间的架构进行查询。  
  
 [执行包含 XPath 查询的模板&#40;sqlxmloledb 访问接口&#41;](executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 说明了如何使用 SQL 查询使用 ClientSideXML、 基路径和映射架构属性执行模板。  
  
 [应用 XSL 转换&#40;sqlxmloledb 访问接口&#41;](applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 演示如何使用中应用 XSL 转换的 ClientSideXML 和 xsl 属性。  
  
## <a name="see-also"></a>请参阅  
 [SQL Server Native Client 的系统要求](../../native-client/system-requirements-for-sql-server-native-client.md)  
  
  
