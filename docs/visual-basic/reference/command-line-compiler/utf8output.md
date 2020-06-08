---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403052"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="bcb6d-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcb6d-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="bcb6d-103">显示使用 UTF-8 编码的编译器输出。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb6d-104">语法</span><span class="sxs-lookup"><span data-stu-id="bcb6d-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bcb6d-105">自变量</span><span class="sxs-lookup"><span data-stu-id="bcb6d-105">Arguments</span></span>  
 <span data-ttu-id="bcb6d-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="bcb6d-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="bcb6d-107">可选。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-107">Optional.</span></span> <span data-ttu-id="bcb6d-108">此选项的默认值为 `-utf8output-`，这意味着编译器输出不使用 UTF-8 编码。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="bcb6d-109">指定 `-utf8output` 与指定 `-utf8output+` 相同。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcb6d-110">备注</span><span class="sxs-lookup"><span data-stu-id="bcb6d-110">Remarks</span></span>  
 <span data-ttu-id="bcb6d-111">在某些国际配置中，编译器输出无法在控制台上正确显示。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="bcb6d-112">在这种情况下，请使用 `-utf8output`，并将编译器输出重定向到文件。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcb6d-113">`-utf8output` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcb6d-114">示例</span><span class="sxs-lookup"><span data-stu-id="bcb6d-114">Example</span></span>  
 <span data-ttu-id="bcb6d-115">下面的代码编译 `In.vb`，并指示编译器使用 UTF-8 编码显示输出。</span><span class="sxs-lookup"><span data-stu-id="bcb6d-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcb6d-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="bcb6d-116">See also</span></span>

- [<span data-ttu-id="bcb6d-117">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="bcb6d-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bcb6d-118">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="bcb6d-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
