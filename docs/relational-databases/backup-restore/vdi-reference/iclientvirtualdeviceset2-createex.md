---
title: IClientVirtualDeviceSet2::CreateEx
titlesuffix: SQL Server VDI reference
description: 本文提供了 IClientVirtualDeviceSet2::CreateEx 命令的参考。
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 90165738dfcea8818353d602f72390bb08eea792
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847348"
---
# <a name="iclientvirtualdeviceset2createex-vdi"></a>IClientVirtualDeviceSet2::CreateEx (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

CreateEx 函数创建虚拟设备集  。

## <a name="syntax"></a>语法

```c
HRESULT IClientVirtualDeviceSet2::CreateEx (
   LPCWSTR         lpInstanceName,
   LPCWSTR         lpName,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>Parameters

*lpInstanceName* 此字符串标识将向其发送 SQL 命令的 SQL Server 实例。

*lpName* 此字符串用于标识虚拟设备集。 必须遵循 CreateFileMapping() 所用的名称规则。 可以使用除反斜杠 (\) 以外的任何字符。 这是一个宽字符 Unicode 字符串。 建议将用户的产品或公司名称和数据库名称作为字符串前缀。

*pCfg* 这是虚拟设备集的配置。 有关详细信息，请参阅“配置”。

## <a name="return-value"></a>返回值

|返回值 | 解释 |
|---|---|
| NOERROR | 函数成功。 |
| VD_E_NOTSUPPORTED | 配置中的一个或多个字段无效或不受支持。 |
| VD_E_PROTOCOL | 已创建虚拟设备集。 |

## <a name="remarks"></a>Remarks

每个 BACKUP 或 RESTORE 操作仅应调用一次 CreateEx 方法。 调用 Close 方法后，客户端可以重复使用接口创建另一个虚拟设备集。

实例名称必须标识向其发出 Transact-SQL 的实例。 NULL 标识默认实例。 不接受 "machineName\" 前缀。

CreateEx（和 Create）调用将修改客户端进程中进程句柄上的安全 DACL。 因此，必须通过调用 CreateEx 对进程句柄的任何其他修改进行序列化。 CreateEx 将通过对 CreateEx 的其他调用进行序列化，但无法通过外部处理进行序列化。 对运行 SQL Server 服务的帐户授予访问权限。

CreateEx 方法取代了原始 IClientVirtualDeviceSet 中定义的 Create 方法。 原始 Create 方法已弃用，不应在未来的开发中使用。 原始 Create 方法使用 VIRTUAL_SERVER_NAME 环境变量实现对实例名称的支持  。 如果在环境中设置该变量，则 Create 方法会在内部调用 CreateEx，并将 VIRTUAL_SERVER_NAME 的值作为实例名称传递  。

## <a name="next-steps"></a>后续步骤

有关详细信息，请参阅 [SQL Server 虚拟设备接口引用概述](reference-virtual-device-interface.md)。