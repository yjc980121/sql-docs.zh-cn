---
title: 浏览预测模型 （数据挖掘中级教程） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 607f300fbf2138796bb02c66c62386fcc93e6a45
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62992273"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a>浏览预测模型（数据挖掘中级教程）
  既然您已经生成预测的挖掘模型，您可以通过使用浏览结果**挖掘模型查看器**数据挖掘设计器选项卡。 [!INCLUDE[msCoName](../includes/msconame-md.md)]时序查看器包含两个选项卡：**图表**并**模型**。  
  
 此外，您可以对所有模型使用 Microsoft 一般内容树查看器。 每个视图都显示时序模型中稍有不同的信息概览。  
  
-   [图表选项卡](#bkmk_Charts)  
  
-   [模型选项卡](#bkmk_Model)  
  
-   [Microsoft 一般内容查看器](#bkmk_Content)  
  
##  <a name="bkmk_Charts"></a> 图表选项卡  
 **图表**选项卡[!INCLUDE[msCoName](../includes/msconame-md.md)]时序查看器以图形方式显示各个序列，包括历史数据和预测。 时序图中的每条线都代表产品、区域和可预测属性的一种唯一组合。  
  
 该查看器右侧的图例列出根据下拉列表中的所选内容提供的时序。 您可以选中和清除图例中的复选框，以便控制图形中显示的时序。  
  
 还可以更改显示选项，例如用于每个时序的颜色或是否在图表中的点显示值。  
  
#### <a name="to-select-a-time-series"></a>选择时序  
  
1.  单击**图表**选项卡**挖掘模型查看器**选项卡上，如果不可见。  
  
2.  单击图表视图右侧的下拉列表，选中所有复选框。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     图表现在应包含 24 条不同的序列线。  
  
3.  在图表右侧的复选框中取消选中响应的框，以临时隐藏基于 Amount 的所有序列线。  
  
     然后，取消选中与 R750 和 R250 自行车有关的复选框。  
  
     现在，图表仅包含以下 6 条序列线，因此您可以更方便地比较 M200 和 T1000 自行车的趋势。  
  
    -   **M200 Europe:数量**  
  
    -   **M200 North America:数量**  
  
    -   **M200 Pacific:数量**  
  
    -   **T1000 Europe:数量**  
  
    -   **T1000 North America:数量**  
  
    -   **T1000 Pacific:数量**  
  
 ![时序预测 M200 和 T1000 数量](../../2014/tutorials/media/6series-defaultforecasting.gif "时序预测 M200 和 T1000 数量")  
  
 在此查看器中显示的图表包括历史数据和预测数据。 预测数据带有底纹，以便与历史数据区分开。 为了方便比较不同的序列，您还可以更改与图形中每条线关联的颜色。 有关详细信息，请参阅 [更改数据挖掘查看器中使用的颜色](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md)。  
  
 从趋势线可以看出：所有区域的总销售额在普遍增长，并且每 12 个月（在 12 月）出现一次峰值。 通过图表，您还可以发现 T1000 自行车数据的开始时间比其他产品序列数据的开始时间晚得多。 这是因为这是一个较新的产品，但由于此序列基于的数据要少得多，预测的准确性可能相对较低。  
  
 默认情况下，将为每个时序显示以虚线表示的五个预测步骤。 您可以更改此值以查看更多或更少的预测。 可以通过向图表添加误差线还以图形方式查看预测标准偏差。  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a>更改“图表”视图中的预测和显示选项  
  
1.  请尝试更改的值**预测步骤**逐渐，增加从**5**到**10**，然后回到**6**。  
  
     如果历史数据具有较大波动，则随着您增大预测次数，波动会重复出现甚至被放大。 此时您可能需要进行一些研究，了解历史数据出现较大增长的原因，然后决定是否接受这些结果，尝试在源数据中进行某种更正，或是对模型应用某种平滑处理。  
  
2.  选择**显示偏差**复选框。  
  
     此选项显示每个预测值的预估误差。  
  
3.  请注意 X 轴的刻度。 历史和预测数据的更改始终表示为百分比，但实际值将被自动调整，以便所有值都能显示在图形中。 因此，在比较模型时务须小心，不要仅依赖于可见值。 若要获取确切值或百分比增长和预测值，将鼠标悬停在虚线或实线上方，或单击要查看中的值中的行**挖掘图例**。  
  
     **提示**：如果**挖掘图例**不可见，请切换到**模型**查看，右键单击任意节点，然后选择**显示图例**。  
  
 通过观察这些趋势，您会担心某些序列缺少数据，并想知道是否可以通过按模型（或者可能按地区）计算销售额的平均值来获取更可靠的预测。 本教程后面的课程中将探讨这种方法。  
  
 [返回页首](#bkmk_Charts)  
  
##  <a name="bkmk_Model"></a> 模型选项卡  
 **模型**选项卡[!INCLUDE[msCoName](../includes/msconame-md.md)]时序查看器在数据挖掘设计器中，可查看预测模型的树关系图的窗体。  
  
 首先请注意，由于您的数据描述三个不同地区（欧洲、北美和太平洋地区）多个产品系列销售情况的两个不同的度量值（“金额”和“数量”），您所构建的模型实际包含 24 个不同的树，每个树表示由不同的地区、产品和可预测属性组合而成的销售模式的一个模型。  
  
 您可以选择的产品系列、 区域和你想要查看通过选择从一系列销售度量值的组合**树**上的下拉列表**模型**选项卡。  
  
 那么，您可以从查看树形模型中学习到什么？ 例如，让我们来比较两个模型，一个具有在树中，多个级别，一个具有单个节点。  
  
-   当树形图包含单个节点时，这表示在模型中发现的趋势基本上随时间发生同质变化。 可以使用这一单个节点，标有**所有**、 查看描述输入的变量和结果之间的关系的公式。  
  
-   如果某一时序的树形图包含多个分支，这表示检测到的时序太过复杂，无法表示为单个公式。 相反，树形图可能包含多个分支，每个分支标记有导致树的条件*拆分*。 当树拆分时，每个分支表示不同的时间段，这些时间段内的趋势可描述为单个公式。  
  
     例如，如果您看看图表图形并查看在启动一段时间内年 9 月中且一直持续到年底假期的销售量突然跳转，您可以切换到**模型**视图，以查看趋势发生的确切日期。 表示"九月前"和"九月后"树中的分支将包含不同的公式： 一个公式用算术方法描述截至拆分的销售趋势和另一个公式描述通过 9 月的销售趋势年底假期。  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a>浏览时序模型的决策树  
  
1.  在中**树**上列出**模型**选项卡的查看器中，选择**T1000 Europe:量**系列。  
  
     单击标记为节点**所有**。  
  
     有关**所有**节点，显示的工具提示在整个系列中，包括信息，如事例数和时序公式派生自数据分析。  
  
2.  如果**挖掘图例**不可见，请右键单击节点，然后选择**显示图例**。  
  
     **挖掘图例**提供的信息基本相同的工具提示。 如有任何自变量为离散变量，您还会看到一个直方图，其中显示变量在节点中的分布。  
  
3.  现在选择其他要查看的时序。 使用**树**上列出**模型**选项卡的查看器中，选择**M200 North America:量**系列。  
  
     树图形现在包含**所有**节点和两个子节点。 通过观察子节点上的标签，您可以发现趋势线在哪一点上发生了变化。  
  
     对于每个子节点中的说明**挖掘图例**还树的每个分支中包括的事例的计数。  
  
 下面的列表描述了树查看器中的其他一些功能：  
  
-   你可以通过使用图表中表示的变量**背景**控件。 默认情况下，较暗的节点包含更多用例，因为值**背景**设置为**填充**。 若要查看只需用例有有多少节点中，将鼠标悬停在某个节点并查看工具提示的出现，或单击该节点，然后查看中的数字**节点图例**窗口。  
  
-   还可以在工具提示中（或通过单击该节点）查看该节点的回归公式。 如果创建了混合模型，则会看到两个公式：一个用于 ARTXP（在叶节点中），一个用于 ARIMA（在树的根节点中）。  
  
-   节点中使用多个小菱形来表示连续数值。 菱形所在的条形中会显示属性的范围。 菱形在节点均值处居中显示，其宽度表示该节点处属性的方差。  
  
 [返回页首](#bkmk_Charts)  
  
##  <a name="bkmk_Content"></a> （可选）一般内容树查看器  
 除了时序的自定义查看器[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]提供了**MicrosoftGeneric 内容树查看器**以用于所有数据挖掘模型。 此查看器具有以下优点：  
  
-   **Microsoft 时序查看器**:此视图合并两个算法的结果。 尽管您可以分别查看每个序列，但您无法确定每种算法的结果是如何合并的。 此外，在此视图中，工具提示和挖掘图例只显示最重要的统计数据。  
  
-   **一般内容树查看器**:可以浏览，然后查看所使用的数据序列的所有模型中的一次和如果创建了混合模型，这两个 ARIMA 和 ARTXP 树同一图表中显示。  
  
     您可以使用此查看器获取两种算法的所有统计数据以及这些值的分布。  
  
     对于要深入了解 ARIMA 和 ARTXP 分析结果的数据挖掘专家级用户，推荐使用此查看器。  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a>在一般内容查看器中查看特定数据序列的详细信息  
  
1.  在中**挖掘模型查看器**选项卡上，选择**Microsoft 一般内容树查看器**从**查看器**下拉列表。  
  
2.  在中**节点标题**窗格中，单击最顶部的 （全部） 节点。  
  
3.  在中**节点的详细信息**窗格中，查看 ATTRIBUTE_NAME 的值。  
  
     此值会显示该节点中包含哪个序列或产品和区域的哪个组合。 在 AdventureWorks 示例中，最顶部的节点是 M200 Europe 序列的节点。  
  
4.  在中**节点标题**窗格中，找到具有子节点的第一个节点。  
  
     如果某个序列节点有子级，树视图上显示**模型**Microsoft 时序查看器选项卡也有一个分支结构。  
  
5.  展开该节点，然后单击某个子节点。  
  
     架构的 NODE_DESCRIPTION 列包含导致树拆分的条件。  
  
6.  在中**节点标题**窗格中，单击最顶部的 ARIMA 节点，并展开节点，直到所有子节点都都可见。  
  
7.  在中**节点的详细信息**窗格中，查看 ATTRIBUTE_NAME 的值。  
  
     此值会指出该节点中包含哪个时序。 ARIMA 部分中最顶部的节点应该与（“全部”）部分中最顶部的节点相匹配。 在 AdventureWorks 示例中，该节点包含序列 M200 Europe 的 ARIMA 分析。  
  
 有关详细信息，请参阅[时序模型的挖掘模型内容](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)。  
  
 [返回页首](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a>课程中的下一个任务  
 [创建时序预测&#40;数据挖掘中级教程&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>请参阅  
 [时序模型查询示例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Microsoft 时序算法技术参考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
