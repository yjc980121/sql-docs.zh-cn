---
title: 下载用于脱机安装的更新
description: 下载适用于 SQL Server 机器学习服务和 SQL Server 2016 R Services 的 R 和 Python CAB 以及包文件。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e7266d90e04071c242145fc0df2e59ce86d86a16
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727623"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>SQL Server 数据库内分析实例上的累积更新的 CAB 下载

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

为数据库内分析配置的 SQL Server 实例包括 R 和 Python 功能。 这些功能随附在 CAB 文件中，可通过 SQL Server 安装程序进行安装和维护。 在连接 Internet 的设备上，通常是通过 Windows 更新应用 CAB 更新。 在断开连接的服务器上，必须手动下载和应用 CAB 文件。 

本文提供了每个累积更新的 CAB 文件的下载链接。 有关脱机安装的详细信息，请参阅[在没有 Internet 访问权限的情况下安装 SQL Server 机器学习组件](sql-ml-component-install-without-internet-access.md#apply-cu)。

## <a name="prerequisites"></a>必备条件

开始使用基线安装。

+ 在 SQL Server 机器学习服务上，初始版本为基线安装。 
+ 在 SQL Server 2016 R Services 上，可从初始版本、SP1 或 SP2 开始。 

还可将累积更新应用于独立服务器。

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CAB

CAB 文件按时间倒序列出。 下载 CAB 文件并将其传输到目标计算机时，请将其放置在方便找到的文件夹中，例如“下载”或安装程序用户的 %temp% 文件夹  。

|发行版本  |组件 | 下载链接  | 解决的问题 | 
|---------|----------|----------------|------------------|
|**[SQL Server 2017 CU14](https://support.microsoft.com/help/4484710/)-[CU15](https://support.microsoft.com/help/4498951/)-[CU16](https://support.microsoft.com/help/4508218/)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073898&clcid=1033)| 包中的二进制文件现已签名。 |
| | Microsoft R Server      |[SRS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2069739&clcid=1033)| 包中的二进制文件现已签名。 |
| | Microsoft Python Open     | [SPO_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073897&clcid=1033)| 包中的二进制文件现已签名。 |
| | Python Server    |[SPS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2071421&clcid=1033)| 包中的二进制文件现已签名。  |
|**[SQL Server 2017 CU13](https://support.microsoft.com/help/4466404)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| 未对前一版本进行更改。 |
| | Microsoft R Server      |[SRS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038263&clcid=1033)| 包含一个修补程序，用于升级通过 SQL Server 安装程序安装的[操作化独立 R Server](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)。 使用 CU13 CAB，并按照[这些说明](sql-machine-learning-standalone-windows-install.md#apply-cu)应用更新。 |
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| 未对前一版本进行更改。 |
| | Python Server    |[SPS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038197&clcid=1033)| 包含一个修补程序，用于升级通过 SQL Server 安装程序安装的[操作化独立 Python Server](https://docs.microsoft.com/machine-learning-server/what-is-operationalization)。 使用 CU13 CAB，并按照[这些说明](sql-machine-learning-standalone-windows-install.md#apply-cu)应用更新。 |
|**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)-[CU12](https://support.microsoft.com/help/4464082)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| 未对前一版本进行更改。 |
| | Microsoft R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| 一些小问题修复。|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| 未对前一版本进行更改。 |
| | Python Server    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| 删除重复项后，Python rx_data_step 将失去行顺序。 <br/>SPEE 无法在聚集列存储索引上检测数据类型。 <br/>当列包含所有 null 值时，将返回一个空表。 |
|**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| 未对前一版本进行更改。 |
| | Microsoft R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| 未对前一版本进行更改。 |
| | Python Server    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
|**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| 未对前一版本进行更改。 |
| | Microsoft R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| 未对前一版本进行更改。 |
| | Python Server    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| SPEES 查询中的日期/时间数据类型。<br/>缺少预先定型模型时在 microsoftml 中改进错误消息。<br/> 修复 revoscalepy 转换函数和变量。|
|**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| 未对前一版本进行更改。 |
| | Microsoft R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| rxInstallPackages 中与长路径相关的错误。<br/>用于 RxExec 的环回中的连接。
| | Microsoft Python Open    | 未对前一版本进行更改。 |
| | Python Server    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>用于 rx_exec 的环回中的连接。
|**[SQL Server 2017 CU4](https://support.microsoft.com/help/4056498)** |  |   |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| 未对前一版本进行更改。 |
| | Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
| | Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| 未对前一版本进行更改。 |
| |  Python Server    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
|**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |  |
| | Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
| | Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
| | Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| 未对前一版本进行更改。 |
| | Python Server    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| 使用 [rx_serialize_model 函数](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model)在 revoscalepy 中进行 Python 模型序列化。<br/>[本机评分](../sql-native-scoring.md)支持，以及[实时评分](../real-time-scoring.md)的增强功能。 
|**[SQL Server 2017 CU1](https://support.microsoft.com/help/4038634)-[CU2](https://support.microsoft.com/help/4052574)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| 未对前一版本进行更改。 |
| | Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| 未对前一版本进行更改。 | 
| | Python Server    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | 添加 rx_create_col_info 以返回架构信息。 <br/>[rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) 的增强功能，可支持使用 `RxLocalParallel` 计算上下文的并行方案。|
|**初始版本** |  |  |
| | Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
| | Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
| | Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
| | Python Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CAB

对于 SQL Server 2016 R Services，基线版本是 RTM 版本或 Service Pack 版本。

|发行版本  |下载链接  |
|---------|---------------|
|**SQL Server 2016 SP2 CU6**     |
|Microsoft R Open     |[SRO_3.2.2.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079936&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079933&clcid=1033)|
|**SQL Server 2016 SP2 CU1-CU5**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
|**SQL Server 2016 SP2**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)|
|**SQL Server 2016 SP1 CU14**     |
|Microsoft R Open     |[SRO_3.2.2.16100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2080130&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.17200_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079935&clcid=1033)|
|**SQL Server 2016 SP1 CU1-CU13**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
|**SQL Server 2016 SP1**     |
|Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)|
|Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)|
|**SQL Server 2016 CU4-CU9**     |
|Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
|Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
|**SQL Server 2016 CU2-CU3**     |
|Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)|
|Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)|
|**SQL Server 2016 CU1**     |
|Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)|
|Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)|
|**SQL Server 2016 RTM**     |
|Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)|
|Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)|

> [!NOTE]
> 
> 脱机安装 SQL Server 2016 SP1 CU4 或 SP1 CU5 时，请下载 SRO_3.2.2.16000_1033.cab。 如果按安装对话框中所示的方式从 FWLINK 831785 下载 SRO_3.2.2.13000_1033.cab，请在安装累积更新前将该文件重命名为 SRO_3.2.2.16000_1033.cab。

如果想查看 Microsoft R 的源代码，可以将其下载为 .tar 格式的存档：[下载 R Server 安装程序](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

::: moniker-end

## <a name="next-steps"></a>后续步骤

[在没有 Internet 访问权限的计算机上应用累积更新](sql-ml-component-install-without-internet-access.md#apply-cu)

[在有 Internet 连接的计算机上应用累积更新](sql-ml-component-install-without-internet-access.md#apply-cu)

[将累积更新应用于独立服务器](sql-machine-learning-standalone-windows-install.md#apply-cu)
