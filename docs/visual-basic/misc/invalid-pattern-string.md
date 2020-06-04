---
title: 无效模式字符串
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402208"
---
# <a name="invalid-pattern-string"></a>无效模式字符串
在搜索的 `Like` 操作中指定的模式字符串无效。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 查看列表中表达式的有效字符。  
  
2. 在模式范围内，请确保起始范围字符小于结束范围字符，如 `[a-z]`中所示。  
  
3. 在模式范围内，请确保不存在彼此相邻的多个连字符，如 `[a--z]`中所示。  
  
4. 以右括号结束模式范围。  
  
## <a name="see-also"></a>另请参阅

- [Like 运算符](../language-reference/operators/like-operator.md)
