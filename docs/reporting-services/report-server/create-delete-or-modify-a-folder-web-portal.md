---
title: 创建、 删除或修改文件夹-Reporting Services |Microsoft Docs
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: 70a38879-856c-414b-8479-5f9dead38f15
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 874fb7ba143c8f08a0f25501e1852b4d2b280cb2
ms.sourcegitcommit: c0e48b643385ce19c65ca6e348ce83b2d22b6514
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2019
ms.locfileid: "67492856"
---
# <a name="create-delete-or-modify-a-folder---reporting-services"></a>创建、 删除或修改文件夹-Reporting Services
  可以创建文件夹来组织和管理发布到报表服务器的项。 创建文件夹有助于用户查找他们关注的报表。 对于内容管理员来说，文件夹提供了应用权限的框架。 可以对特定的文件夹创建角色分配，来限制对处于开发阶段或者不应大范围分布的报表的访问。  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

## <a name="to-create-a-folder"></a>创建文件夹  
  
1.  启动 [报表管理器（SSRS 本机模式）](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)。  
  
2.  在报表管理器中，选择主文件夹，再单击 **“新建文件夹”** 。 或者，若要在现有文件夹中创建文件夹，请在 **“内容”** 页中导航到该文件夹，再单击该文件夹将其打开。 然后单击 **“新建文件夹”** 。  
  
     此时，将打开 **“新建文件夹”** 页。  
  
3.  键入文件夹名称。 文件夹名称可以包含空格，但不能包含以下用于 URL 编码的保留字符：\; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|。 不能通过键入一系列文件夹名称来同时创建多个文件夹。  
  
4.  根据需要，可以键入说明。  
  
5.  如果不希望在 **“内容”** 页的默认视图中显示该文件夹，请选择 **“在列表视图中隐藏”** 。 只有在用户单击了 **“内容”** 页上的 **“显示详细信息”** 时，才可以看到该文件夹。  
  
6.  单击“确定”  。  
  
## <a name="to-delete-a-folder"></a>删除文件夹  
  
1.  在报表管理器中，导航到 **“内容”** 页，然后找到要修改的项。  
  
2.  悬停在该项之上，然后单击下拉箭头。  
  
3.  在下拉菜单中，单击“删除”  。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="to-modify-or-delete-a-folder"></a>修改或删除文件夹  
  
1.  在报表管理器中，导航到 **“内容”** 页，然后找到要修改的项。  
  
2.  悬停在该项之上，然后单击下拉箭头。  
  
3.  在下拉菜单中，单击 **“管理”** 。 此时将打开“常规属性”页。  
  
4.  若要更改该文件夹位置，请单击 **“移动”** 。 键入目标文件夹的位置，或从树中选择目标文件夹，再单击 **“确定”** 。  
  
5.  或者，通过以下方式修改该文件夹属性：  
  
    -   若要修改关于该文件夹的显示文本，请键入名称或说明。  
  
    -   若要在 **“内容”** 页上的默认视图中显示该文件夹，请清除 **“在列表视图中隐藏”** 。  
  
6.  或者，若要删除该文件夹及其内容，请单击 **“删除”** 。  
  
7.  单击 **“应用”** 以保存更改。  

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
 
## <a name="to-create-a-folder"></a>创建文件夹  
  
1. 打开[报表服务器的 Web 门户（SSRS 本机模式）](../../reporting-services/web-portal-ssrs-native-mode.md)。  
  
2. 导航到文件夹或你想要查找的新文件夹的子文件夹。 选择**主页**通过选择文件夹**浏览**在顶部工具栏上的按钮的页后，可以创建在文件夹层次结构的顶部。  
  
3. 选择**新建**右侧的报表服务器工具栏中，并选择顶部的按钮**文件夹**从下拉列表菜单。  
  
4. 在中 **（当前文件夹名称） 中创建一个新文件夹**对话框框中，输入要创建的新文件夹的名称。 文件夹名称可包含空格，但不能包含用于 URL 编码的保留字符：\; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|。 此外，不能键入一系列文件夹名称来同时创建多个文件夹。  
  
5. 选择**创建**以完成操作。  
  
## <a name="to-delete-a-folder"></a>删除文件夹  
  
1. 在 web 门户中导航文件夹层次结构，找到你想要删除的文件夹。  
  
2. 右键单击的文件夹，然后选择**删除**从下拉列表菜单。  
  
3. 选择**删除**按钮**删除<foldername>** 对话框以确认删除。  
  
## <a name="to-modify-a-folders-properties"></a>若要修改文件夹属性  
  
1. 在 web 门户中导航文件夹层次结构，找到你想要删除的文件夹。  
  
2. 右键单击的文件夹，然后选择**删除**从下拉列表菜单。  
  
3. 选择“属性”**选项卡。**属性**默认情况下显示页。  
  
4. 你可以在文件夹名称*名称** 文本框中。  
  
5. 可以添加或更改的文件夹中的说明*说明** 文本框中。  
  
6. 您可以隐藏或取消隐藏文件夹通过选中或取消选中**隐藏此项**复选框分别。  
  
7. 选择**应用**保存属性更改。  
  
8. （可选） 可以移动或删除该文件夹，通过选择**移动**或**删除**顶部的按钮**属性**页。 请参阅[移动或删除项 （web 门户）](../../reporting-services/report-server/move-or-delete-an-item-report-manager.md)文章了解详细信息。  
  
## <a name="see-also"></a>另请参阅  
 [创建、删除或修改文件夹（Web 门户）](../../reporting-services/report-server/create-delete-or-modify-a-folder-web-portal.md)   
 [报表服务器内容管理（SSRS 本机模式）](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [查找、查看和管理报表（报表生成器和 SSRS）](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)    
  
::: moniker-end