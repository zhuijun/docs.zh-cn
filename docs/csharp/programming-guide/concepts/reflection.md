---
title: 反射 (C#)
description: 反射提供描述 C# 中的程序集、模块和类型的对象。 如果代码包括特性，可以利用反射来访问它们。
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302797"
---
# <a name="reflection-c"></a><span data-ttu-id="d8f46-104">反射 (C#)</span><span class="sxs-lookup"><span data-stu-id="d8f46-104">Reflection (C#)</span></span>

<span data-ttu-id="d8f46-105">反射提供描述程序集、模块和类型的对象（<xref:System.Type> 类型）。</span><span class="sxs-lookup"><span data-stu-id="d8f46-105">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="d8f46-106">可以使用反射动态地创建类型的实例，将类型绑定到现有对象，或从现有对象中获取类型，然后调用其方法或访问器字段和属性。</span><span class="sxs-lookup"><span data-stu-id="d8f46-106">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="d8f46-107">如果代码中使用了特性，可以利用反射来访问它们。</span><span class="sxs-lookup"><span data-stu-id="d8f46-107">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="d8f46-108">有关更多信息，请参阅[特性](../../../standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f46-108">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="d8f46-109">下面一个简单的反射示例，使用方法 <xref:System.Object.GetType>（被 `Object` 基类的所有类型继承）以获取变量类型：</span><span class="sxs-lookup"><span data-stu-id="d8f46-109">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="d8f46-110">请确保在 .cs 文件顶部添加 `using System;` 和 `using System.Reflection;`。</span><span class="sxs-lookup"><span data-stu-id="d8f46-110">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="d8f46-111">输出为：`System.Int32`。</span><span class="sxs-lookup"><span data-stu-id="d8f46-111">The output is: `System.Int32`.</span></span>

<span data-ttu-id="d8f46-112">下面的示例使用反射获取已加载的程序集的完整名称。</span><span class="sxs-lookup"><span data-stu-id="d8f46-112">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="d8f46-113">输出为：`System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`。</span><span class="sxs-lookup"><span data-stu-id="d8f46-113">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="d8f46-114">C# 关键字 `protected` 和 `internal` 在 IL 中没有任何意义，且不会用于反射 API 中。</span><span class="sxs-lookup"><span data-stu-id="d8f46-114">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="d8f46-115">在 IL 中对应的术语为“系列”和“程序集”。</span><span class="sxs-lookup"><span data-stu-id="d8f46-115">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="d8f46-116">若要标识 `internal` 使用反射的方法，请使用 <xref:System.Reflection.MethodBase.IsAssembly%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="d8f46-116">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="d8f46-117">若要标识 `protected internal` 方法，请使用 <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>。</span><span class="sxs-lookup"><span data-stu-id="d8f46-117">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="d8f46-118">反射概述</span><span class="sxs-lookup"><span data-stu-id="d8f46-118">Reflection overview</span></span>

<span data-ttu-id="d8f46-119">反射在以下情况下很有用：</span><span class="sxs-lookup"><span data-stu-id="d8f46-119">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="d8f46-120">需要访问程序元数据中的特性时。</span><span class="sxs-lookup"><span data-stu-id="d8f46-120">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="d8f46-121">有关详细信息，请参阅[检索存储在特性中的信息](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f46-121">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="d8f46-122">检查和实例化程序集中的类型。</span><span class="sxs-lookup"><span data-stu-id="d8f46-122">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="d8f46-123">在运行时构建新类型。</span><span class="sxs-lookup"><span data-stu-id="d8f46-123">For building new types at runtime.</span></span> <span data-ttu-id="d8f46-124">使用 <xref:System.Reflection.Emit> 中的类。</span><span class="sxs-lookup"><span data-stu-id="d8f46-124">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="d8f46-125">执行后期绑定，访问在运行时创建的类型上的方法。</span><span class="sxs-lookup"><span data-stu-id="d8f46-125">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="d8f46-126">请参阅主题 “[动态加载和使用类型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)”。</span><span class="sxs-lookup"><span data-stu-id="d8f46-126">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="d8f46-127">相关章节</span><span class="sxs-lookup"><span data-stu-id="d8f46-127">Related sections</span></span>

<span data-ttu-id="d8f46-128">更多相关信息：</span><span class="sxs-lookup"><span data-stu-id="d8f46-128">For more information:</span></span>

- [<span data-ttu-id="d8f46-129">反射</span><span class="sxs-lookup"><span data-stu-id="d8f46-129">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="d8f46-130">查看类型信息</span><span class="sxs-lookup"><span data-stu-id="d8f46-130">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="d8f46-131">反射类型和泛型类型</span><span class="sxs-lookup"><span data-stu-id="d8f46-131">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="d8f46-132">检索存储在特性中的信息</span><span class="sxs-lookup"><span data-stu-id="d8f46-132">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="d8f46-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8f46-133">See also</span></span>

- [<span data-ttu-id="d8f46-134">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="d8f46-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d8f46-135">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="d8f46-135">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
