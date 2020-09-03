---
description: 详细了解 C# 中的 void 关键字
title: void - C# 参考
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: c0282a1eafd03506cd9ff05b209b2a27af216b2f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118151"
---
# <a name="void-c-reference"></a>void（C# 参考）

可以将 `void` 用作[方法](../../programming-guide/classes-and-structs/methods.md)（或[本地函数](../../programming-guide/classes-and-structs/local-functions.md)）的返回类型来指定该方法不返回值。

[!code-csharp[void method](snippets/VoidType.cs#VoidExample)]

还可以将 `void` 用作引用类型来声明指向未知类型的指针。 有关详细信息，请参阅[指针类型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。

不能将 `void` 用作变量的类型。

## <a name="see-also"></a>另请参阅

- [C# 参考](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
