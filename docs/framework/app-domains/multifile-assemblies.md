---
title: 多文件程序集
description: 通过使用命令行编译器或 Visual Studio 和 Visual C++ 来使用面向 .NET 的多文件程序集。 程序集中的文件必须包含程序集清单。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: a5fb41b3b136a325e6b8658da521cba3176e929f
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104637"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="69ecf-104">多文件程序集</span><span class="sxs-lookup"><span data-stu-id="69ecf-104">Multifile assemblies</span></span>

<span data-ttu-id="69ecf-105">可以使用命令行编译器或 Visual Studio 和 Visual C++，创建面向 .NET Framework 的多文件程序集。</span><span class="sxs-lookup"><span data-stu-id="69ecf-105">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="69ecf-106">程序集中的一个文件必须包含程序集清单。</span><span class="sxs-lookup"><span data-stu-id="69ecf-106">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="69ecf-107">启动应用程序的程序集还必须包含入口点，如 `Main` 或 `WinMain` 方法。</span><span class="sxs-lookup"><span data-stu-id="69ecf-107">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="69ecf-108">例如，假设应用程序包含两个代码模块：Client.cs 和 Stringer.cs 。</span><span class="sxs-lookup"><span data-stu-id="69ecf-108">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="69ecf-109">Stringer.cs 创建由 Client.cs 中的代码引用的 `myStringer` 命名空间 。</span><span class="sxs-lookup"><span data-stu-id="69ecf-109">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="69ecf-110">Client.cs 包含作为应用程序入口点的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="69ecf-110">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="69ecf-111">在此示例中，编译两个代码模块，然后创建一个包含程序集清单的第三个文件，用于启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="69ecf-111">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="69ecf-112">程序集清单引用 Client 和 Stringer 这两个模块 。</span><span class="sxs-lookup"><span data-stu-id="69ecf-112">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="69ecf-113">多文件程序集只能有一个入口点，即使该程序集具有多个代码模块。</span><span class="sxs-lookup"><span data-stu-id="69ecf-113">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="69ecf-114">创建多文件程序集的原因有以下几个：</span><span class="sxs-lookup"><span data-stu-id="69ecf-114">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="69ecf-115">合并用不同语言编写的模块。</span><span class="sxs-lookup"><span data-stu-id="69ecf-115">To combine modules written in different languages.</span></span> <span data-ttu-id="69ecf-116">这是创建多文件程序集最常见的原因。</span><span class="sxs-lookup"><span data-stu-id="69ecf-116">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="69ecf-117">将不常用的类型放在只在需要时才下载的模块中，以优化应用程序的下载。</span><span class="sxs-lookup"><span data-stu-id="69ecf-117">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="69ecf-118">如果要创建将使用 `<object>` 标记和 Microsoft Internet Explorer 来下载的应用程序，创建多文件程序集就很重要。</span><span class="sxs-lookup"><span data-stu-id="69ecf-118">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="69ecf-119">在此方案中，创建与只包含程序集清单的代码模块分开的文件。</span><span class="sxs-lookup"><span data-stu-id="69ecf-119">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="69ecf-120">Internet Explorer 首先下载程序集清单，然后创建辅助线程以下载所需的任何其他模块或程序集。</span><span class="sxs-lookup"><span data-stu-id="69ecf-120">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="69ecf-121">由于正在下载包含程序集清单的文件，Internet Explorer 将不响应用户的输入。</span><span class="sxs-lookup"><span data-stu-id="69ecf-121">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="69ecf-122">包含程序集清单的文件越小，Internet Explorer 不作响应的时间就越短。</span><span class="sxs-lookup"><span data-stu-id="69ecf-122">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="69ecf-123">合并由多个开发人员编写的代码模块。</span><span class="sxs-lookup"><span data-stu-id="69ecf-123">To combine code modules written by several developers.</span></span> <span data-ttu-id="69ecf-124">虽然每一位开发人员都可以将各个代码模块编译成程序集，但这样会强制一些类型公开（如果所有模块均放在多文件程序集中，则不会公开）。</span><span class="sxs-lookup"><span data-stu-id="69ecf-124">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="69ecf-125">创建程序集后，可为包含程序集清单（并因此包含程序集）的文件签名，或者为文件及程序集指定强名称并将其放在全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="69ecf-125">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="69ecf-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="69ecf-126">See also</span></span>

- [<span data-ttu-id="69ecf-127">如何：生成多文件程序集</span><span class="sxs-lookup"><span data-stu-id="69ecf-127">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="69ecf-128">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="69ecf-128">Program with assemblies</span></span>](../../standard/assembly/index.md)
