---
title: 函数 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f68a66e778d44059a83ca6eca3cee35b4dffca9c
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892767"
---
# <a name="functions-dmx"></a>函数 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  使用数据挖掘扩展插件 (DMX) 在中[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]查询对象时, 您可以使用函数返回比数据挖掘模型或输入数据集中的列中的值更多的信息。 例如，使用 DMX 查询不仅可以返回列的预测值，还可以返回预测正确的概率。 您不仅可以使用 DMX 函数，还可以使用 Microsoft Visual Basic for Applications (VBA)、Microsoft Excel 和存储过程中的函数。  
  
## <a name="dmx-functions"></a>DMX 函数  
 使用 DMX 函数可以执行下列任务：  
  
-   返回预测。  
  
-   返回预测的统计信息，如概率和支持率。  
  
-   筛选查询结果。  
  
-   重新排序表表达式。  
  
 大多数 DMX 函数均返回一个标量值（如对预测的支持率），但有些函数则只返回表格结果。 例如, PredictHistogram 函数返回一个表, 该表包含指定可预测列的每种状态的支持和概率。 结果将在一个新表格列中显示。  
  
 **有关详细信息:** [常规预测函数&#40;dmx&#41;](../dmx/general-prediction-functions-dmx.md),[数据挖掘扩展&#40;插件&#41;函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
## <a name="visual-basic-for-applications-vba-and-excel-functions"></a>Visual Basic for Applications (VBA) 和 Excel 函数  
 除 DMX 函数外，还可以调用 DMX 语句中的各种 VBA 和 Excel 函数。 例如, 可以使用 lCase 函数来修改 TM_Decision_Tree 模型内容中 Attribute_Name 列的显示方式。 如下面的代码示例所示。  
  
```  
SELECT lCase([Attribute_Name])   
FROM [TM_Decision_Tree].CONTENT  
```  
  
 如果 VBA 和 Excel 中同时存在相同的函数, 则必须在 DMX 语句中的函数名称前面加上**vba**或**excel**。 例如，`VBA!Log` 或 `Excel!Log` 两个函数。 如果要使用的 VBA 或 Excel 函数同时存在于 DMX 或多维表达式 (MDX) 中，或者函数中包含美元符号字符 ($)，则必须使用方括号 ([]) 来转义函数。 例如，函数调用将成为 `[VBA!Format]`。  
  
## <a name="stored-procedures"></a>存储过程  
 可以使用公共语言运行时编程语言来创建可以扩展 DMX 功能的存储过程。 例如, 回归树挖掘模型返回描述回归公式的系数, 如 A、B 等, 但模型不返回等式, 如 + Bx = y。 但是，可以编写一个存储过程，使用数据挖掘模型对象来导航内容架构，并将回归公式作为输出结果返回。 因此，DMX 语句可以在查询结果中返回一组回归公式。  
  
 **有关详细信息:** [多维模型程序集管理](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-assemblies-management)  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘扩展插件 (DMX) 参考](../dmx/data-mining-extensions-dmx-reference.md)   
 [数据挖掘扩展&#40;插件&#41; DMX 函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [数据挖掘扩展&#40;插件&#41; DMX 运算符参考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [数据挖掘扩展&#40;插件&#41; DMX 语句参考](../dmx/data-mining-extensions-dmx-statements.md)   
 [数据挖掘扩展&#40;插件&#41;的 DMX 语法约定](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [数据挖掘扩展&#40;插件&#41;的 DMX 语法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般预测函数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [DMX 预测查询的结构和用法](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 语句](../dmx/understanding-the-dmx-select-statement.md)  
  
  
