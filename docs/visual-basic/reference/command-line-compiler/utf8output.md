---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 2faebb7870cbc019d479215563261f331f9fddcf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085069"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="9863c-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9863c-102">-utf8output (Visual Basic)</span></span>

<span data-ttu-id="9863c-103">显示使用 UTF-8 编码的编译器输出。</span><span class="sxs-lookup"><span data-stu-id="9863c-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9863c-104">语法</span><span class="sxs-lookup"><span data-stu-id="9863c-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9863c-105">自变量</span><span class="sxs-lookup"><span data-stu-id="9863c-105">Arguments</span></span>  

 <span data-ttu-id="9863c-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="9863c-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="9863c-107">可选。</span><span class="sxs-lookup"><span data-stu-id="9863c-107">Optional.</span></span> <span data-ttu-id="9863c-108">此选项的默认值为 `-utf8output-`，这意味着编译器输出不使用 UTF-8 编码。</span><span class="sxs-lookup"><span data-stu-id="9863c-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="9863c-109">指定 `-utf8output` 与指定 `-utf8output+` 相同。</span><span class="sxs-lookup"><span data-stu-id="9863c-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9863c-110">备注</span><span class="sxs-lookup"><span data-stu-id="9863c-110">Remarks</span></span>  

 <span data-ttu-id="9863c-111">在某些国际配置中，编译器输出无法在控制台上正确显示。</span><span class="sxs-lookup"><span data-stu-id="9863c-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="9863c-112">在这种情况下，请使用 `-utf8output`，并将编译器输出重定向到文件。</span><span class="sxs-lookup"><span data-stu-id="9863c-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9863c-113">`-utf8output` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="9863c-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9863c-114">示例</span><span class="sxs-lookup"><span data-stu-id="9863c-114">Example</span></span>  

 <span data-ttu-id="9863c-115">下面的代码编译 `In.vb`，并指示编译器使用 UTF-8 编码显示输出。</span><span class="sxs-lookup"><span data-stu-id="9863c-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9863c-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="9863c-116">See also</span></span>

- [<span data-ttu-id="9863c-117">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="9863c-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9863c-118">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="9863c-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
