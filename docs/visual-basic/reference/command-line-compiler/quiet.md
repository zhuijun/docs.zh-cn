---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400521"
---
# <a name="-quiet"></a><span data-ttu-id="5337d-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="5337d-102">-quiet</span></span>

<span data-ttu-id="5337d-103">阻止编译器显示与语法相关的错误和警告的代码。</span><span class="sxs-lookup"><span data-stu-id="5337d-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="5337d-104">语法</span><span class="sxs-lookup"><span data-stu-id="5337d-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="5337d-105">备注</span><span class="sxs-lookup"><span data-stu-id="5337d-105">Remarks</span></span>

<span data-ttu-id="5337d-106">默认情况，`-quiet` 是无效的。</span><span class="sxs-lookup"><span data-stu-id="5337d-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="5337d-107">当编译器报告与语法相关的错误或警告时，它还会输出源代码中的行。</span><span class="sxs-lookup"><span data-stu-id="5337d-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="5337d-108">对于分析编译器输出的应用程序，编译器仅输出诊断文本可能更方便。</span><span class="sxs-lookup"><span data-stu-id="5337d-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="5337d-109">在下面的示例中，`Module1` 在编译时不使用 `-quiet` 的情况下输出一个包含源代码的错误。</span><span class="sxs-lookup"><span data-stu-id="5337d-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="5337d-110">输出：</span><span class="sxs-lookup"><span data-stu-id="5337d-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="5337d-111">使用 `-quiet` 编译，编译器仅输出以下内容：</span><span class="sxs-lookup"><span data-stu-id="5337d-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="5337d-112">`-quiet` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="5337d-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="5337d-113">示例</span><span class="sxs-lookup"><span data-stu-id="5337d-113">Example</span></span>

<span data-ttu-id="5337d-114">下面的代码编译 `T2.vb`，并且不显示与语法相关的编译器诊断代码：</span><span class="sxs-lookup"><span data-stu-id="5337d-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="5337d-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="5337d-115">See also</span></span>

- [<span data-ttu-id="5337d-116">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="5337d-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5337d-117">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="5337d-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
