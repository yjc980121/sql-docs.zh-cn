---
title: 是 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aaf4151d8291ccd4249892c6ef8fce8a3d280f6b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905981"
---
# <a name="is-mdx"></a>IS (MDX)


  对两个对象表达式执行逻辑比较。  
  
## <a name="syntax"></a>语法  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>Parameters  
 *Expression1*  
 返回 MDX 对象引用的有效多维表达式 (MDX) 表达式。  
  
 *Expression2*  
 返回 MDX 对象引用的有效 MDX 表达式。  
  
## <a name="return-value"></a>返回值  
 一个布尔值，返回 **，则返回 true**如果这两个参数引用同一对象; 否则为**false**。 如果**NULL**指定关键字，则该运算符将返回**true**如果*Expression1*是**null**; 否则为**false**.  
  
## <a name="remarks"></a>备注  
 **IS**运算符通常用于确定是否元组和成员都是幂等的这意味着它们是否完全相等。  
  
## <a name="examples"></a>示例  
 下面的示例演示如何使用**IS**运算符来检查轴上的当前成员是否为特定成员：  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>请参阅  
 [MDX 运算符参考&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
