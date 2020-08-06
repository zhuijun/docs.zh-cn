---
title: 接口中的索引器 - C# 编程指南
description: 可以在 C# 中的接口上声明索引器。 了解接口索引器的访问器与类索引器的访问器有何差异。
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303096"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="5bf1d-104">接口中的索引器（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="5bf1d-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="5bf1d-105">可以在[接口](../../language-reference/keywords/interface.md)上声明索引器。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="5bf1d-106">接口索引器的访问器与[类](../../language-reference/keywords/class.md)索引器的访问器有所不同，差异如下：</span><span class="sxs-lookup"><span data-stu-id="5bf1d-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="5bf1d-107">接口访问器不使用修饰符。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="5bf1d-108">接口访问器通常没有正文。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="5bf1d-109">访问器的用途是指示索引器为读写、只读还是只写。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="5bf1d-110">可以为接口中定义的索引器提供实现，但这种情况非常少。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="5bf1d-111">索引器通常定义 API 来访问数据字段，而数据字段无法在接口中定义。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="5bf1d-112">下面是接口索引器访问器的示例：</span><span class="sxs-lookup"><span data-stu-id="5bf1d-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="5bf1d-113">索引器的签名必须不同于同一接口中声明的所有其他索引器的签名。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="5bf1d-114">示例</span><span class="sxs-lookup"><span data-stu-id="5bf1d-114">Example</span></span>

<span data-ttu-id="5bf1d-115">下面的示例演示如何实现接口索引器。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="5bf1d-116">在前面的示例中，可通过使用接口成员的完全限定名来使用显示接口成员实现。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="5bf1d-117">例如</span><span class="sxs-lookup"><span data-stu-id="5bf1d-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="5bf1d-118">但仅当类采用相同的索引签名实现多个接口时，才需用到完全限定名称以避免歧义。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="5bf1d-119">例如，如果 `Employee` 类正在实现接口 `ICitizen` 和接口 `IEmployee`，而这两个接口具有相同的索引签名，则需要用到显式接口成员实现。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="5bf1d-120">即是说以下索引器声明：</span><span class="sxs-lookup"><span data-stu-id="5bf1d-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="5bf1d-121">在 `IEmployee` 接口中实现索引器，而以下声明：</span><span class="sxs-lookup"><span data-stu-id="5bf1d-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="5bf1d-122">在 `ICitizen` 接口中实现索引器。</span><span class="sxs-lookup"><span data-stu-id="5bf1d-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bf1d-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="5bf1d-123">See also</span></span>

- [<span data-ttu-id="5bf1d-124">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="5bf1d-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5bf1d-125">索引器</span><span class="sxs-lookup"><span data-stu-id="5bf1d-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="5bf1d-126">属性</span><span class="sxs-lookup"><span data-stu-id="5bf1d-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="5bf1d-127">接口</span><span class="sxs-lookup"><span data-stu-id="5bf1d-127">Interfaces</span></span>](../interfaces/index.md)
