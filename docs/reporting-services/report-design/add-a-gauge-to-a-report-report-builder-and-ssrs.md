---
title: 向报表添加仪表（报表生成器和 SSRS）| Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 45da4fef-2b02-40e1-977c-f8f80d87155e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9b5c1a9989831e6c28cd2aecd58a3e9f8640465c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65575020"
---
# <a name="add-a-gauge-to-a-report-report-builder-and-ssrs"></a>向报表添加仪表（报表生成器和 SSRS）
  在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 分页报表中，如果要以可视化格式汇总数据，则可使用仪表数据区域。 将仪表数据区域添加到设计图面后，可以将报表数据集字段拖到仪表的数据窗格中。  
  
## <a name="to-add-a-gauge-to-your-report"></a>向报表添加仪表  
  
1.  创建一个报表或打开现有报表。  
  
2.  在“插入”选项卡上，双击“仪表”。 **“选择仪表类型”** 对话框即会打开。  
  
3.  选择要添加的仪表类型。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  与图表不同的是，仪表只有两个类型：线性和径向。 **“选择仪表类型”** 对话框中的可用仪表是这两类仪表的模板。 因此，在将仪表添加到报表后不能更改仪表类型。 必须通过删除并重新添加仪表来更改仪表类型。  
  
     如果报表没有数据源和数据集，则 **“数据源属性”** 对话框即会打开并引导您完成创建数据源和数据集的步骤。 有关详细信息，请参阅[添加和验证数据连接（报表生成器和 SSRS）](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)。  
  
     如果报表具有数据源但没有数据集，则 **“数据集属性”** 对话框即会打开并引导您完成创建一个数据集的步骤。 有关详细信息，请参阅 [创建共享数据集或嵌入数据集（报表生成器和 SSRS）](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)。  
  
4.  单击仪表以显示数据窗格。 默认情况下，仪表的指针和值一一对应。 您可以添加其他指针。  
  
5.  将数据集中的一个字段添加到数据字段放置区。 您只能添加一个字段。 如果要显示多个字段，必须添加其他指针，每个字段一个指针。  
  
     右键单击仪表刻度，然后选择“刻度属性”  。 为刻度的 **“最小值”** 和 **“最大值”** 分别键入一个值。 有关详细信息，请参阅[设置仪表的最小值或最大值（报表生成器和 SSRS）](../../reporting-services/report-design/set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)。  
  
## <a name="see-also"></a>另请参阅  
 [嵌套数据区域（报表生成器和 SSRS）](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md)   
 [仪表（报表生成器和 SSRS）](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  
