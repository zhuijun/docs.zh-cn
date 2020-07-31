---
title: 发出动态方法和程序集
description: 使用 System.Reflection.Emit 命名空间发出动态方法和程序集，该命名空间允许编译器或工具在运行时发出元数据和 MSIL 代码。
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 76d2a83943d9df06cc66cf86c6869f18fac2a12c
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475042"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="c6771-103">发出动态方法和程序集</span><span class="sxs-lookup"><span data-stu-id="c6771-103">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="c6771-104">本节介绍 <xref:System.Reflection.Emit> 命名空间中的一组托管类型，它们允许编译器或工具在运行时发出元数据和 Microsoft 中间语言 (MSIL)，并在磁盘上生成可移植可执行 (PE) 文件（可选）。</span><span class="sxs-lookup"><span data-stu-id="c6771-104">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="c6771-105">脚本引擎和编译器是此命名空间的主要使用者。</span><span class="sxs-lookup"><span data-stu-id="c6771-105">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="c6771-106">在本节中，<xref:System.Reflection.Emit> 命名空间提供的功能被称为反射发出。</span><span class="sxs-lookup"><span data-stu-id="c6771-106">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="c6771-107">反射发出具有以下功能：</span><span class="sxs-lookup"><span data-stu-id="c6771-107">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="c6771-108">在运行时定义轻量全局方法（使用 <xref:System.Reflection.Emit.DynamicMethod> 类）并通过委托执行这些方法。</span><span class="sxs-lookup"><span data-stu-id="c6771-108">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="c6771-109">在运行时定义程序集，然后运行程序集以及/或者将程序集保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="c6771-109">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="c6771-110">在运行时定义程序集，运行程序集，然后卸载程序集并允许垃圾回收回收其资源。</span><span class="sxs-lookup"><span data-stu-id="c6771-110">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="c6771-111">在运行时在新的程序集中定义模块，然后运行模块以及/或者将模块保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="c6771-111">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="c6771-112">在运行时在模块中定义类型，创建这些类型的实例并调用其方法。</span><span class="sxs-lookup"><span data-stu-id="c6771-112">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="c6771-113">为已定义模块定义可供工具（如调试器和代码探查器）使用的符号化信息。</span><span class="sxs-lookup"><span data-stu-id="c6771-113">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="c6771-114">除了 <xref:System.Reflection.Emit> 命名空间中的托管类型，还有非托管元数据接口，非托管元数据接口在[元数据接口](../unmanaged-api/metadata/metadata-interfaces.md)参考文档中介绍。</span><span class="sxs-lookup"><span data-stu-id="c6771-114">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="c6771-115">托管的反射发出提供比非托管元数据接口更强的语义错误检查和更高级别的元数据抽象。</span><span class="sxs-lookup"><span data-stu-id="c6771-115">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="c6771-116">元数据和 MSIL 的另一个有用资源是《公共语言基础结构 (CLI)》文档，尤其是“第二部分：Metadata Definition and Semantics”（第 2 部分：元数据定义和语义）和“Partition III:CIL Instruction Set”（第 3 部分：CIL 指令集）。</span><span class="sxs-lookup"><span data-stu-id="c6771-116">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="c6771-117">该文档可在 [Ecma 网站](https://www.ecma-international.org/publications/standards/Ecma-335.htm)上联机获取。</span><span class="sxs-lookup"><span data-stu-id="c6771-117">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6771-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="c6771-118">In This Section</span></span>
  
[<span data-ttu-id="c6771-119">反射发出中的安全问题</span><span class="sxs-lookup"><span data-stu-id="c6771-119">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="c6771-120">介绍与使用反射发出创建动态程序集相关的安全问题。</span><span class="sxs-lookup"><span data-stu-id="c6771-120">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="c6771-121">[如何：定义和执行动态方法](how-to-define-and-execute-dynamic-methods.md) 介绍如何执行简单的动态方法和绑定到类实例的动态方法。</span><span class="sxs-lookup"><span data-stu-id="c6771-121">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="c6771-122">[如何：使用反射发出定义泛型类型](how-to-define-a-generic-type-with-reflection-emit.md) 介绍如何创建具有两个参数的简单泛型类型、如何对类型参数应用类约束、接口约束和特殊约束，以及如何创建使用类的类型参数作为参数类型和返回类型的成员。</span><span class="sxs-lookup"><span data-stu-id="c6771-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="c6771-123">[如何：使用反射发出定义泛型方法](how-to-define-a-generic-method-with-reflection-emit.md) 介绍如何创建、发出和调用简单的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="c6771-123">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="c6771-124">[动态类型生成的可回收程序集](collectible-assemblies.md) 介绍可回收程序集，它是一个动态程序集，卸载该程序集时，无需卸载在其中创建了该程序集的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="c6771-124">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="c6771-125">参考</span><span class="sxs-lookup"><span data-stu-id="c6771-125">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="c6771-126">编录可用于生成方法体的 MSIL 指令代码。</span><span class="sxs-lookup"><span data-stu-id="c6771-126">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="c6771-127">包含用于发出动态方法、程序集和类型的托管类。</span><span class="sxs-lookup"><span data-stu-id="c6771-127">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="c6771-128">介绍 <xref:System.Type> 类，该类代表托管反射和反射发出中的类型，它是使用这些技术的关键。</span><span class="sxs-lookup"><span data-stu-id="c6771-128">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="c6771-129">包含用于浏览元数据和托管代码的托管类。</span><span class="sxs-lookup"><span data-stu-id="c6771-129">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c6771-130">相关章节</span><span class="sxs-lookup"><span data-stu-id="c6771-130">Related Sections</span></span>  

[<span data-ttu-id="c6771-131">反射</span><span class="sxs-lookup"><span data-stu-id="c6771-131">Reflection</span></span>](reflection.md)  
<span data-ttu-id="c6771-132">说明如何浏览元数据和托管代码。</span><span class="sxs-lookup"><span data-stu-id="c6771-132">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="c6771-133">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="c6771-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="c6771-134">概述 .NET 实现中的程序集。</span><span class="sxs-lookup"><span data-stu-id="c6771-134">Provides an overview of assemblies in .NET implementations.</span></span>
