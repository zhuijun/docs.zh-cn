---
description: set 关键字 - C# 参考
title: set 关键字 - C# 参考
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: ff0c99e5d4d6271351783befd6650d9a77f39886
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136910"
---
# <a name="set-c-reference"></a><span data-ttu-id="39760-103">set（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="39760-103">set (C# Reference)</span></span>

<span data-ttu-id="39760-104">`set` 关键字在属性或索引器中定义访问器，它会向属性或索引器元素分配值。</span><span class="sxs-lookup"><span data-stu-id="39760-104">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="39760-105">有关详细信息和示例，请参阅[属性](../../programming-guide/classes-and-structs/properties.md)、[自动实现的属性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)和[索引器](../../programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="39760-105">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="39760-106">下面的示例为名为 `Seconds` 的属性同时定义 `get` 和 `set` 访问器。</span><span class="sxs-lookup"><span data-stu-id="39760-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="39760-107">它使用名为 `_seconds` 的私有字段备份属性值。</span><span class="sxs-lookup"><span data-stu-id="39760-107">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="39760-108">通常，`set` 访问器包含分配一个值的单个语句，如前面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="39760-108">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="39760-109">从 C# 7.0 开始，可以将 `set` 访问器作为 expression-bodied 成员实现。</span><span class="sxs-lookup"><span data-stu-id="39760-109">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="39760-110">下面的示例将 `get` 和 `set` 访问器都作为表达式主体成员实现。</span><span class="sxs-lookup"><span data-stu-id="39760-110">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="39760-111">对于属性的 `get` 和 `set` 访问器不执行除设置或检索私有支持字段中的值以外的任何其他操作的简单情况，可以利用 C# 编译器对自动实现的属性的支持。</span><span class="sxs-lookup"><span data-stu-id="39760-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="39760-112">以下示例将 `Hours` 作为自动实现的属性来实现。</span><span class="sxs-lookup"><span data-stu-id="39760-112">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="39760-113">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="39760-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="39760-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="39760-114">See also</span></span>

- [<span data-ttu-id="39760-115">C# 参考</span><span class="sxs-lookup"><span data-stu-id="39760-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="39760-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="39760-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="39760-117">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="39760-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="39760-118">属性</span><span class="sxs-lookup"><span data-stu-id="39760-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
