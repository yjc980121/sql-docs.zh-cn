---
title: Azure Blob 上载任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 392fcbf3a46b48b2032b5792321e9a22b3027341
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62832771"
---
# <a name="azure-blob-upload-task"></a>Azure blob 上载任务
  Azure Blob 上载任务允许 SSIS 包文件上传到 Azure blob 存储。   
若要添加“Azure blob 上传任务”  ，请将其拖放到“SSIS 设计器”中，双击或右键单击它，然后单击“编辑”  调出下面的“Azure blob 上传任务编辑器”  对话框。  
  
 下表介绍了此对话框中的各个字段。  
  
|||  
|-|-|  
|**字段**|**说明**|  
|AzureStorageConnection|选择一个现有的 Azure 存储连接管理器或创建一个新的连接管理器，用于引用指向在其中托管 blob 文件的 Azure 存储帐户。|  
|BlobContainer|指定将上载的文件作为 blob 保留的 blob 容器的名称。|  
|BlobDirectory|指定将上载的文件作为块 blob 存储的 blob 目录。 Blob 目录是虚拟的层次结构。 如果 blob 已存在，它会被替换。|  
|LocalDirectory|指定包含要上载的文件的本地目录。|  
|FileName|指定用于选择具有指定名称模式的文件的名称筛选器。 例如 MySheet*.xls\* 包括如 MySheet001.xls 和 MySheetABC.xlsx 等文件。|  
|TimeRangeFrom/TimeRangeTo|指定时间范围筛选器。 包括介于 **TimeRangeFrom** 和 **TimeRangeTo** 之间修改的文件。|  
  
  
