---
description: -delaysign（C# 编译器选项）
title: -delaysign（C# 编译器选项）
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 5512ebeca4672f5d69852ab07c3f3fa40c305327
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125834"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="86bcc-103">-delaysign（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="86bcc-103">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="86bcc-104">此选项会使编译器在输出文件中保留空间，以便以后添加数字签名。</span><span class="sxs-lookup"><span data-stu-id="86bcc-104">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="86bcc-105">语法</span><span class="sxs-lookup"><span data-stu-id="86bcc-105">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="86bcc-106">自变量</span><span class="sxs-lookup"><span data-stu-id="86bcc-106">Arguments</span></span>

<span data-ttu-id="86bcc-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="86bcc-107">`+` &#124; `-`</span></span>

<span data-ttu-id="86bcc-108">如果需要完全签名的程序集，请使用 -delaysign-。</span><span class="sxs-lookup"><span data-stu-id="86bcc-108">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="86bcc-109">如果仅需要将公钥置于程序集中，则使用 -delaysign+。</span><span class="sxs-lookup"><span data-stu-id="86bcc-109">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="86bcc-110">默认值为 -delaysign-。</span><span class="sxs-lookup"><span data-stu-id="86bcc-110">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="86bcc-111">备注</span><span class="sxs-lookup"><span data-stu-id="86bcc-111">Remarks</span></span>

<span data-ttu-id="86bcc-112">除非与 [-keyfile](./keyfile-compiler-option.md) 或 [-keycontainer](./keycontainer-compiler-option.md) 一同使用，否则 -delaysign 选项将不起作用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="86bcc-112">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="86bcc-113">\*\*\*\*-Delaysign 和 -publicsign \*\*\*\* 选项互斥。</span><span class="sxs-lookup"><span data-stu-id="86bcc-113">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="86bcc-114">在请求完全签名的程序集时，编译器会对包含清单（程序集元数据）的文件进行哈希处理，并使用私钥对哈希进行签名。</span><span class="sxs-lookup"><span data-stu-id="86bcc-114">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="86bcc-115">该操作创建存储在包含清单的文件中的数字签名。</span><span class="sxs-lookup"><span data-stu-id="86bcc-115">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="86bcc-116">在对程序集延迟签名时，编译器不会计算和存储签名，而只是在文件中保留空间以便稍后可添加签名。</span><span class="sxs-lookup"><span data-stu-id="86bcc-116">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="86bcc-117">例如，使用 -delaysign+ 可允许测试人员将程序集放入全局缓存中。</span><span class="sxs-lookup"><span data-stu-id="86bcc-117">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="86bcc-118">测试完成后，可使用[程序集链接器](../../../framework/tools/al-exe-assembly-linker.md)实用工具将私钥置于程序集中，对程序集进行完全签名。</span><span class="sxs-lookup"><span data-stu-id="86bcc-118">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="86bcc-119">有关详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)和[延迟为程序集签名](../../../standard/assembly/delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="86bcc-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="86bcc-120">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="86bcc-120">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="86bcc-121">打开项目的“属性” \*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="86bcc-121">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="86bcc-122">修改“仅延迟签名”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="86bcc-122">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="86bcc-123">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。</span><span class="sxs-lookup"><span data-stu-id="86bcc-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="86bcc-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86bcc-124">See also</span></span>

- [<span data-ttu-id="86bcc-125">C# -publicsign 选项</span><span class="sxs-lookup"><span data-stu-id="86bcc-125">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="86bcc-126">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="86bcc-126">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="86bcc-127">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="86bcc-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
