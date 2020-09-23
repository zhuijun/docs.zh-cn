---
title: 如何：定义一个过程的多个版本
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 2661603ba33dd0bc28ac1a192794a4534225b641
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071633"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="1b764-102">如何：定义一个过程的多个版本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b764-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>

<span data-ttu-id="1b764-103">您 *可以通过使用* 相同的名称，但对于每个版本使用不同的参数列表，在多个版本中定义过程。</span><span class="sxs-lookup"><span data-stu-id="1b764-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="1b764-104">重载的目的是定义过程中的多个紧密相关的版本，而不必按名称对其进行区分。</span><span class="sxs-lookup"><span data-stu-id="1b764-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="1b764-105">有关更多信息，请参见 [Procedure Overloading](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="1b764-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="1b764-106">定义一个过程的多个版本</span><span class="sxs-lookup"><span data-stu-id="1b764-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="1b764-107">`Sub` `Function` 为要定义的过程的每个版本编写一个或声明语句。</span><span class="sxs-lookup"><span data-stu-id="1b764-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="1b764-108">在每个声明中使用相同的过程名称。</span><span class="sxs-lookup"><span data-stu-id="1b764-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="1b764-109">`Sub` `Function` 在每个声明中的或关键字之前加上[Overloads](../../../language-reference/modifiers/overloads.md)关键字。</span><span class="sxs-lookup"><span data-stu-id="1b764-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="1b764-110">您可以选择 `Overloads` 在声明中省略，但如果将其包含在任何声明中，则必须在每个声明中包含它。</span><span class="sxs-lookup"><span data-stu-id="1b764-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="1b764-111">遵循每个声明语句，编写过程代码来处理调用代码提供与该版本的参数列表相匹配的参数的特定情况。</span><span class="sxs-lookup"><span data-stu-id="1b764-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="1b764-112">无需测试调用代码提供了哪些参数。</span><span class="sxs-lookup"><span data-stu-id="1b764-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="1b764-113">Visual Basic 将控制传递给过程的匹配版本。</span><span class="sxs-lookup"><span data-stu-id="1b764-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="1b764-114">根据需要，用或语句终止过程的每个版本 `End Sub` `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="1b764-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b764-115">示例</span><span class="sxs-lookup"><span data-stu-id="1b764-115">Example</span></span>  

 <span data-ttu-id="1b764-116">下面的示例定义了一个 `Sub` 过程，用于将事务发布到客户余额。</span><span class="sxs-lookup"><span data-stu-id="1b764-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="1b764-117">它使用 `Overloads` 关键字定义过程的两个版本，一个版本按姓名，另一个按帐号接受客户。</span><span class="sxs-lookup"><span data-stu-id="1b764-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="1b764-118">调用代码可以获取客户标识作为 `String` 或 `Integer` ，然后在任一情况下均使用相同的调用语句。</span><span class="sxs-lookup"><span data-stu-id="1b764-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="1b764-119">有关如何调用该过程的这些版本的信息 `post` ，请参阅 [如何：调用重载过程](./how-to-call-an-overloaded-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="1b764-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="1b764-120">编译代码</span><span class="sxs-lookup"><span data-stu-id="1b764-120">Compile the code</span></span>  

 <span data-ttu-id="1b764-121">请确保每个重载版本都具有相同的过程名称，但参数列表不同。</span><span class="sxs-lookup"><span data-stu-id="1b764-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b764-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="1b764-122">See also</span></span>

- [<span data-ttu-id="1b764-123">过程</span><span class="sxs-lookup"><span data-stu-id="1b764-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1b764-124">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="1b764-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1b764-125">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="1b764-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="1b764-126">如何：重载带有可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="1b764-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="1b764-127">如何：重载参数数量不确定的过程</span><span class="sxs-lookup"><span data-stu-id="1b764-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="1b764-128">重载过程注意事项</span><span class="sxs-lookup"><span data-stu-id="1b764-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="1b764-129">重载决策</span><span class="sxs-lookup"><span data-stu-id="1b764-129">Overload Resolution</span></span>](./overload-resolution.md)
