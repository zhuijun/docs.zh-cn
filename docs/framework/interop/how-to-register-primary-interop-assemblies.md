---
title: 如何：注册主互操作程序集
description: 使用程序集注册工具 (Regasm.exe) 注册主互操作程序集，并了解与互操作程序集相关的其他问题。
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
ms.openlocfilehash: a15bda7b40f160b31028c62cf7c73bdedd9541fa
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622739"
---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="f0fe5-103">如何：注册主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="f0fe5-103">How to: Register Primary Interop Assemblies</span></span>

<span data-ttu-id="f0fe5-104">类仅能由 COM 互操作封送，并总是作为接口封送。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-104">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="f0fe5-105">在某些情况下用来将该类封送的接口称为类接口。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-105">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="f0fe5-106">有关使用选择的接口重写类接口的信息，请参阅 [COM可调用包装器](../../standard/native-interop/com-callable-wrapper.md)。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-106">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md).</span></span>

 <span data-ttu-id="f0fe5-107">尽管任何想要从 .NET Framework 应用程序使用 COM 类型的开发人员都可以生成互操作程序集，但这样做会产生一个问题。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-107">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="f0fe5-108">每次一名开发人员导入 COM 类型库并对其进行签名时，该开发人员就创建了一组与另一个开发人员所导入和签名的类型不兼容的唯一类型。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-108">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="f0fe5-109">此类型不兼容性问题的解决方案是每个开发人员都获取供应商提供并签名的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-109">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>

 <span data-ttu-id="f0fe5-110">如果你打算向其他应用程序公开第三方 COM 类型，请始终使用与定义的类型库相同的发布者所提供的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-110">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="f0fe5-111">除了提供有保证的类型兼容性，主互操作程序集通常由供应商自定义以增强互操作性。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-111">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>

 <span data-ttu-id="f0fe5-112">即使你不打算公开第三方 COM 类型，使用主互操作程序集也可以使与 COM 组件进行互操作的任务变得更简单。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-112">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="f0fe5-113">但是，此策略不会提供对供应商可能对主互操作程序集中定义的类型所进行的更改的隔离。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-113">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="f0fe5-114">当你的应用程序需要此类隔离时，请生成自己的互操作程序集，而不是使用主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-114">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>

 <span data-ttu-id="f0fe5-115">必须在开发计算机上注册所有需要的主互操作程序集，然后才能通过 Visual Studio 引用它们。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-115">You must register all acquired primary interop assemblies on your development computer before you can reference them with Visual Studio.</span></span> <span data-ttu-id="f0fe5-116">Visual Studio 在你第一次从 COM 类型库引用类型时会查找并使用主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-116">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="f0fe5-117">如果 Visual Studio 找不到与该类型库关联的主互操作程序集，它会提示你获取它，或提出创建一个互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-117">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="f0fe5-118">同样，[类型库导入程序 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 也使用注册表来定位主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-118">Likewise, the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>

 <span data-ttu-id="f0fe5-119">尽管没有必要注册主互操作程序集（除非你打算使用 Visual Studio），但注册可提供两大好处：</span><span class="sxs-lookup"><span data-stu-id="f0fe5-119">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>

- <span data-ttu-id="f0fe5-120">在原始类型库的注册表项下清楚地标记已注册的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-120">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="f0fe5-121">注册是在你的计算机上定位主互操作程序集的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-121">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>

- <span data-ttu-id="f0fe5-122">如果在将来某个时间你使用 Visual Studio 引用具有未注册的主互操作程序集的类型，可以避免意外地生成和使用新的互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-122">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>

<span data-ttu-id="f0fe5-123">使用[程序集注册工具 (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) 注册主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-123">Use the [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>

## <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="f0fe5-124">注册主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="f0fe5-124">To register a primary interop assembly</span></span>

1. <span data-ttu-id="f0fe5-125">在命令提示符处，键入：</span><span class="sxs-lookup"><span data-stu-id="f0fe5-125">At the command prompt, type:</span></span>

     <span data-ttu-id="f0fe5-126">regasm assemblyname</span><span class="sxs-lookup"><span data-stu-id="f0fe5-126">**regasm** *assemblyname*</span></span>

     <span data-ttu-id="f0fe5-127">在此命令中，assemblyname 是已注册的程序集的文件名。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-127">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="f0fe5-128">Regasm.exe 会在与原始类型库相同的注册表项下为主互操作程序集添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-128">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>

## <a name="example"></a><span data-ttu-id="f0fe5-129">示例</span><span class="sxs-lookup"><span data-stu-id="f0fe5-129">Example</span></span>
 <span data-ttu-id="f0fe5-130">下列示例注册 `CompanyA.UtilLib.dll` 主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f0fe5-130">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a><span data-ttu-id="f0fe5-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="f0fe5-131">See also</span></span>

- <span data-ttu-id="f0fe5-132">[用主互操作程序集编程](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0fe5-132">[Programming with Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))</span></span>
- <span data-ttu-id="f0fe5-133">[定位主互操作程序集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0fe5-133">[Locating Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))</span></span>
- <span data-ttu-id="f0fe5-134">[重新分发主互操作程序集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0fe5-134">[Redistributing Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))</span></span>
