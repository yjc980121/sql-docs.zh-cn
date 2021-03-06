---
title: sys. sensitivity_classifications （Transact-sql） |Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- rank
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 376438a45d6b104cbf4e66dbdf8e5542cf3fd2c2
ms.sourcegitcommit: 02449abde606892c060ec9e9e9a85a3f49c47c6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74542055"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

为数据库中的每个已分类项返回一行。

|列名称|数据类型|说明|
|-----------------|---------------|-----------------|  
|**班级**|**整形**|标识存在分类的项的类。 始终具有值1（表示列）|  
|**class_desc**|**varchar （16）**|存在分类的项的类的说明。 始终具有值*OBJECT_OR_COLUMN*|  
|**major_id**|**整形**|表示包含已分类列的表的 ID，该 ID 与 all_objects 相对应。 object_id|  
|**minor_id**|**整形**|表示存在分类的列的 ID，与 sys. all_columns 相对应 column_id|   
|**标识**|**sysname**|为敏感度分类分配的标签（可读）|  
|**label_id**|**sysname**|与标签关联的 ID，可由信息保护系统（如 Azure 信息保护（AIP））使用|  
|**information_type**|**sysname**|为敏感度分类分配的信息类型（可人工读取）|  
|**information_type_id**|**sysname**|与信息保护系统（如 Azure 信息保护（AIP））关联的信息类型的 ID|  
|**rank**|**整形**|排名的数值： <br><br>0表示无<br>10表示低<br>20个用于中型<br>高30<br>40对于严重| 
|**rank_desc**|**sysname**|排名的文本表示形式：  <br><br>无、低、中、高、严重|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>备注  

- 此视图提供数据库的分类状态的可见性。 它可用于管理数据库分类以及生成报告。
- 目前仅支持对数据库列进行分类。
 
## <a name="examples"></a>示例

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. 列出所有已分类的列及其相应的分类

下面的示例返回一个表，该表列出了数据库中每个已分类列的表名称、列名称、标签、标签 ID、信息类型和信息类型 ID。

> [!NOTE]
> 标签是适用于 Azure SQL 数据仓库的关键字。

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID], [Rank], [Rank_Desc]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>权限  
 需要 "**查看任何敏感度分类**" 权限。 
 
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]有关详细信息，请参阅[元数据可见性配置](../../relational-databases/security/metadata-visibility-configuration.md)。  

## <a name="see-also"></a>另请参阅  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[SQL 信息保护入门](https://aka.ms/sqlip)
