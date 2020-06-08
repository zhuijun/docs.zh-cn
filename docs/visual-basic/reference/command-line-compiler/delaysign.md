---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: c9bb302e2b34ebe1f51cf39bb3db1094d420d7f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408694"
---
# <a name="-delaysign"></a><span data-ttu-id="f405b-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="f405b-102">-delaysign</span></span>

<span data-ttu-id="f405b-103">指定程序集是完全签名的还是部分签名的。</span><span class="sxs-lookup"><span data-stu-id="f405b-103">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="f405b-104">语法</span><span class="sxs-lookup"><span data-stu-id="f405b-104">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="f405b-105">自变量</span><span class="sxs-lookup"><span data-stu-id="f405b-105">Arguments</span></span>

<span data-ttu-id="f405b-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f405b-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="f405b-107">可选。</span><span class="sxs-lookup"><span data-stu-id="f405b-107">Optional.</span></span> <span data-ttu-id="f405b-108">如果需要完全签名的程序集，则使用 `-delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="f405b-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="f405b-109">如果希望将公钥置于程序集中，并为签名的哈希保留空间，请使用 `-delaysign+`。</span><span class="sxs-lookup"><span data-stu-id="f405b-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="f405b-110">默认值为 `-delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="f405b-110">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f405b-111">备注</span><span class="sxs-lookup"><span data-stu-id="f405b-111">Remarks</span></span>

<span data-ttu-id="f405b-112">除非与 [-keyfile](keyfile.md) 或 [-keycontainer](keycontainer.md) 一同使用，否则 `-delaysign` 选项将不起作用。</span><span class="sxs-lookup"><span data-stu-id="f405b-112">The `-delaysign` option has no effect unless used with [-keyfile](keyfile.md) or [-keycontainer](keycontainer.md).</span></span>

<span data-ttu-id="f405b-113">在请求完全签名的程序集时，编译器会对包含清单（程序集元数据）的文件进行哈希处理，并使用私钥对哈希进行签名。</span><span class="sxs-lookup"><span data-stu-id="f405b-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="f405b-114">产生的数字签名存储在包含清单的文件中。</span><span class="sxs-lookup"><span data-stu-id="f405b-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="f405b-115">在对程序集延迟签名时，编译器不会计算和存储签名，而是在文件中保留空间，以便稍后可添加签名。</span><span class="sxs-lookup"><span data-stu-id="f405b-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="f405b-116">例如，通过使用 `-delaysign+`，组织中的开发人员可以分发程序集的未签名测试版本，测试人员可以将该版本注册到全局程序集缓存并使用。</span><span class="sxs-lookup"><span data-stu-id="f405b-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="f405b-117">在程序集上完成工作后，负责组织私钥的人员可以对程序集进行完全签名。</span><span class="sxs-lookup"><span data-stu-id="f405b-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="f405b-118">此区室化可防止组织私钥泄露，同时允许所有开发人员处理程序集。</span><span class="sxs-lookup"><span data-stu-id="f405b-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="f405b-119">有关对程序集签名的详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="f405b-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="f405b-120">在 Visual Studio 集成开发环境中设置 -delaysign</span><span class="sxs-lookup"><span data-stu-id="f405b-120">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="f405b-121">在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="f405b-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f405b-122">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="f405b-122">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="f405b-123">单击“签名”选项卡。 </span><span class="sxs-lookup"><span data-stu-id="f405b-123">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="f405b-124">设置“仅延迟签名”  框中的值。</span><span class="sxs-lookup"><span data-stu-id="f405b-124">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="f405b-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="f405b-125">See also</span></span>

- [<span data-ttu-id="f405b-126">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="f405b-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f405b-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="f405b-127">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="f405b-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="f405b-128">-keycontainer</span></span>](keycontainer.md)
- [<span data-ttu-id="f405b-129">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="f405b-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
