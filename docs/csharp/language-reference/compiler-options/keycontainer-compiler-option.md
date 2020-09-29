---
description: -keycontainer（C# 编译器选项）
title: -keycontainer（C# 编译器选项）
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 93ee5cd755a4fd6918d2a5825b63151a201a8f6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152463"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="0f98e-103">-keycontainer（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="0f98e-103">-keycontainer (C# Compiler Options)</span></span>

<span data-ttu-id="0f98e-104">指定加密密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="0f98e-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f98e-105">语法</span><span class="sxs-lookup"><span data-stu-id="0f98e-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f98e-106">自变量</span><span class="sxs-lookup"><span data-stu-id="0f98e-106">Arguments</span></span>  

 `string`  
 <span data-ttu-id="0f98e-107">强名称密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="0f98e-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f98e-108">备注</span><span class="sxs-lookup"><span data-stu-id="0f98e-108">Remarks</span></span>  

 <span data-ttu-id="0f98e-109">当使用“-keycontainer”\*\*\*\* 选项时，编译器将创建一个可共享的组件。</span><span class="sxs-lookup"><span data-stu-id="0f98e-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="0f98e-110">编译器在程序集清单中插入指定容器的公钥，然后使用私钥对最终的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="0f98e-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="0f98e-111">若要生成密钥文件，请在命令行键入 `sn -k file`。</span><span class="sxs-lookup"><span data-stu-id="0f98e-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="0f98e-112">`sn -i` 将密钥对安装到容器中。</span><span class="sxs-lookup"><span data-stu-id="0f98e-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="0f98e-113">编译器在 CoreCLR 上运行时，不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="0f98e-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="0f98e-114">在生成 CoreCLR 时对程序集进行签名，请使用 [-keyfile](keyfile-compiler-option.md) 选项。</span><span class="sxs-lookup"><span data-stu-id="0f98e-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="0f98e-115">如果使用 [-target:module](./target-module-compiler-option.md) 进行编译，当使用 [-addmodule](./addmodule-compiler-option.md) 将此模块编译到程序集时，密钥文件的名称将保存在模块中，且会并入程序集。</span><span class="sxs-lookup"><span data-stu-id="0f98e-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="0f98e-116">还可以将此选项指定为任何 Microsoft 中间语言 (MSIL) 模块的源代码中的自定义特性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="0f98e-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="0f98e-117">此外，可使用 [-keyfile](./keyfile-compiler-option.md) 将加密信息传递给编译器。</span><span class="sxs-lookup"><span data-stu-id="0f98e-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="0f98e-118">如果希望将公钥添加到程序集清单，但希望测试完程序集后再对其签名，请使用 [-delaysign](./delaysign-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="0f98e-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="0f98e-119">有关详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)和[延迟为程序集签名](../../../standard/assembly/delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="0f98e-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0f98e-120">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="0f98e-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="0f98e-121">Visual Studio 开发环境中尚未提供此编译器选项。</span><span class="sxs-lookup"><span data-stu-id="0f98e-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="0f98e-122">可通过 <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> 以编程方式访问此编译器选项。</span><span class="sxs-lookup"><span data-stu-id="0f98e-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f98e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f98e-123">See also</span></span>

- [<span data-ttu-id="0f98e-124">C# 编译器 -keyfile 选项</span><span class="sxs-lookup"><span data-stu-id="0f98e-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="0f98e-125">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="0f98e-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="0f98e-126">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="0f98e-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
