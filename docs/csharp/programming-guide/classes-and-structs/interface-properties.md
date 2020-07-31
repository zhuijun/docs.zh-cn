---
title: 接口属性 - C# 编程指南
description: 可在 C# 中的接口上声明属性。 此示例声明一个接口属性访问器。
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864964"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="bcc4a-104">接口属性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="bcc4a-104">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="bcc4a-105">可以在[接口](../../language-reference/keywords/interface.md)上声明属性。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-105">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="bcc4a-106">下面的示例声明一个接口属性访问器：</span><span class="sxs-lookup"><span data-stu-id="bcc4a-106">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="bcc4a-107">接口属性通常没有主体。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-107">Interface properties typically don't have a body.</span></span> <span data-ttu-id="bcc4a-108">访问器指示属性是读写、只读还是只写。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-108">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="bcc4a-109">与在类和结构中不同，在没有主体的情况下声明访问器不会声明[自动实现的属性](auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-109">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="bcc4a-110">从 C# 8.0 开始，接口可为成员（包括属性）定义默认实现。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-110">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="bcc4a-111">在接口中为属性定义默认实现的情况非常少，因为接口可能不会定义实例数据字段。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-111">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="bcc4a-112">示例</span><span class="sxs-lookup"><span data-stu-id="bcc4a-112">Example</span></span>

<span data-ttu-id="bcc4a-113">在此示例中，接口 `IEmployee` 具有读写属性 `Name` 和只读属性 `Counter`。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-113">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="bcc4a-114">类 `Employee` 实现 `IEmployee` 接口，并使用这两个属性。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-114">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="bcc4a-115">程序读取新员工的姓名以及当前员工数，并显示员工名称和计算的员工数。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-115">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="bcc4a-116">可以使用属性的完全限定名称，它引用其中声明成员的接口。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-116">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="bcc4a-117">例如：</span><span class="sxs-lookup"><span data-stu-id="bcc4a-117">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="bcc4a-118">前面的示例演示了如何[显式接口实现](../interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-118">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="bcc4a-119">例如，如果 `Employee` 类正在实现接口 `ICitizen` 和接口 `IEmployee`，而这两个接口都具有 `Name` 属性，则需要用到显式接口成员实现。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-119">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="bcc4a-120">即是说下列属性声明：</span><span class="sxs-lookup"><span data-stu-id="bcc4a-120">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="bcc4a-121">在 `IEmployee` 接口中实现 `Name` 属性，而以下声明：</span><span class="sxs-lookup"><span data-stu-id="bcc4a-121">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="bcc4a-122">在 `ICitizen` 接口中实现 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="bcc4a-122">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="bcc4a-123">示例输出</span><span class="sxs-lookup"><span data-stu-id="bcc4a-123">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="bcc4a-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="bcc4a-124">See also</span></span>

- [<span data-ttu-id="bcc4a-125">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="bcc4a-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bcc4a-126">属性</span><span class="sxs-lookup"><span data-stu-id="bcc4a-126">Properties</span></span>](./properties.md)
- [<span data-ttu-id="bcc4a-127">使用属性</span><span class="sxs-lookup"><span data-stu-id="bcc4a-127">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="bcc4a-128">属性与索引器之间的比较</span><span class="sxs-lookup"><span data-stu-id="bcc4a-128">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="bcc4a-129">索引器</span><span class="sxs-lookup"><span data-stu-id="bcc4a-129">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="bcc4a-130">接口</span><span class="sxs-lookup"><span data-stu-id="bcc4a-130">Interfaces</span></span>](../interfaces/index.md)
