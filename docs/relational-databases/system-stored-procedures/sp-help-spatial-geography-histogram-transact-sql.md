---
title: sp_help_spatial_geography_histogram (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_histogram_TSQL
- sp_help_spatial_geography_histogram
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_histogram
ms.assetid: 5c5bd319-055d-4cd6-8c5a-06354cc056cc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3c2b94b4c76054fb1e9ce6e078f3490ad263a52c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085194"
---
# <a name="sphelpspatialgeographyhistogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  简化为空间索引键入网格参数的过程。  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_help_spatial_geography_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @sample = ] 'tablesample' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @tabname = ] 'tabname'` 是为其指定空间索引的限定或非限定名称。  
  
 仅当指定了限定表时才需要引号。 如果提供的是完全限定名称（包括数据库名称），则数据库名称必须是当前数据库的名称。 *tabname*是**sysname**，无默认值。  
  
`[ @colname = ] 'columnname'` 是指定的空间列的名称。 *columnname*是**sysname**，无默认值。  
  
`[ @resolution = ] 'resolution'` 是边界框的分辨率。 有效值为 10 到 5000。 *解决方法*是**tinyint**，无默认值。  
  
`[ @sample = ] 'sample'` 是使用表的百分比。 有效的值范围是从 0 到 100。 *tablesample*是**float**。 默认值为 100。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 返回表值。 下面的网格描述表的列内容。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|表示每个单元格，起始计数为 1 的唯一 ID。|  
|**cell**|**地理**|是表示每个单元的矩形多边形。 该单元形状与用于空间索引的单元形状相同。|  
|**row_count**|**bigint**|指示接触或包含单元的空间对象数 。|  
  
## <a name="permissions"></a>权限  
 用户必须是属于**公共**角色。 需要服务器和对象的 READ ACCESS 权限。  
  
## <a name="remarks"></a>备注  
 SSMS 空间选项卡显示结果的图形表示形式。 您可以针对空间窗口查询结果，以获取近似的结果项数。  
  
> [!NOTE]  
>  表中的对象可能涵盖多个单元，因此表中单元之和可能大于实际对象数。  
  
 边界框**geography**类型是整个球体。  
  
## <a name="examples"></a>示例  
 下面的示例调用**sp_help_spatial_geography_histogram**上`Person.Address`表中[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]数据库。  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>请参阅  
 [空间索引存储过程&#40;Transact SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
