---
description: '#region -C# 参考'
title: '#region -C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: ed40d895fedb9be271bb389a4f8de69d7ae3f266
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137937"
---
# <a name="region-c-reference"></a>#region（C# 参考）
利用 `#region`，可以指定在使用代码编辑器的[大纲](/visualstudio/ide/outlining)功能时可展开或折叠的代码块。 在较长的代码文件中，能够折叠或隐藏一个或多个区域会十分便利，这样，可将精力集中于当前处理的文件部分。 下面的示例演示如何定义区域：  
  
```csharp
#region MyClass definition  
public class MyClass
{  
    static void Main()
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>备注  
 `#region` 块必须通过 [#endregion](./preprocessor-endregion.md) 指令终止。  
  
 `#region` 块不能与 [#if](./preprocessor-if.md) 块重叠。 但是，可以将 `#region` 块嵌套在 `#if` 块内，或将 `#if` 块嵌套在 `#region` 块内。  
  
## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 预处理器指令](./index.md)
