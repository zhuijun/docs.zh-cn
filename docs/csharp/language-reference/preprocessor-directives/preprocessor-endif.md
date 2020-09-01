---
description: '#endif - C# 参考'
title: '#endif - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138158"
---
# <a name="endif-c-reference"></a>#endif（C# 参考）
`#endif` 指定条件指令的末尾，以 [#if](./preprocessor-if.md) 指令开头。 例如，应用于对象的  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>备注  
 以 `#if` 指令开头的条件指令必须以 `#endif` 指令显式终止。 有关如何使用 `#endif` 的示例，请参阅 [#if](./preprocessor-if.md)。  
  
## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 预处理器指令](./index.md)
