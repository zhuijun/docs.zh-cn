---
title: 代码中用作元素名称的关键字
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: e895db180dbb44cd4cfe4053d4be429f13324fe8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065744"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="b2542-102">代码中用作元素名称的关键字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2542-102">Keywords as Element Names in Code (Visual Basic)</span></span>

<span data-ttu-id="b2542-103">任何程序元素（例如变量、类或成员）可以具有与受限制关键字相同的名称。</span><span class="sxs-lookup"><span data-stu-id="b2542-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="b2542-104">例如，可以创建一个名为的变量 `Loop` 。</span><span class="sxs-lookup"><span data-stu-id="b2542-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="b2542-105">但是，若要引用您的版本（其名称与限制 `Loop` 关键字相同），必须在其前面加上一个完全限定字符串，或将其放在方括号内 (`[ ]`) 中，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="b2542-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="b2542-106">如果未执行上述任一操作，则 Visual Basic 假设使用内部 `Loop` 关键字，并产生错误，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="b2542-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="b2542-107">在引用窗体和控件时，以及声明变量或定义与受限制关键字同名的过程时，可以使用方括号。</span><span class="sxs-lookup"><span data-stu-id="b2542-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="b2542-108">很容易忘记限定名称或包含方括号，进而将错误引入代码并使其更难阅读。</span><span class="sxs-lookup"><span data-stu-id="b2542-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="b2542-109">出于此原因，我们建议不要使用受限制的关键字作为程序元素的名称。</span><span class="sxs-lookup"><span data-stu-id="b2542-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="b2542-110">但是，如果 Visual Basic 的将来版本定义了与现有窗体或控件名称冲突的新关键字，则在更新代码以使用新版本时，可以使用此方法。</span><span class="sxs-lookup"><span data-stu-id="b2542-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2542-111">您的程序还可能包括由其他引用的程序集提供的元素名称。</span><span class="sxs-lookup"><span data-stu-id="b2542-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="b2542-112">如果这些名称与受限制的关键字冲突，则在它们周围放置方括号会导致 Visual Basic 将它们解释为你定义的元素。</span><span class="sxs-lookup"><span data-stu-id="b2542-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2542-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="b2542-113">See also</span></span>

- [<span data-ttu-id="b2542-114">Visual Basic 命名约定</span><span class="sxs-lookup"><span data-stu-id="b2542-114">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="b2542-115">程序结构和代码约定</span><span class="sxs-lookup"><span data-stu-id="b2542-115">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="b2542-116">关键字</span><span class="sxs-lookup"><span data-stu-id="b2542-116">Keywords</span></span>](../../language-reference/keywords/index.md)
