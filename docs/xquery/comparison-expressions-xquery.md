---
title: 比较表达式 (XQuery) |Microsoft 文档
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- node comparison operators [XQuery]
- comparison expressions [XQuery]
- node order comparison operators [XQuery]
- expressions [XQuery], comparison
- comparison operators [XQuery]
- value comparison operators
ms.assetid: dc671348-306f-48ef-9e6e-81fc3c7260a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 7462e089f70b4da76edea25dcfe6e7e314ad7c46
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039028"
---
# <a name="comparison-expressions-xquery"></a>比较表达式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XQuery 提供了下列类型的比较运算符：  
  
-   常规比较运算符  
  
-   值比较运算符  
  
-   节点比较运算符  
  
-   节点顺序比较运算符  
  
## <a name="general-comparison-operators"></a>常规比较运算符  
 常规比较运算符可用于比较原子值、序列或二者的任意组合。  
  
 下表中定义了常规运算符。  
  
|运算符|描述|  
|--------------|-----------------|  
|=|等于|  
|!=|不等于|  
|\<|小于|  
|>|大于|  
|\<=|小于或等于|  
|>=|大于或等于|  
  
 使用常规比较运算符比较两个序列时，如果第二个序列中存在某个值与第一个序列中的某个值比较结果为 True，则整个结果为 True。 否则，它为 False。 例如，(1, 2, 3) = (3, 4) 为 True，因为值 3 同时出现在两个序列中。  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2,3) = (3,4)')    
```  
  
 若要进行比较，值应是可比较的类型。 具体来说，对这些值是进行静态检查的。 对于数值比较，可能会出现数值类型提升。 例如，如果对十进制值 10 与双精度值 1e1 进行比较，则将十进制值更改为双精度值。 注意，由于双精度比较不可能很精确，因此得到的结果并不精确。  
  
 如果其中一个值是非类型化的，则将其转换为另一个值的类型。 在下面的示例中，将值 7 视为一个整数。 在进行比较之前，将非类型化值 /a[1] 转换为一个整数。 该整数比较返回 True。  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < 7')  
```  
  
 相反，如果将非类型化值与字符串或其他非类型化值进行比较，则将其转换为 xs:string。 在下面的查询中，对字符串 6 与字符串“17”进行比较。 因为是字符串比较，所以下面的查询返回 False。  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < "17"')  
```  
  
 下面的查询从 AdventureWorks 示例数据库中提供的产品目录中返回某个产品型号的小尺寸图片。 该查询将 `PD:ProductDescription/PD:Picture/PD:Size` 返回的一组原子值与一个单一序列“small”进行比较。 如果比较结果为 True，它将返回 < 图片\>元素。  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
SELECT CatalogDescription.query('         
    for $P in /PD:ProductDescription/PD:Picture[PD:Size = "small"]         
    return $P') as Result         
FROM   Production.ProductModel         
WHERE  ProductModelID=19         
```  
  
 以下查询将进行比较的序列中的电话号码 < 数\>字符串文字"112-111-1111"的元素。 该查询对 AdditionalContactInfo 列中的一组电话号码元素进行比较，以确定文档中是否存在某个特定客户的特定电话号码。  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.value('         
   /aci:AdditionalContactInfo//act:telephoneNumber/act:number = "112-111-1111"', 'nvarchar(10)') as Result         
FROM Person.Contact         
WHERE ContactID=1         
```  
  
 该查询返回 True。 这表示文档中存在相应号码。 下面的查询只对上面的查询稍微做了修改。 在此查询中，将从文档中检索的电话号码值与包含两个电话号码值的组进行比较。 如果比较结果为 True，< 数\>返回元素。  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.query('         
  if (/aci:AdditionalContactInfo//act:telephoneNumber/act:number = ("222-222-2222","112-111-1111"))         
  then          
     /aci:AdditionalContactInfo//act:telephoneNumber/act:number         
  else         
    ()') as Result         
FROM Person.Contact         
WHERE ContactID=1  
  
```  
  
 下面是结果：  
  
```  
\<act:number   
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
    111-111-1111  
\</act:number>  
\<act:number   
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
    112-111-1111  
\</act:number>   
```  
  
## <a name="value-comparison-operators"></a>值比较运算符  
 值比较运算符用于比较原子值。 注意，在查询中可以使用常规比较运算符来代替值比较运算符。  
  
 下表中定义了值比较运算符。  
  
|运算符|描述|  
|--------------|-----------------|  
|eq|等于|  
|ne|不等于|  
|lt|小于|  
|gt|大于|  
|le|小于或等于|  
|ge|大于或等于|  
  
 如果根据所选的运算符两个值的比较结果相同，则表达式将返回 True。 否则将返回 False。 如果其中任何一个值是空序列，则表达式的结果为 False。  
  
 这些运算符只适用于单一原子值。 也就是说，不能将一个序列指定为其中一个操作数。  
  
 例如，以下查询将检索\<图片 > 针对某个产品型号图片的大小是其中的元素"小：  
  
```  
SELECT CatalogDescription.query('         
              declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";         
              for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]         
              return         
                    $P         
             ') as Result         
FROM Production.ProductModel         
WHERE ProductModelID=19         
```  
  
 请注意上述查询的以下方面：  
  
-   `declare namespace` 定义在随后的查询中使用的命名空间前缀。  
  
-   \<大小 > 元素值与指定的原子值"small"进行比较。  
  
-   请注意，由于值运算符只适用于原子值**data （)** 函数隐式用于检索节点值。 也就是说，`data($P/PD:Size) eq "small"` 生成相同的结果。  
  
 下面是结果：  
  
```  
\<PD:Picture   
  xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  \<PD:Angle>front\</PD:Angle>  
  \<PD:Size>small\</PD:Size>  
  \<PD:ProductPhotoID>31\</PD:ProductPhotoID>  
\</PD:Picture>  
```  
  
 注意，用于值比较的类型提升规则与用于常规比较的类型提升规则相同。 另外，在值比较过程中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对非类型化值使用的转换规则与它在常规比较过程中使用的转换规则相同。 而 XQuery 规范中的规则是，在值比较过程中总是将非类型化值转换为 xs:string。  
  
## <a name="node-comparison-operator"></a>节点比较运算符  
 节点比较运算符**是**，仅适用于节点类型。 它返回的结果表明作为操作数传入的两个节点是否表示源文档中的同一节点。 如果两个操作数是同一节点，则此运算符返回 True。 否则，它返回 False。  
  
 下面的查询检查在某个特定产品型号的生产过程中生产车间 10 是否排在第一位。  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' AS AWMI)  
  
SELECT ProductModelID, Instructions.query('         
    if (  (//AWMI:root/AWMI:Location[@LocationID=10])[1]         
          is          
          (//AWMI:root/AWMI:Location[1])[1] )          
    then         
          <Result>equal</Result>         
    else         
          <Result>Not-equal</Result>         
         ') as Result         
FROM Production.ProductModel         
WHERE ProductModelID=7           
```  
  
 下面是结果：  
  
```  
ProductModelID       Result          
-------------- --------------------------  
7              <Result>equal</Result>      
```  
  
## <a name="node-order-comparison-operators"></a>节点顺序比较运算符  
 节点顺序比较运算符根据节点在文档中的位置来比较节点对。  
  
 下面是根据文档顺序所做的比较：  
  
-   `<<` :Does**操作数 1**前加上**操作数 2**按文档顺序。  
  
-   `>>` :Does**操作数 1**按照**操作数 2**按文档顺序。  
  
 下面的查询返回 True，如果产品目录说明\<担保 > 元素之前出现\<维护 > 某一特定产品的文档顺序中的元素。  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM)  
  
SELECT CatalogDescription.value('  
     (/PD:ProductDescription/PD:Features/WM:Warranty)[1] <<   
           (/PD:ProductDescription/PD:Features/WM:Maintenance)[1]', 'nvarchar(10)') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 请注意上述查询的以下方面：  
  
-   **Value （)** 方法**xml**查询中使用数据类型。  
  
-   查询的布尔值结果转换为**nvarchar(10)** 和返回。  
  
-   该查询返回 True。  
  
## <a name="see-also"></a>请参阅  
 [类型系统&#40;XQuery&#41;](../xquery/type-system-xquery.md)   
 [XQuery 表达式](../xquery/xquery-expressions.md)  
  
  
