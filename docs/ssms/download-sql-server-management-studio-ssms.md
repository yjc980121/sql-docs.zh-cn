---
title: 下载 SQL Server Management Studio (SSMS) | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein, maghan
ms.technology: ssms
ms.topic: conceptual
keywords:
- 安装 SSMS，下载 SSMS，最新的 SSMS
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- SQL Management Studio 安装
- 下载 SQL Management Studio
- MS SQL Management Studio
- 安装 SQL Management Studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
author: dnethi
ms.author: dinethi
ms.custom: ''
ms.date: 11/04/2019
ms.openlocfilehash: 38c594e235bf68c18ec493fd8ec43f585ea0378c
ms.sourcegitcommit: 0c40843c13f67ba7d975f4fedb9d20d70747f66d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74097859"
---
# <a name="download-sql-server-management-studio-ssms"></a>下载 SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) 是一种集成环境，用于管理从 SQL Server 到 Azure SQL 数据库的任何 SQL 基础结构。 SSMS 提供用于配置、监视和管理 SQL Server 和数据库实例的工具。 使用 SSMS 部署、监视和升级应用程序使用的数据层组件，以及生成查询和脚本。

使用 SSMS 在本地计算机或云端查询、设计和管理数据库及数据仓库，无论它们位于何处。

SSMS 是免费的！

## <a name="download-ssms"></a>下载 SSMS

**[![下载](media/download-icon.png)下载 SQL Server Management Studio (SSMS)](https://aka.ms/ssmsfullsetup)**

SSMS 18.4 是 SSMS 的最新正式发布 (GA) 版。 如果安装了之前的 SSMS 18 GA 版本，请安装 SSMS 18.4 将它升级到 18.4。 如果安装了较早的 SSMS 18.x 预览版，必须在安装 SSMS 18.4 前卸载预览版  。

### <a name="version-information"></a>版本信息

- 版本号：18.4  
- 生成号：15.0.18206.0  
- 发布日期：2019 年 11 月 4 日  

如果你有任何意见或建议，或想报告问题，最好是通过 [UserVoice](https://aka.ms/sqlfeedback) 与 SSMS 团队联系。

SSMS 18.x 安装不会升级或替换 SSMS 17.x 或更早版本。 SSMS 18.x 与以前的版本并行安装，因此，这两个版本均可供使用。

如果计算机包含 SSMS 的并行安装，请验证你是否针对特定需求启动相应的版本。 最新版本标记为 Microsoft SQL Server Management Studio 18 

> [!Note]
> 如果你正从一个非英语的语言版本访问此页面并想要查看最新内容，请访问[此网站的英语（美国）版本](https://aka.ms/downloadssmsusenglish)。 可以通过选择[可用语言](#available-languages)从英语（美国）版本站点下载不同的语言。

## <a name="available-languages"></a>可用语言

此版本的 SSMS 可以安装在以下语言中：

SQL Server Management Studio 18.4：  
[中文（简体）](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x804) | [中文（繁体）](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x404) | [英语（美国）](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x409) | [法语](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x40c) | [德语](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x407) | [意大利语](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x410) | [日语](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x411) | [朝鲜语](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x412) | [葡萄牙语（巴西）](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x416) | [俄语](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x419) | [西班牙语](https://go.microsoft.com/fwlink/?linkid=2108895&clcid=0x40a)

> [!NOTE]
> SQL Server PowerShell 模块可通过 PowerShell 库单独安装。 有关详细信息，请参阅[下载 SQL Server PowerShell 模块](download-sql-server-ps-module.md)。

## <a name="new-in-this-release-ssms-184"></a>此版本 (SSMS 18.4) 中的新增功能

| 新建项 | 详细信息 |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 数据分类 | 添加了对用于数据分类的自定义信息保护策略的支持。 |
| 查询存储 | 在对话框属性中添加了“每个查询的最大计划数”值  。 |
| 查询存储 | 添加了对新的自定义捕获策略的支持。 |
| SMO/脚本 | SQL DW 中的具体化视图的支持脚本。 |
| SMO/脚本 | 添加了对按需 SQL 的支持  。 |
| SMO/脚本 | [SQL 评估 API](../sql-assessment-api/sql-assessment-api-overview.md) - 添加了 50 条评估规则（请参阅 GitHub 上的详细信息）。 |
| SMO/脚本 | [SQL 评估 API](../sql-assessment-api/sql-assessment-api-overview.md) - 添加了基本数学表达式以及与规则条件的比较。 |
| SMO/脚本 | [SQL 评估 API](../sql-assessment-api/sql-assessment-api-overview.md) - 添加了对 RegisteredServer 对象的支持。 |
| SMO/脚本 | [SQL 评估 API](../sql-assessment-api/sql-assessment-api-overview.md) - 更新了以 JSON 格式存储规则，还更新了应用替代项/自定义项的机制。 |
| SMO/脚本 | [SQL 评估 API](../sql-assessment-api/sql-assessment-api-overview.md) - 更新了规则以支持 Linux 上的 SQL。 |
| SMO/脚本 | [SQL 评估 API](../sql-assessment-api/sql-assessment-api-overview.md) - 更新了规则集 JSON 格式并添加了架构版本。 |
| SMO/脚本 | [SQL 评估 API](../sql-assessment-api/sql-assessment-api-overview.md) - 更新了 cmdlet 输出以提高建议的可读性。 |
| XEvent 探查器 | 向 XEvent 探查器会话添加了 error_reported 事件  。 |

有关此版本中新增功能的详细信息，请参阅 [SSMS 发行说明](release-notes-ssms.md)。

## <a name="supported-sql-offerings-ssms-184"></a>受支持的 SQL 产品/服务 (SSMS 18.4)

- 此版本的 SSMS 适用于所有[受支持 SQL Server 2008 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044)，并且在最大程度上支持与 Azure SQL 数据库和 Azure SQL 数据仓库中的最新云功能配合使用。
- 此外，SSMS 18.x 可与 SSMS 17.x、SSMS 16.x 或 SQL Server 2014 SSMS 及早期版本并行安装。
- SQL Server Integration Services (SSIS) - SSMS 版本 17.x 或更高版本不支持连接到旧版 SQL Server Integration Services 服务。 要连接到早期版本的 Integration Services，请使用与 SQL Server 版本一致的 SSMS 版本。 例如，使用 SSMS 16.x 连接到旧版 SQL Server 2016 Integration Services 服务。 可以在同一台计算机上并行安装 SSMS 17.x 和 SSMS 16.x。 由于 SQL Server 2012 的发布，建议使用 SSIS 目录数据库 (SSISDB) 来存储、管理、运行和监视 Integration Services 包。 有关详细信息，请参阅 [SSIS 目录](../integration-services/catalog/ssis-catalog.md)。

## <a name="supported-operating-systems-ssms-184"></a>受支持的操作系统 (SSMS 18.4)

与最新可用的服务包一起使用时，此版本的 SSMS 支持以下 64 位平台：

- Windows 10（64 位）<sup>*</sup>
- Windows 8.1（64 位）
- Windows Server 2019（64 位）
- Windows Server 2016（64 位）<sup>*</sup>
- Windows Server 2012 R2（64 位）
- Windows Server 2012（64 位）
- Windows Server 2008 R2（64 位）

<sup>*</sup> 需要 1607 (10.0.14393) 或更高版本

> [!NOTE]
> SSMS 仅在 Windows 上运行。 如果需要在 Windows 以外的平台上运行的工具，请查看 Azure Data Studio。 Azure Data Studio 是一个全新的跨平台工具，可在 macOS、Linux 以及 Windows 上运行。 有关详细信息，请参阅 [Azure Data Studio](../azure-data-studio/what-is.md)。

## <a name="release-notes-ssms-184"></a>发行说明 (SSMS 18.4)

此版本存在一些[已知问题](release-notes-ssms.md#known-issues-184)。

有关此版本的详细信息，请参阅 [SSMS 发行说明](release-notes-ssms.md)。

## <a name="previous-ssms-releases"></a>SSMS 的早期版本

[旧版 SQL Server Management Studio](../ssms/release-notes-ssms.md#previous-ssms-releases)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

## <a name="see-also"></a>另请参阅

- [教程：SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [SQL Server Management Studio 文档](sql-server-management-studio-ssms.md)
- [其他更新程序和 Service Pack](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [下载 SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
