---
title: 如何使用指针复制字节数组 - C# 编程指南
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397410"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>如何使用指针复制字节数组（C# 编程指南）

下面的示例使用指针将字节从一个数组复制到另一个数组。

此示例使用 [unsafe](../../language-reference/keywords/unsafe.md) 关键字，使你可以在 `Copy` 方法中使用指针。 [fixed](../../language-reference/keywords/fixed-statement.md) 语句用于声明指向源数组和目标数组的指针。 `fixed` 语句将源数组和目标数组的位置固定  在内存中，以便它们不会被垃圾回收所移动。 当完成 `fixed` 块后，将取消固定数组的内存块。 因为此示例中的 `Copy` 方法使用 `unsafe` 关键字，所以必须使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 编译器选项对其进行编译。

此示例使用索引而非第二个非托管的指针访问这两个数组的元素。 `pSource` 和 `pTarget` 指针的声明固定数组。 从 C# 7.3 开始可以使用此功能。

## <a name="example"></a>示例

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>另请参阅

- [C# 编程指南](../index.md)
- [不安全代码和指针](index.md)
- [-unsafe（C# 编译器选项）](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [垃圾回收](../../../standard/garbage-collection/index.md)
