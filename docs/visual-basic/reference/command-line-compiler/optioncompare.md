---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400548"
---
# <a name="-optioncompare"></a><span data-ttu-id="4e5f9-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="4e5f9-102">-optioncompare</span></span>

<span data-ttu-id="4e5f9-103">指定如何进行字符串比较。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e5f9-104">语法</span><span class="sxs-lookup"><span data-stu-id="4e5f9-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="4e5f9-105">备注</span><span class="sxs-lookup"><span data-stu-id="4e5f9-105">Remarks</span></span>

<span data-ttu-id="4e5f9-106">可以使用以下两种形式之一指定 `-optioncompare`：使用二进制字符串比较的 `-optioncompare:binary`，和使用文本字符串比较的 `-optioncompare:text`。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="4e5f9-107">默认情况下，编译器使用 `-optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="4e5f9-108">在 Microsoft Windows 中，当前代码页确定二进制排序顺序。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="4e5f9-109">典型的二进制排序顺序如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e5f9-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="4e5f9-110">基于由系统的区域设置确定的不区分大小写的文本排序顺序对基于文本的字符串进行比较。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="4e5f9-111">典型的文本排序顺序如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e5f9-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="4e5f9-112">若要在 Visual Studio IDE 中设置 -optioncompare</span><span class="sxs-lookup"><span data-stu-id="4e5f9-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="4e5f9-113">在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4e5f9-114">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="4e5f9-115">单击“编译”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="4e5f9-116">修改“Option Compare”  框中的值。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="4e5f9-117">以编程方式设置 -optioncompare</span><span class="sxs-lookup"><span data-stu-id="4e5f9-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="4e5f9-118">请参阅 [Option Compare 语句](../../language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-118">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e5f9-119">示例</span><span class="sxs-lookup"><span data-stu-id="4e5f9-119">Example</span></span>

<span data-ttu-id="4e5f9-120">下面的代码编译 `ProjFile.vb`，并使用二进制字符串比较。</span><span class="sxs-lookup"><span data-stu-id="4e5f9-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="4e5f9-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e5f9-121">See also</span></span>

- [<span data-ttu-id="4e5f9-122">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="4e5f9-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4e5f9-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4e5f9-123">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="4e5f9-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="4e5f9-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="4e5f9-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="4e5f9-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="4e5f9-126">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="4e5f9-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="4e5f9-127">Option Compare 语句</span><span class="sxs-lookup"><span data-stu-id="4e5f9-127">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="4e5f9-128">“选项”对话框 ->“项目”->“Visual Basic 默认值”</span><span class="sxs-lookup"><span data-stu-id="4e5f9-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
