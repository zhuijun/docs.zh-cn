---
description: -keyfile（C# 编译器选项）
title: -keyfile（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 5af40da18895d47933cb809d710e31a40f14513b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152424"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="2f727-103">-keyfile（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="2f727-103">-keyfile (C# Compiler Options)</span></span>

<span data-ttu-id="2f727-104">指定包含加密密钥的文件名。</span><span class="sxs-lookup"><span data-stu-id="2f727-104">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f727-105">语法</span><span class="sxs-lookup"><span data-stu-id="2f727-105">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f727-106">自变量</span><span class="sxs-lookup"><span data-stu-id="2f727-106">Arguments</span></span>  
  
|<span data-ttu-id="2f727-107">术语</span><span class="sxs-lookup"><span data-stu-id="2f727-107">Term</span></span>|<span data-ttu-id="2f727-108">定义</span><span class="sxs-lookup"><span data-stu-id="2f727-108">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="2f727-109">含有强名称密钥的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="2f727-109">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f727-110">备注</span><span class="sxs-lookup"><span data-stu-id="2f727-110">Remarks</span></span>  

 <span data-ttu-id="2f727-111">使用此选项时，编译器在程序集清单中插入指定字段的公钥，然后使用私钥对最终的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="2f727-111">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="2f727-112">若要生成密钥文件，请在命令行键入 sn-k `file`。</span><span class="sxs-lookup"><span data-stu-id="2f727-112">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="2f727-113">如果使用 -target:module 进行编译，密钥文件的名称将保存在模块中，并在使用 [-addmodule](./addmodule-compiler-option.md) 编译程序集时包含到创建的程序集中。</span><span class="sxs-lookup"><span data-stu-id="2f727-113">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="2f727-114">也可以使用 [-keycontainer](./keycontainer-compiler-option.md) 将加密信息传递给编译器。</span><span class="sxs-lookup"><span data-stu-id="2f727-114">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="2f727-115">如果需要部分签名的程序集，请使用 [-delaysign](./delaysign-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="2f727-115">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="2f727-116">如果在同一编译中同时指定 -keyfile 和 -keycontainer（通过命令行选项或通过自定义特性），则 Al.exe 将首先尝试用密钥容器。</span><span class="sxs-lookup"><span data-stu-id="2f727-116">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="2f727-117">如果成功，则使用密钥容器中的信息对程序集签名。</span><span class="sxs-lookup"><span data-stu-id="2f727-117">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="2f727-118">如果编译器没有找到密钥容器，它将尝试用 -keyfile 指定的文件。</span><span class="sxs-lookup"><span data-stu-id="2f727-118">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="2f727-119">如果成功，则使用密钥文件中的信息对程序集签名，并且将密钥信息安装到密钥容器中（类似于 sn -i），以便在下一次编译中，密钥容器选项将生效。</span><span class="sxs-lookup"><span data-stu-id="2f727-119">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="2f727-120">请注意，密钥文件可能仅包含公钥。</span><span class="sxs-lookup"><span data-stu-id="2f727-120">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="2f727-121">有关详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)和[延迟为程序集签名](../../../standard/assembly/delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="2f727-121">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2f727-122">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="2f727-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2f727-123">打开项目的“属性” \*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="2f727-123">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="2f727-124">单击“签名”\*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="2f727-124">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="2f727-125">修改“选择强名称密钥文件”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="2f727-125">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="2f727-126">可通过 <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> 以编程方式访问此编译器选项。</span><span class="sxs-lookup"><span data-stu-id="2f727-126">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f727-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f727-127">See also</span></span>

- [<span data-ttu-id="2f727-128">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="2f727-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2f727-129">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="2f727-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
