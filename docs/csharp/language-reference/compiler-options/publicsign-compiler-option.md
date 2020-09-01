---
description: -publicsign（C# 编译器选项）
title: -publicsign（C# 编译器选项）
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124807"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="03862-103">-publicsign（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="03862-103">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="03862-104">此选项会导致编译器应用公钥，但不会实际对程序集签名。</span><span class="sxs-lookup"><span data-stu-id="03862-104">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="03862-105"> -publicsign 选项还会在程序集中设置位，以告知运行时该文件实际已签名。</span><span class="sxs-lookup"><span data-stu-id="03862-105">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="03862-106">语法</span><span class="sxs-lookup"><span data-stu-id="03862-106">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="03862-107">参数</span><span class="sxs-lookup"><span data-stu-id="03862-107">Arguments</span></span>

<span data-ttu-id="03862-108">无。</span><span class="sxs-lookup"><span data-stu-id="03862-108">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="03862-109">备注</span><span class="sxs-lookup"><span data-stu-id="03862-109">Remarks</span></span>

<span data-ttu-id="03862-110"> -publicsign 选项需要使用 [-keyfile](keyfile-compiler-option.md) 或 [-keycontainer](keycontainer-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="03862-110">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="03862-111"> keyfile 或  keycontainer 选项指定公钥。</span><span class="sxs-lookup"><span data-stu-id="03862-111">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="03862-112"> -publicsign 和 -delaysign  选项互斥。</span><span class="sxs-lookup"><span data-stu-id="03862-112">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="03862-113">公共签名有时称为“假签名”或“OSS 签名”，它包括输出程序集中的公钥并设置“已签名”标记，但实际上并未使用私钥对程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="03862-113">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="03862-114">这对开放源代码项目非常有用，人们希望生成与已发布的“完全签名”程序集兼容的程序集，但无权访问用于对程序集进行签名的私钥。</span><span class="sxs-lookup"><span data-stu-id="03862-114">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="03862-115">由于几乎没有使用者实际需要检查程序集是否完全签名，因此这些公开生成的程序集几乎适用于每个使用完全签名程序集的方案。</span><span class="sxs-lookup"><span data-stu-id="03862-115">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a><span data-ttu-id="03862-116">在 csproj 文件中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="03862-116">To set this compiler option in a csproj file</span></span>

<span data-ttu-id="03862-117">打开项目的 csproj 文件，并添加以下元素：</span><span class="sxs-lookup"><span data-stu-id="03862-117">Open the .csproj file for a project, and add the following element:</span></span>

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a><span data-ttu-id="03862-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03862-118">See also</span></span>

- [<span data-ttu-id="03862-119">C# 编译器 -delaysign 选项</span><span class="sxs-lookup"><span data-stu-id="03862-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="03862-120">C# 编译器 -keyfile 选项</span><span class="sxs-lookup"><span data-stu-id="03862-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="03862-121">C# 编译器 -keycontainer 选项</span><span class="sxs-lookup"><span data-stu-id="03862-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="03862-122">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="03862-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="03862-123">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="03862-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
