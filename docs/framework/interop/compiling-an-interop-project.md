---
title: 编译互操作项目
description: 查看如何编译 COM 互操作项目，如果它们引用包含导入 COM 类型的一个或多个程序集，则这些项目可以像托管项目一样进行编译。
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: 1cf5bdbedd53227e812b0d2ed97778ab34a81444
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557092"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="efdb4-103">编译互操作项目</span><span class="sxs-lookup"><span data-stu-id="efdb4-103">Compiling an Interop Project</span></span>

<span data-ttu-id="efdb4-104">如果 COM 互操作项目引用一个或多个包含导入 COM 类型的程序集，则可以像其他任何托管项目一样进行编译。</span><span class="sxs-lookup"><span data-stu-id="efdb4-104">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="efdb4-105">可以在 Visual Studio 等开发环境中或使用命令行编译器时引用互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="efdb4-105">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="efdb4-106">无论哪种情况，若要正确编译，互操作程序集必须与其他项目文件位于同一个目录中。</span><span class="sxs-lookup"><span data-stu-id="efdb4-106">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="efdb4-107">可以通过以下两种方式引用互操作程序集：</span><span class="sxs-lookup"><span data-stu-id="efdb4-107">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="efdb4-108">嵌入互操作类型：从 .NET Framework 4 和 Visual Studio 2010 开始，可以指示编译器将类型信息从互操作程序集嵌入到可执行文件中。</span><span class="sxs-lookup"><span data-stu-id="efdb4-108">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="efdb4-109">这是推荐采用的方法。</span><span class="sxs-lookup"><span data-stu-id="efdb4-109">This is the recommended technique.</span></span>

- <span data-ttu-id="efdb4-110">部署互操作程序集：可通过这种方式创建对互操作程序集的标准引用。</span><span class="sxs-lookup"><span data-stu-id="efdb4-110">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="efdb4-111">这种情况下，互操作程序集必须与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="efdb4-111">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="efdb4-112">这两种方法之间的差异在[在托管代码中使用 COM 类型 ](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))中有更详细的讨论。</span><span class="sxs-lookup"><span data-stu-id="efdb4-112">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="efdb4-113">有关如何使用 Visual Studio 嵌入互操作类型，请参阅[演练：在 Visual Studio 中嵌入托管程序集中的类型](../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="efdb4-113">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="efdb4-114">若要使用命令行编译器引用互操作程序集，并将类型信息嵌入可执行文件中，请使用 [-link（C# 编译器选项）](../../csharp/language-reference/compiler-options/link-compiler-option.md)或 [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) 编译器开关并指定互操作程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="efdb4-114">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="efdb4-115">Visual C++ 应用程序无法嵌入类型信息，但它们可以与应用程序或加载项进行互操作。</span><span class="sxs-lookup"><span data-stu-id="efdb4-115">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="efdb4-116">若要编译部署时包括主互操作程序集的应用程序，请使用“/reference”编译器开关并指定互操作程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="efdb4-116">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="efdb4-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="efdb4-117">See also</span></span>

- [<span data-ttu-id="efdb4-118">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="efdb4-118">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="efdb4-119">语言独立性和与语言无关的组件</span><span class="sxs-lookup"><span data-stu-id="efdb4-119">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="efdb4-120">[在托管代码中使用 COM 类型](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="efdb4-120">[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="efdb4-121">演练：在 Visual Studio 中嵌入托管程序集中的类型</span><span class="sxs-lookup"><span data-stu-id="efdb4-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="efdb4-122">将类型库作为程序集导入</span><span class="sxs-lookup"><span data-stu-id="efdb4-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
