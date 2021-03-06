---
title: 第 3 课：生成市场篮方案 （数据挖掘中级教程） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c2f1c5a8ae897284f07c3fd6c65d9735099a41fa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042781"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a>第 3 课：生成市场篮方案 （数据挖掘中级教程）
  [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 市场部希望改进公司的网站以促进跨区销售。 作为网站更新的一部分，他们希望能够根据客户的在线购物篮中已有的其他产品来预测客户可能要购买的产品。 市场部还希望更好的了解客户购买行为，以便他们能够将网站设计为将可能被集中购买的项统一放置在一个位置上。 他们已经了解数据挖掘对于此类“  市场蓝分析”尤其有用，并已经请您来开发一个数据挖掘模型。  
  
 在完成本课中的任务之后，您还会获得一个可显示客户历史交易中的商品分组的完整挖掘模型。 另外，您可以使用挖掘模型来预测客户可能希望购买的其他产品。  
  
 若要完成本课程中的任务，将使用的第一课中创建的解决方案和数据源[数据挖掘中级教程&#40;Analysis Services-数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)。 您将通过添加一个数据源视图并在该视图中包含多个有关客户的表（包括客户购买情况的嵌套表）来修改此解决方案。  随后，您将生成一个使用 Microsoft 关联规则算法的挖掘模型，该模型适于市场篮方案。  
  
 本课程包含以下主题：  
  
-   [添加数据源视图使用嵌套表&#40;数据挖掘中级教程&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [创建市场篮结构和模型&#40;数据挖掘中级教程&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [修改和处理市场篮模型&#40;数据挖掘中级教程&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [浏览市场篮模型&#40;数据挖掘中级教程&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [筛选挖掘模型中的嵌套的表&#40;数据挖掘中级教程&#41;](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [预测关联&#40;数据挖掘中级教程&#41;](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>课程中的下一个任务  
 [添加数据源视图使用嵌套表&#40;数据挖掘中级教程&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>所有课程  
 [第 1 课：创建中级数据挖掘解决方案&#40;数据挖掘中级教程&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [第 2 课：生成预测方案&#40;数据挖掘中级教程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 第 3 课：市场篮方案 （数据挖掘中级教程）  
  
 [第 4 课：生成顺序聚类分析方案&#40;数据挖掘中级教程&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [第 5 课：生成神经网络模型和逻辑回归模型&#40;数据挖掘中级教程&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [第 2 课：生成预测方案&#40;数据挖掘中级教程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)   
 [第 4 课：生成顺序聚类分析方案&#40;数据挖掘中级教程&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
