---
title: SetDefaults 方法（SInstance）
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3edec1ccd74e59a8bb79353e02939030bf43ce8a
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73659087"
---
# <a name="setdefaults-method-sinstance-class"></a>SetDefaults 方法（SInstance 类）
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  为 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例设置所有默认值，并选择覆盖现有数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>组成部分  
 对象  
 一个表示服务器实例的[SInstance 类](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md)对象。  
  
#### <a name="parameters"></a>Parameters  
  
|参数|说明|  
|---------------|-----------------|  
|*OverwriteAll*|指定是否覆盖 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端实例上的现有值的布尔值：如果覆盖现有数据，**则为 true** ; 如果不覆盖现有数据，则为**false** 。|  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 一个 **uint32** 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。  
  
## <a name="remarks"></a>注释  
  
## <a name="see-also"></a>另请参阅  
 [配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
