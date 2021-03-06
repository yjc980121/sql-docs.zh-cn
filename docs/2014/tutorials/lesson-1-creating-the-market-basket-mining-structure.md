---
title: 第 1 课：创建市场篮挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62676275"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>第 1 课：创建市场篮挖掘模型
  在本课中，将创建一个挖掘模型，可以使用该模型预测客户要同时购买的 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 产品。 如果您不熟悉挖掘结构和数据挖掘中的其角色，请参阅[挖掘结构&#40;Analysis Services-数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)。  
  
 将在本课程中创建的关联挖掘结构支持添加挖掘模型基于[Microsoft 关联算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)。 在后面的课程中，您将使用挖掘模型来预测客户要同时购买的产品类型，这称为市场篮分析。 例如，您可能会发现客户要同时购买山地自行车、自行车轮胎和头盔。  
  
 在本课中，挖掘结构是使用嵌套表定义的。 使用嵌套表是因为将由结构定义的数据域分别包含在两个不同的源表中。 有关嵌套表的详细信息，请参阅[嵌套表&#40;Analysis Services-数据挖掘&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)。  
  
## <a name="create-mining-structure-statement"></a>创建挖掘结构语句  
 若要创建挖掘结构包含嵌套的表，则使用[CREATE MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/create-mining-structure-dmx)语句。 可以将语句中的代码分为下列几部分：  
  
-   命名结构  
  
-   定义键列  
  
-   定义挖掘列  
  
-   定义嵌套表列  
  
 下面是 CREATE MINING STRUCTURE 语句的一般示例：  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 代码的第一行定义了结构的名称：  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 有关命名 DMX 中的对象的信息，请参阅[标识符&#40;DMX&#41;](/sql/dmx/identifiers-dmx)。  
  
 代码的下一行定义了挖掘结构的键列，它唯一标识源数据中的实体：  
  
```  
<key column>  
```  
  
 代码的下一行用于定义与挖掘结构关联的挖掘模型所使用的挖掘列：  
  
```  
<mining structure columns>  
```  
  
 代码中接下来几行定义了嵌套表列：  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 有关挖掘结构列可以定义的类型的信息，请参阅[挖掘结构列](../../2014/analysis-services/data-mining/mining-structure-columns.md)。  
  
> [!NOTE]  
>  默认情况下，[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 为每个挖掘结构创建 30% 的维持数据集；但是，如果使用 DMX 创建挖掘结构，则必须手动添加维持数据集（如果需要）。  
  
## <a name="lesson-tasks"></a>课程任务  
 在本课程中，将执行以下任务：  
  
-   创建新的空白查询  
  
-   更改查询以创建挖掘结构  
  
-   执行查询  
  
## <a name="creating-the-query"></a>创建查询  
 第一步是连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例，并在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中创建一个新的 DMX 查询。  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>在 SQL Server Management Studio 中创建一个新的 DMX 查询  
  
1.  打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。  
  
2.  在中**连接到服务器**对话框中，对于**服务器类型**，选择**Analysis Services**。 在中**服务器名称**，类型`LocalHost`，或实例的名称[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]想要连接到本课程中。 单击 **“连接”** 。  
  
3.  在中**对象资源管理器**，右键单击该实例的[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，依次指向**新查询**，然后单击**DMX**。  
  
     将打开查询编辑器，其中包含一个新的空白查询。  
  
## <a name="altering-the-query"></a>更改查询  
 下一步是修改上述 CREATE MINING STRUCTURE 语句以创建市场篮挖掘结构。  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>自定义 CREATE MINING STRUCTURE 语句  
  
1.  在查询编辑器中，将 CREATE MINING STRUCTURE 语句的一般示例复制到空白查询。  
  
2.  将  
  
    ```  
    [mining structure name]   
    ```  
  
     使用：  
  
    ```  
    [Market Basket]  
    ```  
  
3.  将  
  
    ```  
    <key column>  
    ```  
  
     使用：  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  将  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     使用：  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     TEXT KEY 语言指定 Model 列为嵌套表的键列。  
  
     现在，完整的挖掘结构语句应该如下所示：  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  上**文件**菜单上，单击**另存 dmxquery1.dmx 另存为**。  
  
6.  在中**另存为**对话框中，浏览到相应的文件夹，并将文件命名`Market Basket Structure.dmx`。  
  
## <a name="executing-the-query"></a>执行查询  
 最后一步是执行查询。 创建并保存查询后，需要执行该查询（即，需要执行该语句）以便在服务器中创建挖掘结构。 有关在查询编辑器中执行查询的详细信息，请参阅[数据库引擎查询编辑器&#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)。  
  
#### <a name="to-execute-the-query"></a>若要执行查询  
  
-   在查询编辑器中，在工具栏上，单击**Execute**。  
  
     查询的状态显示在**消息**在底部的查询编辑器执行完语句后的选项卡。 所显示的消息应为：  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     名为的新结构**市场篮**现在服务器上是否存在。  
  
 在下一课中，您将向刚才创建的市场篮挖掘结构中添加挖掘模型。  
  
## <a name="next-lesson"></a>下一课  
 [第 2 课：向市场篮挖掘结构添加挖掘模型](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
