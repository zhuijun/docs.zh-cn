---
description: namespace 关键字 - C# 参考
title: namespace 关键字 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: a6cfd1c3d37cbdef1f0dd72ddca85ce91f2e183b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139575"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="338ac-103">命名空间（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="338ac-103">namespace (C# Reference)</span></span>

<span data-ttu-id="338ac-104">`namespace` 关键字用于声明包含一组相关对象的作用域。</span><span class="sxs-lookup"><span data-stu-id="338ac-104">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="338ac-105">可以使用命名空间来组织代码元素并创建全局唯一类型。</span><span class="sxs-lookup"><span data-stu-id="338ac-105">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="338ac-106">备注</span><span class="sxs-lookup"><span data-stu-id="338ac-106">Remarks</span></span>

<span data-ttu-id="338ac-107">在命名空间中，可以声明零个或多个以下类型：</span><span class="sxs-lookup"><span data-stu-id="338ac-107">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="338ac-108">另一个命名空间</span><span class="sxs-lookup"><span data-stu-id="338ac-108">another namespace</span></span>

- [<span data-ttu-id="338ac-109">class</span><span class="sxs-lookup"><span data-stu-id="338ac-109">class</span></span>](class.md)

- [<span data-ttu-id="338ac-110">interface</span><span class="sxs-lookup"><span data-stu-id="338ac-110">interface</span></span>](interface.md)

- [<span data-ttu-id="338ac-111">struct</span><span class="sxs-lookup"><span data-stu-id="338ac-111">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="338ac-112">enum</span><span class="sxs-lookup"><span data-stu-id="338ac-112">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="338ac-113">delegate</span><span class="sxs-lookup"><span data-stu-id="338ac-113">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="338ac-114">无论是否在 C# 源文件中显式声明命名空间，编译器都会添加一个默认命名空间。</span><span class="sxs-lookup"><span data-stu-id="338ac-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="338ac-115">此未命名的命名空间（有时被称为全局命名空间）存在于每个文件中。</span><span class="sxs-lookup"><span data-stu-id="338ac-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="338ac-116">全局命名空间中的任何标识符都可用于已命名的命名空间。</span><span class="sxs-lookup"><span data-stu-id="338ac-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="338ac-117">命名空间隐式具有公共访问权限，这是不可修改的。</span><span class="sxs-lookup"><span data-stu-id="338ac-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="338ac-118">有关可以分配给命名空间中元素的访问修饰符的讨论，请参阅[访问修饰符](access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="338ac-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="338ac-119">可以在两个或多个声明中定义一个命名空间。</span><span class="sxs-lookup"><span data-stu-id="338ac-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="338ac-120">例如，以下示例将两个类定义为 `MyCompany` 命名空间的一部分：</span><span class="sxs-lookup"><span data-stu-id="338ac-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="338ac-121">示例</span><span class="sxs-lookup"><span data-stu-id="338ac-121">Example</span></span>

<span data-ttu-id="338ac-122">以下示例显示如何在嵌套命名空间中调用静态方法。</span><span class="sxs-lookup"><span data-stu-id="338ac-122">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="338ac-123">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="338ac-123">C# language specification</span></span>

<span data-ttu-id="338ac-124">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[命名空间](~/_csharplang/spec/namespaces.md)部分。</span><span class="sxs-lookup"><span data-stu-id="338ac-124">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="338ac-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="338ac-125">See also</span></span>

- [<span data-ttu-id="338ac-126">C# 参考</span><span class="sxs-lookup"><span data-stu-id="338ac-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="338ac-127">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="338ac-127">C# keywords</span></span>](index.md)
- [<span data-ttu-id="338ac-128">using</span><span class="sxs-lookup"><span data-stu-id="338ac-128">using</span></span>](using-directive.md)
- [<span data-ttu-id="338ac-129">using static</span><span class="sxs-lookup"><span data-stu-id="338ac-129">using static</span></span>](using-static.md)
- [<span data-ttu-id="338ac-130">命名空间别名限定符 `::`</span><span class="sxs-lookup"><span data-stu-id="338ac-130">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="338ac-131">命名空间</span><span class="sxs-lookup"><span data-stu-id="338ac-131">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
