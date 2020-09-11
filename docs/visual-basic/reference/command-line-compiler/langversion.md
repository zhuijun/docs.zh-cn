---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.custom: updateeachrelease
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 9921df0b8bb1a4808528b58a5a38d75e5e3fbdd2
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359254"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="b46d8-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b46d8-102">-langversion (Visual Basic)</span></span>

<span data-ttu-id="b46d8-103">使编译器仅接受包含在指定 Visual Basic 语言版本中的语法。</span><span class="sxs-lookup"><span data-stu-id="b46d8-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46d8-104">语法</span><span class="sxs-lookup"><span data-stu-id="b46d8-104">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="b46d8-105">自变量</span><span class="sxs-lookup"><span data-stu-id="b46d8-105">Arguments</span></span>

 `version`\
 <span data-ttu-id="b46d8-106">必需。</span><span class="sxs-lookup"><span data-stu-id="b46d8-106">Required.</span></span> <span data-ttu-id="b46d8-107">要在编译过程中使用的语言版本。</span><span class="sxs-lookup"><span data-stu-id="b46d8-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="b46d8-108">接受的值为 `9`、`10`、`11`、`12`、`14`、`15`、`15.3`、`15.5`、`16`、`default` 和 `latest`。</span><span class="sxs-lookup"><span data-stu-id="b46d8-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `16`, `default` and `latest`.</span></span>

 <span data-ttu-id="b46d8-109">还可以使用 `.0` 作为次要版本来指定任何整数，例如 `11.0`。</span><span class="sxs-lookup"><span data-stu-id="b46d8-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="b46d8-110">通过在命令行上指定 `-langversion:?`，可以查看所有可能值的列表。</span><span class="sxs-lookup"><span data-stu-id="b46d8-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="b46d8-111">备注</span><span class="sxs-lookup"><span data-stu-id="b46d8-111">Remarks</span></span>

<span data-ttu-id="b46d8-112">`-langversion` 选项指定编译器接受的语法。</span><span class="sxs-lookup"><span data-stu-id="b46d8-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="b46d8-113">例如，如果指定语言版本为 9.0，则编译器将生成仅在 10.0 及更高版本中有效的语法错误。</span><span class="sxs-lookup"><span data-stu-id="b46d8-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>

<span data-ttu-id="b46d8-114">在开发面向不同 .NET Framework 版本的应用程序时，可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="b46d8-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="b46d8-115">例如，如果面向的是 .NET Framework 3.5，则可以使用此选项来确保不使用语言版本 10.0 中的语法。</span><span class="sxs-lookup"><span data-stu-id="b46d8-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>

<span data-ttu-id="b46d8-116">只能使用命令行直接设置 `-langversion`。</span><span class="sxs-lookup"><span data-stu-id="b46d8-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="b46d8-117">有关详细信息，请参阅[面向特定的 .NET Framework 版本](/visualstudio/ide/visual-studio-multi-targeting-overview)。</span><span class="sxs-lookup"><span data-stu-id="b46d8-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/visual-studio-multi-targeting-overview).</span></span>

## <a name="example"></a><span data-ttu-id="b46d8-118">示例</span><span class="sxs-lookup"><span data-stu-id="b46d8-118">Example</span></span>

<span data-ttu-id="b46d8-119">以下代码为 Visual Basic 9.0 编译 `sample.vb`。</span><span class="sxs-lookup"><span data-stu-id="b46d8-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>

```console
vbc -langversion:9.0 sample.vb
```

## <a name="see-also"></a><span data-ttu-id="b46d8-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="b46d8-120">See also</span></span>

- [<span data-ttu-id="b46d8-121">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="b46d8-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b46d8-122">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="b46d8-122">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
