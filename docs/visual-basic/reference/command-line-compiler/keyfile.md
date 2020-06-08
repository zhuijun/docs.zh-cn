---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 3f476f6b6db1a788002a938eb5ae4bbbed7a5dae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408570"
---
# <a name="-keyfile"></a><span data-ttu-id="72bc8-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="72bc8-102">-keyfile</span></span>
<span data-ttu-id="72bc8-103">指定包含密钥或密钥对的文件从而为程序集赋予强名称。</span><span class="sxs-lookup"><span data-stu-id="72bc8-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72bc8-104">语法</span><span class="sxs-lookup"><span data-stu-id="72bc8-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="72bc8-105">自变量</span><span class="sxs-lookup"><span data-stu-id="72bc8-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="72bc8-106">必需。</span><span class="sxs-lookup"><span data-stu-id="72bc8-106">Required.</span></span> <span data-ttu-id="72bc8-107">包含密钥的文件。</span><span class="sxs-lookup"><span data-stu-id="72bc8-107">File that contains the key.</span></span> <span data-ttu-id="72bc8-108">如果文件名包含空格，则将名称括在引号内 (" ")。</span><span class="sxs-lookup"><span data-stu-id="72bc8-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72bc8-109">备注</span><span class="sxs-lookup"><span data-stu-id="72bc8-109">Remarks</span></span>  
 <span data-ttu-id="72bc8-110">编译器在程序集清单中插入公钥，然后使用私钥对最终的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="72bc8-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="72bc8-111">若要生成密钥文件，请在命令行键入 `sn -k file`。</span><span class="sxs-lookup"><span data-stu-id="72bc8-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="72bc8-112">有关详细信息，请参阅 [Sn.exe（强名称工具）](../../../framework/tools/sn-exe-strong-name-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="72bc8-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="72bc8-113">如果使用 `-target:module` 进行编译，密钥文件的名称将保存在模块中，并在使用 [-addmodule](addmodule.md) 编译程序集时包含到创建的程序集中。</span><span class="sxs-lookup"><span data-stu-id="72bc8-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="72bc8-114">也可以使用 [-keycontainer](keycontainer.md) 将加密信息传递给编译器。</span><span class="sxs-lookup"><span data-stu-id="72bc8-114">You can also pass your encryption information to the compiler with [-keycontainer](keycontainer.md).</span></span> <span data-ttu-id="72bc8-115">如果需要部分签名的程序集，请使用 [-delaysign](delaysign.md)。</span><span class="sxs-lookup"><span data-stu-id="72bc8-115">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="72bc8-116">还可以将此选项指定为任何 Microsoft 中间语言模块的源代码中的自定义属性 (<xref:System.Reflection.AssemblyKeyFileAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="72bc8-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="72bc8-117">如果在同一编译中同时指定 `-keyfile` 和 [-keycontainer](keycontainer.md)（通过命令行选项或通过自定义特性），则编译器将首先尝试密钥容器。</span><span class="sxs-lookup"><span data-stu-id="72bc8-117">In case both `-keyfile` and [-keycontainer](keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="72bc8-118">如果成功，则使用密钥容器中的信息对程序集签名。</span><span class="sxs-lookup"><span data-stu-id="72bc8-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="72bc8-119">如果编译器没有找到密钥容器，它将尝试用 `-keyfile` 指定的文件。</span><span class="sxs-lookup"><span data-stu-id="72bc8-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="72bc8-120">如果成功，则使用密钥文件中的信息对程序集签名，并且将密钥信息安装到密钥容器中（类似于 `sn -i`），以便在下一次编译中，密钥容器选项将生效。</span><span class="sxs-lookup"><span data-stu-id="72bc8-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="72bc8-121">请注意，密钥文件可能仅包含公钥。</span><span class="sxs-lookup"><span data-stu-id="72bc8-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="72bc8-122">有关对程序集签名的详细信息，请参阅[创建和使用具有强名称的程序集](../../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="72bc8-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72bc8-123">`-keyfile` 选项不适用于 Visual Studio 开发环境内，仅当从命令行编译时可用。</span><span class="sxs-lookup"><span data-stu-id="72bc8-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="72bc8-124">示例</span><span class="sxs-lookup"><span data-stu-id="72bc8-124">Example</span></span>

<span data-ttu-id="72bc8-125">下面的代码编译源文件 `Input.vb`，并指定一个密钥文件。</span><span class="sxs-lookup"><span data-stu-id="72bc8-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="72bc8-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="72bc8-126">See also</span></span>

- [<span data-ttu-id="72bc8-127">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="72bc8-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="72bc8-128">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="72bc8-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="72bc8-129">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72bc8-129">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="72bc8-130">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="72bc8-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
