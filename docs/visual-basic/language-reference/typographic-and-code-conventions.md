---
title: 版式和代码约定
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 0e36d9d61b0dd2701210ce614d15fd38f08f5401
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401350"
---
# <a name="typographic-and-code-conventions-visual-basic"></a><span data-ttu-id="f0f63-102">版式和代码约定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0f63-102">Typographic and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="f0f63-103">Visual Basic 文档使用以下排字和代码约定。</span><span class="sxs-lookup"><span data-stu-id="f0f63-103">Visual Basic documentation uses the following typographic and code conventions.</span></span>  
  
## <a name="typographic-conventions"></a><span data-ttu-id="f0f63-104">版式约定</span><span class="sxs-lookup"><span data-stu-id="f0f63-104">Typographic Conventions</span></span>  
  
|<span data-ttu-id="f0f63-105">示例</span><span class="sxs-lookup"><span data-stu-id="f0f63-105">Example</span></span>|<span data-ttu-id="f0f63-106">说明</span><span class="sxs-lookup"><span data-stu-id="f0f63-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0f63-107">`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`</span><span class="sxs-lookup"><span data-stu-id="f0f63-107">`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`</span></span>|<span data-ttu-id="f0f63-108">特定于语言的关键字和运行时成员具有词首大写字母，并设置格式，如本示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-108">Language-specific keywords and runtime members have initial uppercase letters and are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="f0f63-109">**SmallProject**、 **ButtonCollection**</span><span class="sxs-lookup"><span data-stu-id="f0f63-109">**SmallProject**, **ButtonCollection**</span></span>|<span data-ttu-id="f0f63-110">将为您指示键入的单词和短语设置格式，如本示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-110">Words and phrases you are instructed to type are formatted as shown in this example.</span></span>|  
|[<span data-ttu-id="f0f63-111">Module 语句</span><span class="sxs-lookup"><span data-stu-id="f0f63-111">Module Statement</span></span>](statements/module-statement.md)|<span data-ttu-id="f0f63-112">可单击以切换到另一个帮助页的链接的格式如本示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-112">Links you can click to go to another Help page are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="f0f63-113">*object*、 *variableName*、`argumentList`</span><span class="sxs-lookup"><span data-stu-id="f0f63-113">*object*, *variableName*, `argumentList`</span></span>|<span data-ttu-id="f0f63-114">您提供的信息的占位符格式如本示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-114">Placeholders for information that you supply are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="f0f63-115">[Shadows]，[ *expressionList* ]</span><span class="sxs-lookup"><span data-stu-id="f0f63-115">[ Shadows ], [ *expressionList* ]</span></span>|<span data-ttu-id="f0f63-116">在语法中，可选项括在括号中。</span><span class="sxs-lookup"><span data-stu-id="f0f63-116">In syntax, optional items are enclosed in brackets.</span></span>|  
|<span data-ttu-id="f0f63-117">{ `Public` &#124; `Friend` &#124; `Private` }</span><span class="sxs-lookup"><span data-stu-id="f0f63-117">{ `Public` &#124; `Friend` &#124; `Private` }</span></span>|<span data-ttu-id="f0f63-118">在语法中，当你必须在两个或多个项之间进行选择时，项括在大括号中，并用竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="f0f63-118">In syntax, when you must make a choice between two or more items, the items are enclosed in braces and separated by vertical bars.</span></span><br /><br /> <span data-ttu-id="f0f63-119">您必须选择一个（且只有一个）项。</span><span class="sxs-lookup"><span data-stu-id="f0f63-119">You must select one, and only one, of the items.</span></span>|  
|<span data-ttu-id="f0f63-120">[ `Protected` &#124; `Friend` ]</span><span class="sxs-lookup"><span data-stu-id="f0f63-120">[ `Protected` &#124; `Friend` ]</span></span>|<span data-ttu-id="f0f63-121">在语法中，当您有选择两个或多个项之间的选项时，项将括在方括号中，并用竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="f0f63-121">In syntax, when you have the option of selecting between two or more items, the items are enclosed in square brackets and separated by vertical bars.</span></span><br /><br /> <span data-ttu-id="f0f63-122">您可以选择项的任意组合，或不选择任何项。</span><span class="sxs-lookup"><span data-stu-id="f0f63-122">You can select any combination of the items, or no item.</span></span>|  
|<span data-ttu-id="f0f63-123">[{ `ByVal` &#124; `ByRef` }]</span><span class="sxs-lookup"><span data-stu-id="f0f63-123">[{ `ByVal` &#124; `ByRef` }]</span></span>|<span data-ttu-id="f0f63-124">在语法中，如果您可以选择不多个项，但您也可以完全省略项，则项括在括在大括号中的方括号内，并用竖线分隔。</span><span class="sxs-lookup"><span data-stu-id="f0f63-124">In syntax, when you can select no more than one item, but you can also omit the items completely, the items are enclosed in square brackets surrounded by braces and separated by vertical bars.</span></span>|  
|<span data-ttu-id="f0f63-125">*成员*名称1，*成员名称*2，*成员名称*3</span><span class="sxs-lookup"><span data-stu-id="f0f63-125">*memberName*1, *memberName*2, *memberName*3</span></span>|<span data-ttu-id="f0f63-126">同一个占位符的多个实例通过下标来区分，如示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-126">Multiple instances of the same placeholder are differentiated by subscripts, as shown in the example.</span></span>|  
|<span data-ttu-id="f0f63-127">*1*</span><span class="sxs-lookup"><span data-stu-id="f0f63-127">*memberName1*</span></span><br /><br /> <span data-ttu-id="f0f63-128">...</span><span class="sxs-lookup"><span data-stu-id="f0f63-128">...</span></span><br /><br /> <span data-ttu-id="f0f63-129">*memberNameN*</span><span class="sxs-lookup"><span data-stu-id="f0f63-129">*memberNameN*</span></span>|<span data-ttu-id="f0f63-130">在语法中，省略号（...）用于指示直接在省略号前面的类型的无限项。</span><span class="sxs-lookup"><span data-stu-id="f0f63-130">In syntax, an ellipsis (...) is used to indicate an indefinite number of items of the kind immediately in front of the ellipsis.</span></span><br /><br /> <span data-ttu-id="f0f63-131">在代码中，省略号表示为清楚起见省略了代码。</span><span class="sxs-lookup"><span data-stu-id="f0f63-131">In code, ellipses signify code omitted for the sake of clarity.</span></span>|  
|<span data-ttu-id="f0f63-132">ESC，ENTER</span><span class="sxs-lookup"><span data-stu-id="f0f63-132">ESC, ENTER</span></span>|<span data-ttu-id="f0f63-133">键盘上的键名和键序列均以大写字母显示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-133">Key names and key sequences on the keyboard appear in all uppercase letters.</span></span>|  
|<span data-ttu-id="f0f63-134">Alt+F1</span><span class="sxs-lookup"><span data-stu-id="f0f63-134">ALT+F1</span></span>|<span data-ttu-id="f0f63-135">当键名称之间出现加号（+）时，必须在按下一个键的同时按下一个键。</span><span class="sxs-lookup"><span data-stu-id="f0f63-135">When plus signs (+) appear between key names, you must hold down one key while pressing the other.</span></span> <span data-ttu-id="f0f63-136">例如，ALT + F1 表示按下 F1 键时按下 ALT 键。</span><span class="sxs-lookup"><span data-stu-id="f0f63-136">For example, ALT+F1 means hold down the ALT key while pressing the F1 key.</span></span>|  
  
## <a name="code-conventions"></a><span data-ttu-id="f0f63-137">代码约定</span><span class="sxs-lookup"><span data-stu-id="f0f63-137">Code Conventions</span></span>  
  
|<span data-ttu-id="f0f63-138">示例</span><span class="sxs-lookup"><span data-stu-id="f0f63-138">Example</span></span>|<span data-ttu-id="f0f63-139">说明</span><span class="sxs-lookup"><span data-stu-id="f0f63-139">Description</span></span>|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|<span data-ttu-id="f0f63-140">代码示例以固定间距字体显示，并设置格式，如本示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-140">Code samples appear in a fixed-pitch font and are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="f0f63-141">上一语句将的值设置 `sampleString` 为 "Hello，world！"</span><span class="sxs-lookup"><span data-stu-id="f0f63-141">The previous statement sets the value of `sampleString` to "Hello, world!"</span></span>|<span data-ttu-id="f0f63-142">解释性文本中的代码元素显示为固定间距字体，如本示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f0f63-142">Code elements in explanatory text appear in a fixed-pitch font, as shown in this example.</span></span>|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|<span data-ttu-id="f0f63-143">代码注释由撇号（'）或 REM 关键字引入。</span><span class="sxs-lookup"><span data-stu-id="f0f63-143">Code comments are introduced by an apostrophe (') or the REM keyword.</span></span>|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|<span data-ttu-id="f0f63-144">位于行末尾的空格后跟下划线（_）指示该语句在下一行继续。</span><span class="sxs-lookup"><span data-stu-id="f0f63-144">A space followed by an underscore ( _) at the end of a line indicates that the statement continues on the following line.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0f63-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0f63-145">See also</span></span>

- [<span data-ttu-id="f0f63-146">Visual Basic 语言参考</span><span class="sxs-lookup"><span data-stu-id="f0f63-146">Visual Basic Language Reference</span></span>](index.md)
- [<span data-ttu-id="f0f63-147">关键字</span><span class="sxs-lookup"><span data-stu-id="f0f63-147">Keywords</span></span>](keywords/index.md)
- [<span data-ttu-id="f0f63-148">Visual Basic 运行库成员</span><span class="sxs-lookup"><span data-stu-id="f0f63-148">Visual Basic Runtime Library Members</span></span>](runtime-library-members.md)
- [<span data-ttu-id="f0f63-149">Visual Basic 命名约定</span><span class="sxs-lookup"><span data-stu-id="f0f63-149">Visual Basic Naming Conventions</span></span>](../programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="f0f63-150">如何：在代码中拆分和合并语句</span><span class="sxs-lookup"><span data-stu-id="f0f63-150">How to: Break and Combine Statements in Code</span></span>](../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="f0f63-151">代码中的注释</span><span class="sxs-lookup"><span data-stu-id="f0f63-151">Comments in Code</span></span>](../programming-guide/program-structure/comments-in-code.md)
