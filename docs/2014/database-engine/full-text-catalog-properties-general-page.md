---
title: 全文目录属性 （常规页） |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: be73ed98700ef261ccee026469dddd22017998e0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62779660"
---
# <a name="full-text-catalog-properties-general-page"></a>全文目录属性（“常规”页）
  本节介绍在 **“全文目录属性”** 对话框的 **“常规”** 页上可用的选项和功能。  
  
> [!NOTE]  
>  对于 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 数据库，全文目录是表示一组全文索引的逻辑概念。 全文目录是虚拟对象，不属于任何文件组。  
  
## <a name="options"></a>选项  
  
### <a name="properties"></a>属性  
 **默认目录**  
 显示目录是否为数据库的默认目录。  
  
 **填充状态**  
 指示目录的状态。 可能的值有：  
  
-   **Idle**  
  
-   **正在进行爬网**  
  
-   **已暂停**  
  
-   **限制**  
  
-   **恢复**  
  
-   **关闭**  
  
-   **正在进行增量填充**  
  
-   **正在生成索引**  
  
-   **磁盘已满暂停**  
  
-   **Change tracking**  
  
 **项计数**  
 显示目录中的全文项数。  
  
 **目录大小**  
 显示全文目录的大小 (MB)。  
  
 **名称**  
 全文目录的名称。  
  
 **区分重音**  
 查看或修改目录是否区分标注字符，例如波形符 ( **~** )、锐音符 (**´**) 或元音 (**¨**)。 有效值为  
  
-   **是**  
  
-   **是**  
  
-   有关标注字符的信息，请参阅[音调符号](https://www.merriam-webster.com/dictionary/diacritic)Merriam Webster 字典中。  
  
 **上次填充日期**  
 显示上次填充目录的日期。  
  
 **“所有者”**  
 全文目录的所有者。  
  
 **唯一键计数**  
 组成目录的全文索引的唯一词条的数目。  
  
### <a name="catalog-action"></a>目录操作  
  
|||  
|-|-|  
|**无**|不执行 **“优化目录”** 、 **“重新生成目录”** 或 **“重新填充目录”** 操作。|  
|**优化目录**|优化目录的空间利用率，从而提高查询性能。 它还可提高搜索结果相关排名的准确性。<br /><br /> 该操作执行 ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE。|  
|**重新生成目录**|删除并重新生成全文目录。 如果更改了基本目录属性（如区分重音），则必须执行此操作。<br /><br /> 全文目录所在的文件组必须为联机或可读写状态，重新生成才可成功。 重新生成后，全文索引将重新填充。<br /><br /> 该操作执行 ALTER FULLTEXT CATALOG *catalog_name* REBUILD。|  
|**重新填充目录**|使用数据的最新更改来更新目录。 使用此选项并不要求停用目录。|  
  
## <a name="see-also"></a>请参阅  
 [填充全文索引](../relational-databases/indexes/indexes.md)  
  
  
