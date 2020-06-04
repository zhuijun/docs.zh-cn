---
title: Option Compare 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 1ffe3e45a296d02364f488540d987d85133013bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404377"
---
# <a name="option-compare-statement"></a><span data-ttu-id="efb33-102">Option Compare 语句</span><span class="sxs-lookup"><span data-stu-id="efb33-102">Option Compare Statement</span></span>
<span data-ttu-id="efb33-103">声明比较字符串数据时要使用的默认比较方法。</span><span class="sxs-lookup"><span data-stu-id="efb33-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb33-104">语法</span><span class="sxs-lookup"><span data-stu-id="efb33-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="efb33-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="efb33-105">Parts</span></span>  
  
|<span data-ttu-id="efb33-106">术语</span><span class="sxs-lookup"><span data-stu-id="efb33-106">Term</span></span>|<span data-ttu-id="efb33-107">定义</span><span class="sxs-lookup"><span data-stu-id="efb33-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="efb33-108">可选。</span><span class="sxs-lookup"><span data-stu-id="efb33-108">Optional.</span></span> <span data-ttu-id="efb33-109">字符串比较中的结果基于派生自字符的内部二进制表示形式排序顺序。</span><span class="sxs-lookup"><span data-stu-id="efb33-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="efb33-110">这种比较类型在字符串包含不能解释为文本的字符时尤其有用。</span><span class="sxs-lookup"><span data-stu-id="efb33-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="efb33-111">在这种情况下，你不想因为字母顺序的等效性（如，不区分大小写）而使比较出现偏差。</span><span class="sxs-lookup"><span data-stu-id="efb33-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="efb33-112">可选。</span><span class="sxs-lookup"><span data-stu-id="efb33-112">Optional.</span></span> <span data-ttu-id="efb33-113">字符串比较中的结果基于由系统的区域设置确定的不区分大小写的文本排序顺序。</span><span class="sxs-lookup"><span data-stu-id="efb33-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="efb33-114">如果字符串包含所有文本字符且你想在比较它们时考虑到母顺序等效性（如，不区分大小写和紧密相关的字母），则这种比较类型非常有用。</span><span class="sxs-lookup"><span data-stu-id="efb33-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="efb33-115">例如，你可能认定 `A` 等于 `a`，`Ä` 和 `ä` 出现在 `B` 和 `b` 之前。</span><span class="sxs-lookup"><span data-stu-id="efb33-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efb33-116">备注</span><span class="sxs-lookup"><span data-stu-id="efb33-116">Remarks</span></span>  
 <span data-ttu-id="efb33-117">使用时，`Option Compare` 语句必须在文件中任何其他源代码语句之前。</span><span class="sxs-lookup"><span data-stu-id="efb33-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="efb33-118">`Option Compare` 语句指定字符串比较方法（`Binary` 或 `Text`）。</span><span class="sxs-lookup"><span data-stu-id="efb33-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="efb33-119">默认的文本比较方法是 `Binary`。</span><span class="sxs-lookup"><span data-stu-id="efb33-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="efb33-120">`Binary` 比较会对每个字符串中每个字符的数字 Unicode 值进行比较。</span><span class="sxs-lookup"><span data-stu-id="efb33-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="efb33-121">`Text` 比较会基于当前区域性中的词汇意义对每个 Unicode 字符进行比较。</span><span class="sxs-lookup"><span data-stu-id="efb33-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="efb33-122">在 Microsoft Windows 中，排序顺序取决于代码页。</span><span class="sxs-lookup"><span data-stu-id="efb33-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="efb33-123">有关详细信息，请参阅[代码页](/cpp/c-runtime-library/code-pages)。</span><span class="sxs-lookup"><span data-stu-id="efb33-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="efb33-124">在下例中，使用 `Option Compare Binary` 对英语/欧洲代码页 (ANSI 1252) 中的字符进行排序，由此产生典型的二进制排序顺序。</span><span class="sxs-lookup"><span data-stu-id="efb33-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="efb33-125">使用 `Option Compare Text` 对同一代码页中的相同字符进行排序时，会产生以下文本排序顺序。</span><span class="sxs-lookup"><span data-stu-id="efb33-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="efb33-126">当 Option Compare 语句不存在时</span><span class="sxs-lookup"><span data-stu-id="efb33-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="efb33-127">如果源代码不包含 `Option Compare` 语句，则使用 "编译" 页上的 "**选项比较**" 设置[，"项目设计器（Visual Basic）](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) "。</span><span class="sxs-lookup"><span data-stu-id="efb33-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="efb33-128">如果使用命令行编译器，则使用[-optioncompare](../../reference/command-line-compiler/optioncompare.md)编译器选项指定的设置。</span><span class="sxs-lookup"><span data-stu-id="efb33-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="efb33-129">若要在 IDE 中设置 Option Compare</span><span class="sxs-lookup"><span data-stu-id="efb33-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="efb33-130">在**解决方案资源管理器**中，选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="efb33-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="efb33-131">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="efb33-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="efb33-132">单击“编译”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="efb33-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="efb33-133">设置 "**选项比较**" 框中的值。</span><span class="sxs-lookup"><span data-stu-id="efb33-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="efb33-134">创建项目时，"**编译**" 选项卡上的 "**选项比较**" 设置设置为 "**选项**" 对话框中的 " **option compare** " 设置。</span><span class="sxs-lookup"><span data-stu-id="efb33-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="efb33-135">若要更改此设置，请在 "**工具**" 菜单上单击 "**选项**"。</span><span class="sxs-lookup"><span data-stu-id="efb33-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="efb33-136">在“选项”对话框中，展开“项目和解决方案”，然后单击“VB 默认值”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="efb33-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="efb33-137">**VB 默认**设置中的初始默认设置为 "**二进制**"。</span><span class="sxs-lookup"><span data-stu-id="efb33-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="efb33-138">若要设置命令行上的 Option Compare</span><span class="sxs-lookup"><span data-stu-id="efb33-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="efb33-139">在**vbc**命令中包含[-optioncompare](../../reference/command-line-compiler/optioncompare.md)编译器选项。</span><span class="sxs-lookup"><span data-stu-id="efb33-139">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efb33-140">示例</span><span class="sxs-lookup"><span data-stu-id="efb33-140">Example</span></span>  
 <span data-ttu-id="efb33-141">下例使用 `Option Compare` 语句将二进制比较设置为默认字符串比较方法。</span><span class="sxs-lookup"><span data-stu-id="efb33-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="efb33-142">若要使用此代码，请取消 `Option Compare Binary` 语句的注释，并将其置于源文件顶部。</span><span class="sxs-lookup"><span data-stu-id="efb33-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="efb33-143">示例</span><span class="sxs-lookup"><span data-stu-id="efb33-143">Example</span></span>  
 <span data-ttu-id="efb33-144">下例使用 `Option Compare` 语句将不区分大小写的文本排序顺序设置为默认字符串比较方法。</span><span class="sxs-lookup"><span data-stu-id="efb33-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="efb33-145">若要使用此代码，请取消 `Option Compare Text` 语句的注释，并将其置于源文件顶部。</span><span class="sxs-lookup"><span data-stu-id="efb33-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="efb33-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efb33-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="efb33-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="efb33-147">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="efb33-148">比较运算符</span><span class="sxs-lookup"><span data-stu-id="efb33-148">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="efb33-149">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efb33-149">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="efb33-150">Like 运算符</span><span class="sxs-lookup"><span data-stu-id="efb33-150">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="efb33-151">字符串函数</span><span class="sxs-lookup"><span data-stu-id="efb33-151">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="efb33-152">Option Explicit 语句</span><span class="sxs-lookup"><span data-stu-id="efb33-152">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="efb33-153">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="efb33-153">Option Strict Statement</span></span>](option-strict-statement.md)
