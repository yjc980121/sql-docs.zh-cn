---
title: 正在加载数据 (MDS add-in for Excel) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3bbd3ac1bf97530d64760d1434b9e7e8f6a81d34
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65482804"
---
# <a name="loading-data-mds-add-in-for-excel"></a>加载数据（用于 Excel 的 MDS 外接程序）
  在中[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]，您必须加载数据从 MDS 存储库到 Excel 活动工作表之前您可以使用它。 完成数据处理后，将其发布到 MDS 存储库以便其他用户可以共享这些数据。  
  
 您可以加载的数据仅限于您具有访问权限的数据。 访问数据的权限是在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序中或以编程方式设置的。  
  
 加载大量数据时，您可以设置在数据可能需要较长时间加载时显示警告。 若要执行此操作，请在 **“选项”** 组中单击 **“设置”** 。 在 **“数据”** 选项卡上，选择 **“显示针对大型数据集的筛选警告”** 。  
  
> [!WARNING]  
>  只能使用用于 Excel 的 MDS 外接程序在 Excel 中打开和更新启用 MDS 的工作薄。 不支持在未安装 MDS Excel 外接程序的计算机上的 Excel 中打开启用 MDS 的工作簿，并且可能导致工作簿文件损坏。 若要与他人共享数据，应该通过电子邮件向他人发送快捷查询文件，而不是保存该工作表并通过电子邮件发送。 有关查询的详细信息，请参阅[以电子邮件形式发送快捷查询文件（用于 Excel 的 MDS 外接程序）](email-a-shortcut-query-file-mds-add-in-for-excel.md)。  
  
## <a name="filtering-data"></a>筛选数据  
 您可以加载来限制要下载的数据量之前筛选数据。 这包括选择要加载的属性（列）、属性的显示顺序，以及要处理的成员（数据行）。 有关详细信息请参阅[加载前筛选数据&#40;MDS 外接程序 excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)。  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>自动连接和加载常用数据  
 如果总要连接同一服务器并加载相同的一组数据，您可以创建快捷查询文件，其中包含连接和筛选器信息。 有关查询文件的详细信息，请参阅 [快捷查询文件（用于 Excel 的 MDS 外接程序）](shortcut-query-files-mds-add-in-for-excel.md)。  
  
## <a name="refreshing-data"></a>刷新数据  
 在您加载 MDS 存储库中的数据后，其他用户可能更新这些数据。 可以检索此数据，而不会丢失对非 MDS 数据所做的更改。 有关详细信息，请参阅[刷新数据（用于 Excel 的 MDS 外接程序）](refreshing-data-mds-add-in-for-excel.md)。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|任务说明|主题|  
|----------------------|-----------|  
|将 MDS 数据加载到 Excel 中之前先对其进行筛选。|[加载前筛选数据&#40;MDS add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|将 MDS 数据加载到 Excel 中。|[将数据从 MDS 加载到 Excel](export-data-to-excel-from-master-data-services.md)|  
|下载数据前更改列的顺序。|[对列重新排序（用于 Excel 的 MDS 外接程序）](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>相关内容  
  
-   [连接（用于 Excel 的 MDS 外接程序）](connections-mds-add-in-for-excel.md)  
  
-   [快捷查询文件（用于 Excel 的 MDS 外接程序）](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [用于 Microsoft Excel 的 Master Data Services 外接程序](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [安全性 (Master Data Services)](../security-master-data-services.md)  
  
  
