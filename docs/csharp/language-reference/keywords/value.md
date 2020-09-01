---
description: value 上下文关键字 - C# 参考
title: value 上下文关键字 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f72e9f097880d9de725a85a0973001baaefd9a9c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141733"
---
# <a name="value-c-reference"></a><span data-ttu-id="482b4-103">value（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="482b4-103">value (C# Reference)</span></span>

<span data-ttu-id="482b4-104">上下文关键字 `value` 在[属性](../../programming-guide/classes-and-structs/properties.md)和[索引器](../../programming-guide/indexers/index.md)声明的 `set` 访问器中使用。</span><span class="sxs-lookup"><span data-stu-id="482b4-104">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="482b4-105">此关键字类似于方法的输入参数。</span><span class="sxs-lookup"><span data-stu-id="482b4-105">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="482b4-106">关键字 `value` 引用客户端代码尝试分配给属性或索引器的值。</span><span class="sxs-lookup"><span data-stu-id="482b4-106">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="482b4-107">在以下示例中，`MyDerivedClass` 有一个名为 `Name` 的属性，该属性使用 `value` 参数向支持字段 `name` 分配新字符串。</span><span class="sxs-lookup"><span data-stu-id="482b4-107">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="482b4-108">从客户端代码的角度来看，该操作写作一个简单的赋值语句。</span><span class="sxs-lookup"><span data-stu-id="482b4-108">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="482b4-109">有关详细信息，请参阅[属性](../../programming-guide/classes-and-structs/properties.md)和[索引器](../../programming-guide/indexers/index.md)一文。</span><span class="sxs-lookup"><span data-stu-id="482b4-109">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="482b4-110">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="482b4-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="482b4-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="482b4-111">See also</span></span>

- [<span data-ttu-id="482b4-112">C# 参考</span><span class="sxs-lookup"><span data-stu-id="482b4-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="482b4-113">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="482b4-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="482b4-114">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="482b4-114">C# Keywords</span></span>](index.md)
