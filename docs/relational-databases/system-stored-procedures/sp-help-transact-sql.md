---
title: "sp_help (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help
- sp_help_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help
ms.assetid: 913cd5d4-39a3-4a4b-a926-75ed32878884
caps.latest.revision: "60"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4df2325ef2da29b60ca4f1e7109dd73ff9530ea2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="sphelp-transact-sql"></a>sp_help (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  报告有关数据库对象的信息 (在列出的任何对象**sys.sysobjects**兼容性视图)，用户定义数据类型或数据类型。  
  
 
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_help [ [ @objname = ] 'name' ]  
```  
  
## <a name="arguments"></a>参数  
 [  **@objname=**] *名称*  
 是中的任何对象的名称**sysobjects**中任何用户定义数据类型或**systypes**表。 *名称*是**nvarchar (**776**)**，默认值为 NULL。 不能接受数据库名称。  必须分隔两个或三个部分组成的名称，如 Person.AddressType 或 [Person.AddressType]。   
   
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
 返回的结果集取决于是否*名称*是指定，指定时，并且它是哪些数据库对象。  
  
1.  如果**sp_help**执行不带任何参数，返回的对象的当前数据库中存在的所有类型的摘要信息。  
  
    |列名|数据类型|Description|  
    |-----------------|---------------|-----------------|  
    |**名称**|**nvarchar (**128**)**|对象名称|  
    |**“所有者”**|**nvarchar (**128**)**|对象所有者（拥有对象的数据库主体。 默认为包含对象的架构所有者。）|  
    |**对象类型**|**nvarchar (**31**)**|对象类型|  
  
2.  如果*名称*是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型或用户定义数据类型， **sp_help**返回该结果集。  
  
    |列名|数据类型|Description|  
    |-----------------|---------------|-----------------|  
    |**类型 _ 名称**|**nvarchar (**128**)**|数据类型名称。|  
    |**Storage_type**|**nvarchar (**128**)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型名称。|  
    |**长度**|**int**|数据类型的物理长度（以字节为单位）。|  
    |**Prec**|**int**|精度（数字总位数）。|  
    |**小数位数**|**int**|小数点右侧的数字个数。|  
    |**可以为 Null**|**varchar (**35**)**|指示是否允许 NULL 值：“是”或“否”。|  
    |**Default_name**|**nvarchar (**128**)**|绑定到此类型的默认值的名称。<br /><br /> NULL = 未绑定默认值。|  
    |**Rule_name**|**nvarchar (**128**)**|绑定到此类型的规则的名称。<br /><br /> NULL = 未绑定默认值。|  
    |**排序规则**|**sysname**|数据类型的排序规则。 如果是非字符数据类型，则为 NULL。|  
  
3.  如果*名称*是以外的数据类型，任何数据库对象**sp_help**返回此结果集和也其他结果集，基于指定的对象的类型。  
  
    |列名|数据类型|Description|  
    |-----------------|---------------|-----------------|  
    |**名称**|**nvarchar (**128**)**|表名|  
    |**“所有者”**|**nvarchar (**128**)**|表所有者|  
    |**类型**|**nvarchar (**31**)**|表类型|  
    |**Created_datetime**|**datetime**|表的创建日期|  
  
     根据指定的数据库对象**sp_help**返回额外的结果集。  
  
     如果*名称*是系统表，用户表或视图， **sp_help**返回以下结果集。 但是，不会为视图返回说明数据文件在文件组中位置的结果集。  
  
    -   返回的有关列对象的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**Column_name**|**nvarchar (**128**)**|列名称。|  
        |**类型**|**nvarchar (**128**)**|列数据类型。|  
        |**计算**|**varchar (**35**)**|指示是否计算列中的值：“是”或“否”。|  
        |**长度**|**int**|以字节为单位的列长度。<br /><br /> 注意： 列数据类型是否为较大的值类型 (**varchar （max)**， **nvarchar (max)**， **varbinary （max)**，或**xml**)，将的值显示为-1。|  
        |**Prec**|**char (**5**)**|列精度。|  
        |**小数位数**|**char (**5**)**|列小数位数。|  
        |**可以为 Null**|**varchar (**35**)**|指示是否允许列中包含 NULL 值：“是”或“否”。|  
        |**TrimTrailingBlanks**|**varchar (**35**)**|剪裁尾随空格。 返回 Yes 或 No。|  
        |**FixedLenNullInSource**|**varchar (**35**)**|仅为保持向后兼容。|  
        |**排序规则**|**sysname**|列的排序规则。 对于非字符数据类性为 NULL。|  
  
    -   针对标识列返回的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**标识**|**nvarchar (**128**)**|其数据类型被声明为标识的列名。|  
        |**种子**|**numeric**|标识列的起始值。|  
        |**增量**|**numeric**|用于此列中的值的增量。|  
        |**不用于复制**|**int**|不强制执行标识属性，当复制登录名，如**sqlrepl**，将数据插入到表：<br /><br /> 1 = True<br /><br /> 0 = False|  
  
    -   针对各列返回的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**RowGuidCol**|**sysname**|全局唯一标识符列的名称。|  
  
    -   针对文件组返回的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**Data_located_on_filegroup**|**nvarchar (**128**)**|数据所在的文件组：主要文件组、次要文件组或事务日志文件组。|  
  
    -   针对索引返回的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**index_name**|**sysname**|索引名。|  
        |**Index_description**|**varchar (**210**)**|索引的说明。|  
        |**index_keys**|**nvarchar (**2078年**)**|要生成索引的列的列名。 对于 xVelocity 内存优化的列存储索引返回 NULL。|  
  
    -   针对约束返回的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**constraint_type**|**nvarchar (**146**)**|约束的类型。|  
        |**constraint_name**|**nvarchar (**128**)**|约束名称。|  
        |**delete_action**|**nvarchar (**9**)**|指示 DELETE 操作是 NO_ACTION、CASCADE、SET_NULL、SET_DEFAULT 还是 N/A。<br /><br /> 仅适用于 FOREIGN KEY 约束。|  
        |**update_action**|**nvarchar (**9**)**|指示 UPDATE 操作是 NO_ACTION、CASCADE、SET_NULL、SET_DEFAULT 还是 N/A。<br /><br /> 仅适用于 FOREIGN KEY 约束。|  
        |**status_enabled**|**varchar (**8**)**|指示是否启用约束：Enabled、Disabled 或 N/A。<br /><br /> 仅适用于 CHECK 和 FOREIGN KEY 约束。|  
        |**status_for_replication**|**varchar (**19**)**|指示约束是否用于复制。<br /><br /> 仅适用于 CHECK 和 FOREIGN KEY 约束。|  
        |**constraint_keys**|**nvarchar (**2078年**)**|构成约束的列的名称。对于默认值和规则而言，则为定义默认值或规则的文本。|  
  
    -   针对执行引用的对象返回的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**通过引用表**|**nvarchar (**516**)**|标识引用表的其他数据库对象。|  
  
    -   针对存储过程、函数或扩展存储过程返回的其他结果集：  
  
        |列名|数据类型|Description|  
        |-----------------|---------------|-----------------|  
        |**Parameter_name**|**nvarchar (**128**)**|存储过程参数名。|  
        |**类型**|**nvarchar (**128**)**|存储过程参数的数据类型。|  
        |**长度**|**int**|最大物理存储长度（以字节为单位）。|  
        |**Prec**|**int**|精度，即数字总位数。|  
        |**小数位数**|**int**|小数点右边的数字位数。|  
        |**Param_order**|**int**|参数的顺序。|  
  
## <a name="remarks"></a>注释  
 **Sp_help**过程查找当前数据库中的对象。  
  
 当*名称*未指定， **sp_help**列表对象名称、 所有者和当前数据库中的所有对象的对象类型。 **sp_helptrigger**提供有关触发器的信息。  
  
 **sp_help**公开仅可排序的索引列; 因此，它不公开有关 XML 索引或空间索引的信息。  
  
## <a name="permissions"></a>Permissions  
 要求 **公共** 角色具有成员身份。 用户必须具有至少一个权限*objname*。 若要查看列约束键、默认值或规则，必须对表具有 VIEW DEFINITION 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-information-about-all-objects"></a>A. 返回有关所有对象的信息  
 以下示例将列出有关 `master` 数据库中每个对象的信息。  
  
```  
USE master;  
GO  
EXEC sp_help;  
GO  
```  
  
### <a name="b-returning-information-about-a-single-object"></a>B. 返回有关单个对象的信息  
 以下示例将显示有关 `Person` 表的信息。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help 'Person.Person';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据库引擎存储过程 &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpindex &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)   
 [sp_helprotect &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helptrigger (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helpuser &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sysobjects &#40;Transact SQL &#41;](../../relational-databases/system-compatibility-views/sys-sysobjects-transact-sql.md)  
  
  