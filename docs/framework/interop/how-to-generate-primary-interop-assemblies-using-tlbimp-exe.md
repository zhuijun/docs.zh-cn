---
title: 如何：使用 Tlbimp.exe 生成主互操作程序集
description: 了解如何使用 Windows SDK 提供的类型库导入程序 (Tlbimp.exe) 来生成主互操作程序集。
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
ms.openlocfilehash: 56ce10e0b6f9be988a06d44550cd3b9dc2efd188
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554151"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="f7c1d-103">如何：使用 Tlbimp.exe 生成主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="f7c1d-103">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>

<span data-ttu-id="f7c1d-104">有两种生成主互操作程序集的方法：</span><span class="sxs-lookup"><span data-stu-id="f7c1d-104">There are two ways to generate a primary interop assembly:</span></span>

- <span data-ttu-id="f7c1d-105">使用由 Windows SDK 提供的[类型库导入程序 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-105">Using the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) provided by the Windows SDK.</span></span>

  <span data-ttu-id="f7c1d-106">生成主互操作程序集最简单的方法是使用 [Tlbimp.exe（类型库导入程序）](../tools/tlbimp-exe-type-library-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-106">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="f7c1d-107">Tlbimp.exe 提供了以下安全措施：</span><span class="sxs-lookup"><span data-stu-id="f7c1d-107">Tlbimp.exe provides the following safeguards:</span></span>

  - <span data-ttu-id="f7c1d-108">在为任何嵌套的类型库引用创建新的互操作程序集之前，检查其他已注册的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-108">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>

  - <span data-ttu-id="f7c1d-109">如果未指定容器或文件名称赋予主互操作程序集文件强名称，则将无法发出主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-109">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>

  - <span data-ttu-id="f7c1d-110">如果省略对依赖程序集的引用，则无法发出主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-110">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>

  - <span data-ttu-id="f7c1d-111">如果将引用添加到不是主互操作程序集的依赖程序集，则无法发出主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-111">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>

- <span data-ttu-id="f7c1d-112">在源代码中使用符合公共语言规范 (CLS)（如 C#）的语言手动创建主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-112">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="f7c1d-113">当类型库不可用时，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-113">This approach is useful when a type library is unavailable.</span></span>

<span data-ttu-id="f7c1d-114">要使用强名称为程序集签名，必须具有加密密钥对。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-114">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="f7c1d-115">有关详细信息，请参阅 [Creating A Key Pair](../../standard/assembly/create-public-private-key-pair.md)（创建密钥对）。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-115">For details, see [Creating A Key Pair](../../standard/assembly/create-public-private-key-pair.md).</span></span>

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="f7c1d-116">若要使用 Tlbimp.exe 生成主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="f7c1d-116">To generate a primary interop assembly using Tlbimp.exe</span></span>

1. <span data-ttu-id="f7c1d-117">在命令提示符处，键入：</span><span class="sxs-lookup"><span data-stu-id="f7c1d-117">At the command prompt, type:</span></span>

    <span data-ttu-id="f7c1d-118">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="f7c1d-118">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>

    <span data-ttu-id="f7c1d-119">在此命令中，tlbfile 是要包含 COM 类型库的文件，filename 是包含密钥对的容器或文件的名称，assemblyname 是要使用强名称签名的程序集的名称  。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-119">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>

<span data-ttu-id="f7c1d-120">主互操作程序集仅可引用其他主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-120">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="f7c1d-121">如果你的程序集从第三方 COM 类型库引用类型，则必须在生成主互操作程序集之前，先从发布服务器上获取主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-121">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="f7c1d-122">如果你是发布者，则必须在生成引用的主互操作程序集之前，生成依赖类型库的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-122">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>

<span data-ttu-id="f7c1d-123">当具有不同于原始类型库的版本号的依赖主互操作程序集安装在当前目录时，此程序集是不可发现的。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-123">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="f7c1d-124">必须在 Windows 注册表中注册此依赖主互操作程序集，或者使用 /reference 选项确保 Tlbimp.exe 可以找到依赖 DLL。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-124">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>

<span data-ttu-id="f7c1d-125">还可以包装类型库的多个版本。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-125">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="f7c1d-126">有关说明，请参阅[如何：包装类型库的多个版本](/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-126">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="f7c1d-127">示例</span><span class="sxs-lookup"><span data-stu-id="f7c1d-127">Example</span></span>

<span data-ttu-id="f7c1d-128">以下示例导入 COM 类型库 `LibUtil.tlb` 并借助密钥文件 `CompanyA.snk` 为程序集 `LibUtil.dll` 签署强名称。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-128">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="f7c1d-129">通过省略特定的命名空间名称，此示例将生成默认的命名空间，`LibUtil`。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-129">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

<span data-ttu-id="f7c1d-130">对于更具描述性的名称（使用 VendorName.LibraryName 命名规则），以下示例将重写默认程序集的文件名和命名空间名称 。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-130">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

<span data-ttu-id="f7c1d-131">以下示例导入引用 `CompanyA.LibUtil.dll` 的 `MyLib.tlb`，并借助密钥文件 `CompanyB.snk` 为程序集 `CompanyB.MyLib.dll` 签署强名称。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-131">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="f7c1d-132">命名空间 `CompanyB.MyLib` 将重写默认的命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="f7c1d-132">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a><span data-ttu-id="f7c1d-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="f7c1d-133">See also</span></span>

- [<span data-ttu-id="f7c1d-134">如何：注册主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="f7c1d-134">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)
