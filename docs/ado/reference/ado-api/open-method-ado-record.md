---
title: Open 方法 （ADO 记录） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97c7f1c143c83dd35ca5ff17e9776d79fb734ff9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917925"
---
# <a name="open-method-ado-record"></a>Open 方法（ADO 记录）
此时将打开一个现有[记录](../../../ado/reference/ado-api/record-object-ado.md)对象，或创建新的项表示**记录**，如文件或目录。  
  
## <a name="syntax"></a>语法  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Parameters  
 *数据源*  
 可选。 一个**Variant**可能表示该实体的 URL，以将由此**记录**对象，**命令**，打开[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)或另一个**记录**对象，包含一个 SQL SELECT 语句或表名称的字符串。  
  
 *ActiveConnection*  
 可选。 一个**Variant**表示的连接字符串或打开[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象。  
  
 *模式*  
 可选。 一个[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)值，该值指定所产生的访问模式**记录**对象。 默认值是**adModeUnknown**。  
  
 *CreateOptions*  
 可选。 一个[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)值，该值指定是否应打开现有文件或目录，或应创建新文件或目录。 默认值是**adFailIfNotExists**。 如果设置为默认值，请访问模式获取从[模式下](../../../ado/reference/ado-api/mode-property-ado.md)属性。 忽略此参数时*源*参数不包含 URL。  
  
 *选项*  
 可选。 一个[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)值，该值指定用于打开选项**记录**。 默认值是**adOpenRecordUnspecified**。 可以组合这些值。  
  
 *UserName*  
 可选。 一个**字符串**值，该值包含必需的如果授予的访问权限的用户 ID*源*。  
  
 *密码*  
 可选。 一个**字符串**值，该值包含的密码是必需的如果将验证是否*用户名*。  
  
## <a name="remarks"></a>备注  
 *源*可能是：  
  
-   一个 URL。 如果 url 的协议为 http，将默认情况下调用 Internet 提供商。 如果 URL 指向包含一个可执行脚本的节点 (如。ASP 页面）**记录**，其中包含源而不是执行默认情况下打开内容。 使用*选项*参数来修改此行为。  
  
-   一个**记录**对象。 一个**记录**从另一个打开的对象**记录**将克隆原始**记录**对象。  
  
-   一个**命令**对象。 打开**记录**对象表示通过执行返回的单个行**命令**。 如果结果包含多个行，第一行的内容放置在记录和错误可能会添加到**错误**集合。  
  
-   SQL SELECT 语句。 打开**记录**对象都表示返回通过执行该字符串的内容的单个行。 如果结果包含多个行，第一行的内容放置在记录和错误可能会添加到**错误**集合。  
  
-   表名称。  
  
 如果**记录**对象表示 URL 不能访问的实体 (例如，行**记录集**派生自数据库)，这两者的值[ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)属性和访问与字段**adRecordURL**常量均为 null。  
  
> [!NOTE]
>  Url 使用 http 方案将自动调用[Microsoft OLE DB 访问接口用于 Internet 发布](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)。 有关详细信息，请参阅[绝对和相对 Url](../../../ado/guide/data/absolute-and-relative-urls.md)。  
  
## <a name="applies-to"></a>适用范围  
 [记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [Open 方法 （ADO 连接）](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open 方法 （ADO 记录集）](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open 方法 (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema 方法](../../../ado/reference/ado-api/openschema-method.md)
