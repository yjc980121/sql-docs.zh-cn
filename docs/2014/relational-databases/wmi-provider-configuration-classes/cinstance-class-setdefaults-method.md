---
title: SetDefaults 方法 （CInstance 类） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (CInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2a105fd636c454ab236764611f1e57729ccad6ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63192440"
---
# <a name="setdefaults-method-cinstance-class"></a>SetDefaults 方法（CInstance 类）
  设置实例的所有默认值[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]选择覆盖现有数据的客户端。  
  
## <a name="syntax"></a>语法  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>组成部分  
 *object*  
 一个表示 [客户端实例的](cinstance-class.md) CInstance 类 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
#### <a name="parameters"></a>Parameters  
  
|参数|Description|  
|---------------|-----------------|  
|*OverwriteAll*|一个指定是否覆盖 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端实例的现有值的布尔值：若要覆盖现有数据，则为 `true`；如果不希望覆盖现有数据，则为 `false`。|  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。  
  
## <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [配置客户端协议](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
