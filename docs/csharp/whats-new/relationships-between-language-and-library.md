---
title: 语言功能与库类型之间的关系 |Microsoft 文档
description: 语言功能通常依赖于要实现的库类型。 了解该关系。
ms.date: 07/20/2017
ms.openlocfilehash: abf15385da3756c35db2df822cc2e11e9edf5758
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174096"
---
# <a name="relationships-between-language-features-and-library-types"></a><span data-ttu-id="bc839-104">语言功能与库类型之间的关系</span><span class="sxs-lookup"><span data-stu-id="bc839-104">Relationships between language features and library types</span></span>

<span data-ttu-id="bc839-105">C# 语言定义要求标准库拥有某些类型以及这些类型的特定可访问成员。</span><span class="sxs-lookup"><span data-stu-id="bc839-105">The C# language definition requires a standard library to have certain types and certain accessible members on those types.</span></span> <span data-ttu-id="bc839-106">编译器针对多种不同语言功能生成使用这些必需类型和成员的代码。</span><span class="sxs-lookup"><span data-stu-id="bc839-106">The compiler generates code that uses these required types and members for many different language features.</span></span> <span data-ttu-id="bc839-107">如有必要，在针对尚未部署这些类型或成员的环境编写代码时，可使用包含较新版本的语言所需类型的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="bc839-107">When necessary, there are NuGet packages that contain types needed for newer versions of the language when writing code for environments where those types or members have not been deployed yet.</span></span>

<span data-ttu-id="bc839-108">此标准库功能的依赖项自其第一个版本起就是 C# 语言的一部分。</span><span class="sxs-lookup"><span data-stu-id="bc839-108">This dependency on standard library functionality has been part of the C# language since its first version.</span></span> <span data-ttu-id="bc839-109">在该版本中，相关示例包括：</span><span class="sxs-lookup"><span data-stu-id="bc839-109">In that version, examples included:</span></span>

* <span data-ttu-id="bc839-110"><xref:System.Exception> - 用于编译器生成的所有异常。</span><span class="sxs-lookup"><span data-stu-id="bc839-110"><xref:System.Exception> - used for all compiler generated exceptions.</span></span>
* <span data-ttu-id="bc839-111"><xref:System.String> - C# `string` 类型是 <xref:System.String> 的同义词。</span><span class="sxs-lookup"><span data-stu-id="bc839-111"><xref:System.String> - the C# `string` type is a synonym for <xref:System.String>.</span></span>
* <span data-ttu-id="bc839-112"><xref:System.Int32> - `int` 的同义词。</span><span class="sxs-lookup"><span data-stu-id="bc839-112"><xref:System.Int32> - synonym of `int`.</span></span>

<span data-ttu-id="bc839-113">第一个版本很简单：编译器和标准库一起提供，且各自都只有一个版本。</span><span class="sxs-lookup"><span data-stu-id="bc839-113">That first version was simple: the compiler and the standard library shipped together, and there was only one version of each.</span></span>

<span data-ttu-id="bc839-114">后续版本的 C# 偶尔会向依赖项添加新类型或成员。</span><span class="sxs-lookup"><span data-stu-id="bc839-114">Subsequent versions of C# have occasionally added new types or members to the dependencies.</span></span> <span data-ttu-id="bc839-115">相关示例包括：<xref:System.Runtime.CompilerServices.INotifyCompletion>、<xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 和 <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>。</span><span class="sxs-lookup"><span data-stu-id="bc839-115">Examples include: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> and <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>.</span></span> <span data-ttu-id="bc839-116">C# 7.0 继续添加 <xref:System.ValueTuple> 的依赖项，以实现[元组](../language-reference/builtin-types/value-tuples.md)语言功能。</span><span class="sxs-lookup"><span data-stu-id="bc839-116">C# 7.0 continues this by adding a dependency on <xref:System.ValueTuple> to implement the [tuples](../language-reference/builtin-types/value-tuples.md) language feature.</span></span>

<span data-ttu-id="bc839-117">语言设计团队致力于最小化符合标准的标准库所需的类型和成员的外围应用。</span><span class="sxs-lookup"><span data-stu-id="bc839-117">The language design team works to minimize the surface area of the types and members required in a compliant standard library.</span></span> <span data-ttu-id="bc839-118">该目标针对新库功能无缝集成到语言的简洁设计进行了平衡。</span><span class="sxs-lookup"><span data-stu-id="bc839-118">That goal is balanced against a clean design where new library features are incorporated seamlessly into the language.</span></span> <span data-ttu-id="bc839-119">未来版本的 C# 中还会包括需要标准库中的新类型和成员的新功能。</span><span class="sxs-lookup"><span data-stu-id="bc839-119">There will be new features in future versions of C# that require new types and members in a standard library.</span></span> <span data-ttu-id="bc839-120">必须了解如何管理工作中的这些依赖项。</span><span class="sxs-lookup"><span data-stu-id="bc839-120">It's important to understand how to manage those dependencies in your work.</span></span>

## <a name="managing-your-dependencies"></a><span data-ttu-id="bc839-121">管理依赖项</span><span class="sxs-lookup"><span data-stu-id="bc839-121">Managing your dependencies</span></span>

<span data-ttu-id="bc839-122">C# 编译器工具现在从支持的平台上 .NET 库的发布周期分离。</span><span class="sxs-lookup"><span data-stu-id="bc839-122">C# compiler tools are now decoupled from the release cycle of the .NET libraries on supported platforms.</span></span> <span data-ttu-id="bc839-123">实际上，不同的 .NET 库有不同的发布周期：Windows 上的 .NET Framework 作为 Windows 更新发布，.NET Core 在单独的计划中提供，Xamarin 版本的库更新随适用于每个目标平台的 Xamarin 工具提供。</span><span class="sxs-lookup"><span data-stu-id="bc839-123">In fact, different .NET libraries have different release cycles: the .NET Framework on Windows is released as a Windows Update, .NET Core ships on a separate schedule, and the Xamarin versions of library updates ship with the Xamarin tools for each target platform.</span></span>

<span data-ttu-id="bc839-124">大多数时候，用户都不会注意到这些更改。</span><span class="sxs-lookup"><span data-stu-id="bc839-124">The majority of time, you won't notice these changes.</span></span> <span data-ttu-id="bc839-125">但是，如果使用的较新版本语言需要该平台上的 .NET 库中尚未包含的功能，则会引用 NuGet 包以提供这些新类型。</span><span class="sxs-lookup"><span data-stu-id="bc839-125">However, when you are working with a newer version of the language that requires features not yet in the .NET libraries on that platform, you'll reference the NuGet packages to provide those new types.</span></span>
<span data-ttu-id="bc839-126">应用支持的平台会随着新框架的安装而更新，因此可以删除额外的引用。</span><span class="sxs-lookup"><span data-stu-id="bc839-126">As the platforms your app supports are updated with new framework installations, you can remove the extra reference.</span></span>

<span data-ttu-id="bc839-127">此分离意味着即使面向没有相应框架的计算机，仍可使用新语言功能。</span><span class="sxs-lookup"><span data-stu-id="bc839-127">This separation means you can use new language features even when you are targeting machines that may not have the corresponding framework.</span></span>
