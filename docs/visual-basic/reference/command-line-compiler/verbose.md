---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403026"
---
# <a name="-verbose"></a><span data-ttu-id="3286b-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="3286b-102">-verbose</span></span>
<span data-ttu-id="3286b-103">导致编译器生成详细状态和错误消息。</span><span class="sxs-lookup"><span data-stu-id="3286b-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3286b-104">语法</span><span class="sxs-lookup"><span data-stu-id="3286b-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3286b-105">自变量</span><span class="sxs-lookup"><span data-stu-id="3286b-105">Arguments</span></span>  
 <span data-ttu-id="3286b-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="3286b-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="3286b-107">可选。</span><span class="sxs-lookup"><span data-stu-id="3286b-107">Optional.</span></span> <span data-ttu-id="3286b-108">指定 `-verbose` 与指定 `-verbose+` 相同，这将导致编译器发出详细消息。</span><span class="sxs-lookup"><span data-stu-id="3286b-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="3286b-109">此选项的默认值为 `-verbose-`。</span><span class="sxs-lookup"><span data-stu-id="3286b-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3286b-110">备注</span><span class="sxs-lookup"><span data-stu-id="3286b-110">Remarks</span></span>  
 <span data-ttu-id="3286b-111">`-verbose` 选项显示编译器发出的错误总数的相关信息，报告模块正在加载的程序集，并显示当前正在编译的文件。</span><span class="sxs-lookup"><span data-stu-id="3286b-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3286b-112">`-verbose` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="3286b-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3286b-113">示例</span><span class="sxs-lookup"><span data-stu-id="3286b-113">Example</span></span>  
 <span data-ttu-id="3286b-114">下面的代码编译 `In.vb`，并指示编译器显示详细状态信息。</span><span class="sxs-lookup"><span data-stu-id="3286b-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3286b-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="3286b-115">See also</span></span>

- [<span data-ttu-id="3286b-116">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="3286b-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3286b-117">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="3286b-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
