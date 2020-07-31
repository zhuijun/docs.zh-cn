---
title: 如何使用集合初始值设定项初始化字典 - C# 编程指南
description: 了解如何使用 C# 中的 Add 方法或索引初始值设定项初始化字典。 此示例显示了这两个选项。
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 2f33240b02785c5c886a1ebebb8984d29c9f7795
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865042"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="4276a-104">如何使用集合初始值设定项初始化字典（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4276a-104">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="4276a-105"><xref:System.Collections.Generic.Dictionary%602> 包含键/值对集合。</span><span class="sxs-lookup"><span data-stu-id="4276a-105">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="4276a-106">其 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 方法采用两个参数，一个用于键，一个用于值。</span><span class="sxs-lookup"><span data-stu-id="4276a-106">Its <xref:System.Collections.Generic.Dictionary%602.Add%2A> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="4276a-107">若要初始化 <xref:System.Collections.Generic.Dictionary%602> 或其 `Add` 方法采用多个参数的任何集合，一种方法是将每组参数括在大括号中，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="4276a-107">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="4276a-108">另一种方法是使用索引初始值设定项，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="4276a-108">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="4276a-109">示例</span><span class="sxs-lookup"><span data-stu-id="4276a-109">Example</span></span>

<span data-ttu-id="4276a-110">在下面的代码示例中，使用类型 `StudentName` 的实例初始化 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="4276a-110">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="4276a-111">第一个初始化使用具有两个参数的 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="4276a-111">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="4276a-112">编译器为每对 `int` 键和 `StudentName` 值生成对 `Add` 的调用。</span><span class="sxs-lookup"><span data-stu-id="4276a-112">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="4276a-113">第二个初始化使用 `Dictionary` 类的公共读取/写入索引器方法：</span><span class="sxs-lookup"><span data-stu-id="4276a-113">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="4276a-114">请注意，在第一个声明中，集合中的每个元素有两对大括号。</span><span class="sxs-lookup"><span data-stu-id="4276a-114">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="4276a-115">最内层的大括号中的是 `StudentName` 的对象初始值设定项，最外层的大括号中的是要添加到 `students` <xref:System.Collections.Generic.Dictionary%602> 的键/值对的初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="4276a-115">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="4276a-116">最后，字典的整个集合初始值设定项被括在大括号中。</span><span class="sxs-lookup"><span data-stu-id="4276a-116">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="4276a-117">在第二个初始化中，左侧赋值是键，右侧是将对象初始值设定项用于 `StudentName` 的值。</span><span class="sxs-lookup"><span data-stu-id="4276a-117">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4276a-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="4276a-118">See also</span></span>

- [<span data-ttu-id="4276a-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="4276a-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4276a-120">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="4276a-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
