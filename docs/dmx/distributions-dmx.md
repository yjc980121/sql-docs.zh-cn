---
title: 分布 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fda2eb169985eb670614f611764fbf149c71a42d
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892792"
---
# <a name="distributions-dmx"></a>分布 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  在[!INCLUDE[msCoName](../includes/msconame-md.md)]中[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ,您可以在挖掘结构中定义列的内容,以影响在创建挖掘模型时算法如何处理这些列中的数据。[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对于某些算法，如果已知列中包含常用的值分布，则在处理模型之前定义任意连续列的分布将非常有用。 如果不定义分布，则由于算法据以解释数据的信息较少，生成的挖掘模型产生的预测可能不如定义了分布时产生的预测精确。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] 数据挖掘算法支持下列分布类型：  
  
 **一般**  
 连续列的值构成一个正态高斯分布直方图。  
  
 **Log Normal**  
 连续列的值构成一个直方图，其中值的对数呈正态分布。  
  
 **等**  
 连续列的值构成平坦曲线，曲线上的所有值都具有相同概率。  
  
 有关[!INCLUDE[msCoName](../includes/msconame-md.md)]数据挖掘算法的详细信息, 请参阅[数据挖掘&#40;算法 Analysis Services-数据&#41;挖掘](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)。 第三方算法提供程序可能支持其他分布类型。 若要确定算法支持的分发类型, 请使用**SUPPORTED_DISTRIBUTION_FLAGS**架构行集。  
  
 有关分发类型的详细信息, 请参阅[列&#40;分布数据&#41;挖掘](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining)。  
  
## <a name="see-also"></a>请参阅  
 [内容类型 &#40;数据挖掘&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)   
 [数据挖掘扩展插件 (DMX) 参考](../dmx/data-mining-extensions-dmx-reference.md)   
 [数据挖掘扩展&#40;插件&#41;的 DMX 语法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [数据挖掘扩展&#40;插件&#41; DMX 函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [数据挖掘扩展&#40;插件&#41; DMX 运算符参考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [数据挖掘扩展&#40;插件&#41; DMX 语句参考](../dmx/data-mining-extensions-dmx-statements.md)   
 [数据挖掘扩展&#40;插件&#41;的 DMX 语法约定](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般预测函数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [DMX 预测查询的结构和用法](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 语句](../dmx/understanding-the-dmx-select-statement.md)  
  
  
