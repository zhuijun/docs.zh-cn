---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 7ded2b7d102430d8d4e545da5ab6ce8bafe3609e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095416"
---
# <a name="-recurse"></a><span data-ttu-id="e7f9c-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="e7f9c-102">-recurse</span></span>

<span data-ttu-id="e7f9c-103">在指定目录或项目目录的所有子目录中编译源代码文件。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f9c-104">语法</span><span class="sxs-lookup"><span data-stu-id="e7f9c-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7f9c-105">自变量</span><span class="sxs-lookup"><span data-stu-id="e7f9c-105">Arguments</span></span>  

 `dir`  
 <span data-ttu-id="e7f9c-106">可选。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-106">Optional.</span></span> <span data-ttu-id="e7f9c-107">希望从中开始搜索的目录。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="e7f9c-108">如未指定目录，搜索将从项目目录开始。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="e7f9c-109">必需。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-109">Required.</span></span> <span data-ttu-id="e7f9c-110">要搜索的文件。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-110">The file(s) to search for.</span></span> <span data-ttu-id="e7f9c-111">允许通配符。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7f9c-112">备注</span><span class="sxs-lookup"><span data-stu-id="e7f9c-112">Remarks</span></span>  

 <span data-ttu-id="e7f9c-113">可在文件名中使用通配符，对项目目录中的所有匹配文件进行编译，而无需使用 `-recurse`。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="e7f9c-114">如果未指定输出文件名，编译器会将输出文件名建立在处理的第一个输入文件的基础上。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="e7f9c-115">这通常是按字母顺序查看时所编译文件列表中的第一个文件。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="e7f9c-116">因此，最好使用 `-out` 选项来指定输出文件。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7f9c-117">`-recurse` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f9c-118">示例</span><span class="sxs-lookup"><span data-stu-id="e7f9c-118">Example</span></span>  

 <span data-ttu-id="e7f9c-119">以下命令编译当前目录中的所有 Visual Basic 文件。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="e7f9c-120">以下命令编译 `Test\ABC` 目录及其下任何目录中的所有 Visual Basic 文件，然后生成 `Test.ABC.dll`。</span><span class="sxs-lookup"><span data-stu-id="e7f9c-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7f9c-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7f9c-121">See also</span></span>

- [<span data-ttu-id="e7f9c-122">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="e7f9c-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e7f9c-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7f9c-123">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="e7f9c-124">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="e7f9c-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
