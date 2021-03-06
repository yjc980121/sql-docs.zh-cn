---
title: 在报表生成器中预览报表 | Microsoft Docs
ms.date: 01/09/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 36c1c3172e4d37963340fdbebce85eff9b5086b9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65580717"
---
# <a name="previewing-reports-in-report-builder"></a>在报表生成器中预览报表
  当创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 分页报表时，经常预览报表以验证报表显示你所需的内容会非常有用。 若要预览报表，请单击 **“运行”** 。 报表将在预览模式下呈现。  
  
 报表生成器通过在连接到报表服务器时使用编辑会话改进了预览体验。 编辑会话创建数据缓存，并使缓存中的数据集可用于重复性的报表预览。 编辑会话并不是一种您可以直接与之交互的功能，但了解何时刷新缓存的数据集将帮助您改进预览报表时的性能并理解报表呈现变快或变慢的原因。  
  
 编辑会话的其他优点包括可以编辑使用嵌入数据源或引用项（如存储在报表服务器上的图像或子报表）的报表。  
  
> [!NOTE]  
> 在报表生成器中预览与在浏览器中查看有一些差异。 例如，在指定日期/时间类型参数时添加到报表中的日历控件与报表生成器和浏览器中的日历控件有所不同。 
  
## <a name="improving-preview-performance"></a>改进预览性能  
 您创建和更新报表的方式影响报表在预览中呈现的速度。 当您首次预览依赖于服务器引用的报表时，将为您创建一个编辑会话，并且将在报表运行时使用的数据添加到存储在报表服务器上的数据缓存中。 当您对报表进行不影响数据的更改时，报表将使用数据的缓存副本。 这意味着，您每次预览报表时将看不到数据更改。 如果您需要新数据，请单击功能区上的 **“刷新”** 按钮。  
  
 下面的操作会导致刷新缓存，并减慢您下一次预览报表时的报表呈现速度。  
  
-   添加、更改或删除数据集。 缓存的数据集包含报表使用的所有数据集，对任何数据集进行修改都会使缓存的数据集变为无效。 这包括在数据集中更改名称、查询或字段。  
  
    > [!NOTE]  
    >  如果数据集包含大量您预期不会使用的字段，则应考虑更新数据集以忽略这些字段。 尽管这会创建新的编辑会话并且报表的第一次预览将变慢，但缓存数据集较小对于报表服务器的性能而言总体上是有利的。  
  
-   添加、更改或删除数据源。 这包括更改数据源的名称或属性、数据源的数据扩展或与数据源的连接的属性。  
  
-   将报表使用的共享数据源更改为其他数据源。  
  
-   更改报表的语言。  
  
-   更改报表使用的程序集或自定义代码。  
  
-   添加、更改或删除报表中的查询参数或参数值。  
  
 对于报表布局和数据格式的更改不影响缓存的数据集。 您可以执行以下操作，而不刷新缓存的数据集：  
  
-   添加或删除数据区域，例如表、矩阵或图表。  
  
-   在报表中添加或删除列。 数据集中的所有字段均可用于报表中。 在报表中添加或删除字段对数据集没有任何影响。  
  
-   更改表和矩阵中的字段顺序。  
  
-   添加、更改或删除行组和列组。  
  
-   添加、更改或删除字段中数据值的格式。  
  
-   添加、更改或删除图像、线条或文本框。  
  
-   更改分页符。  
  
 您首次预览报表时，将创建编辑会话。 默认情况下，编辑会话持续 7200 秒（2 小时）。 每次运行报表时，此会话重置为两小时。 当编辑会话到期时，将删除数据缓存。 如果编辑会话到期，当您下一次预览报表时，将自动再次创建一个编辑会话。 可以配置编辑会话的到期时间。 如果您发现两个小时过长或过短，则与报表服务器管理员联系。  
  
 默认情况下，数据缓存可以容纳多达五个数据集。 如果您使用参数值的多种不同组合，则报表可能需要更多数据。 这要求刷新缓存，并且当您下一次预览报表时，报表呈现将变慢。 缓存中的条目数可以由报表服务器的管理员进行配置。  
  
## <a name="concurrency-of-report-updates"></a>报表更新的并发性  
 您经常将预览报表作为更新报表而后将其保存到报表服务器的过程的一个步骤。 当您更新报表时，可能其他人同时正在更新和保存报表。 最后保存的报表是可供将来查看和更新的报表版本。 这意味着您预览的报表版本可能并不是您重新打开的版本。 您可以使用“报表生成器”菜单上的 **“另存为”** 选项，选择使用新名称来保存报表。  
  
## <a name="external-report-items"></a>外部报表项  
 报表可能包含诸如与报表分开存储的共享数据源、外部图像以及子报表等此类项。 由于项是单独存储的，因此，可能可以将它们移到报表服务器上的不同位置或删除它们。 如果发生这种情况，则报表可能无法预览。 您可以更新报表以指示更新后的项位置，或者，如果删除了项，则将其替换为现有项，或者从报表中删除对于该项的引用。  
  
 如果在创建编辑会话之后更改报表使用的子报表，报表将不呈现在预览中。 若要成功预览报表，应保存该报表并单击 **“刷新”** 以获取新数据。  
  
## <a name="see-also"></a>另请参阅  
 [报表数据集 (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [设置报表项的格式（报表生成器和 SSRS）](../../reporting-services/report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [表、矩阵和列表（报表生成器和 SSRS）](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [图表（报表生成器和 SSRS）](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [表、矩阵和列表（报表生成器和 SSRS）](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [保存报表（报表生成器）](../../reporting-services/report-builder/saving-reports-report-builder.md)  
  
  
