---
title: 如何：将程序集安装到全局程序集缓存
description: 将程序集安装到 .NET 中的全局程序集缓存 (GAC)，以供多个应用程序共享。 使用 Windows Installer 或 GAC 实用程序。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104657"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="0ee6c-104">如何：将程序集安装到全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="0ee6c-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="0ee6c-105">全局程序集缓存 (GAC) 存储由多个应用程序共享的程序集。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="0ee6c-106">使用以下任一组件将程序集安装到[全局程序集缓存](gac.md)中：</span><span class="sxs-lookup"><span data-stu-id="0ee6c-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="0ee6c-107">Windows 安装程序</span><span class="sxs-lookup"><span data-stu-id="0ee6c-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="0ee6c-108">全局程序集缓存工具</span><span class="sxs-lookup"><span data-stu-id="0ee6c-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="0ee6c-109">可以只将强名称程序集安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="0ee6c-110">有关如何创建强名称程序集的信息，请参阅[如何：使用强名称为程序集签名](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="0ee6c-111">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="0ee6c-111">Windows Installer</span></span>

<span data-ttu-id="0ee6c-112">建议使用 [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)（即 Windows 安装引擎）将程序集添加到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="0ee6c-113">Windows Installer 可提供全局程序集缓存中程序集的引用计数，还具有其他优点。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="0ee6c-114">若要创建 Windows Installer 的安装程序包，请使用[适用于 Visual Studio 2017 的 WiX 工具集扩展](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="0ee6c-115">全局程序集缓存工具</span><span class="sxs-lookup"><span data-stu-id="0ee6c-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="0ee6c-116">可以使用 [.NET 全局程序集实用程序 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 将程序集添加到全局程序集缓存，并查看全局程序集缓存的内容。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0ee6c-117">Gacutil.exe 仅用于开发目的。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="0ee6c-118">请勿用于将生产程序集安装到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="0ee6c-119">使用 gacutil.exe 在 GAC 中安装程序集的语法如下：</span><span class="sxs-lookup"><span data-stu-id="0ee6c-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="0ee6c-120">在此命令中，\<assembly name> 是要在全局程序集缓存中安装的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="0ee6c-121">如果 gacutil.exe 不在系统路径中，则使用 [VS 开发人员命令提示符\<version>](../tools/developer-command-prompt-for-vs.md) 。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-121">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="0ee6c-122">下面的示例将文件名为 hello.dll 的程序集安装到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="0ee6c-123">在 .NET Framework 的早期版本中，可以使用 Shfusion.dll Windows 外壳扩展通过将程序集拖到“文件资源管理器”来安装这些程序集。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-123">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="0ee6c-124">从 .NET Framework 4 开始，Shfusion.dll 已过时。</span><span class="sxs-lookup"><span data-stu-id="0ee6c-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ee6c-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="0ee6c-125">See also</span></span>

- [<span data-ttu-id="0ee6c-126">使用程序集和全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="0ee6c-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="0ee6c-127">如何：从全局程序集缓存中删除程序集</span><span class="sxs-lookup"><span data-stu-id="0ee6c-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="0ee6c-128">Gacutil.exe（全局程序集缓存工具）</span><span class="sxs-lookup"><span data-stu-id="0ee6c-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="0ee6c-129">如何：使用强名称为程序集签名</span><span class="sxs-lookup"><span data-stu-id="0ee6c-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
