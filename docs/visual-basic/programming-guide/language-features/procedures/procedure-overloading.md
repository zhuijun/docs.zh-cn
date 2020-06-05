---
title: 过程重载
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: f8accc74fbdd9b1d8cf9bc3d8f6ddd26f73452b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363871"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="7d629-102">过程重载 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d629-102">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="7d629-103">*重载*过程意味着使用相同的名称但不同的参数列表在多个版本中定义它。</span><span class="sxs-lookup"><span data-stu-id="7d629-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="7d629-104">重载的目的是定义过程中的多个紧密相关的版本，而不必按名称对其进行区分。</span><span class="sxs-lookup"><span data-stu-id="7d629-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="7d629-105">可以通过改变参数列表来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="7d629-105">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="7d629-106">重载规则</span><span class="sxs-lookup"><span data-stu-id="7d629-106">Overloading Rules</span></span>

<span data-ttu-id="7d629-107">重载过程时，以下规则适用：</span><span class="sxs-lookup"><span data-stu-id="7d629-107">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="7d629-108">**相同的名称**。</span><span class="sxs-lookup"><span data-stu-id="7d629-108">**Same Name**.</span></span> <span data-ttu-id="7d629-109">每个重载版本必须使用相同的过程名称。</span><span class="sxs-lookup"><span data-stu-id="7d629-109">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="7d629-110">**不同的签名**。</span><span class="sxs-lookup"><span data-stu-id="7d629-110">**Different Signature**.</span></span> <span data-ttu-id="7d629-111">每个重载版本必须与所有其他重载版本都有以下两个方面中的至少一个：</span><span class="sxs-lookup"><span data-stu-id="7d629-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="7d629-112">参数数目</span><span class="sxs-lookup"><span data-stu-id="7d629-112">Number of parameters</span></span>

  - <span data-ttu-id="7d629-113">参数的顺序</span><span class="sxs-lookup"><span data-stu-id="7d629-113">Order of the parameters</span></span>

  - <span data-ttu-id="7d629-114">参数的数据类型</span><span class="sxs-lookup"><span data-stu-id="7d629-114">Data types of the parameters</span></span>

  - <span data-ttu-id="7d629-115">类型参数的数目（针对泛型过程）</span><span class="sxs-lookup"><span data-stu-id="7d629-115">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="7d629-116">返回类型（仅适用于转换运算符）</span><span class="sxs-lookup"><span data-stu-id="7d629-116">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="7d629-117">与过程名称一起，以上各项统称为过程的*签名*。</span><span class="sxs-lookup"><span data-stu-id="7d629-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="7d629-118">调用重载过程时，编译器将使用签名来检查调用是否与定义正确匹配。</span><span class="sxs-lookup"><span data-stu-id="7d629-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="7d629-119">**项不是签名的一部分**。</span><span class="sxs-lookup"><span data-stu-id="7d629-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="7d629-120">不能重载过程而不会改变签名。</span><span class="sxs-lookup"><span data-stu-id="7d629-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="7d629-121">具体而言，你不能通过仅改变一个或多个以下项来重载过程：</span><span class="sxs-lookup"><span data-stu-id="7d629-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="7d629-122">过程修饰符关键字，如 `Public` 、 `Shared` 和`Static`</span><span class="sxs-lookup"><span data-stu-id="7d629-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="7d629-123">参数或类型参数名称</span><span class="sxs-lookup"><span data-stu-id="7d629-123">Parameter or type parameter names</span></span>

  - <span data-ttu-id="7d629-124">类型参数约束（针对泛型过程）</span><span class="sxs-lookup"><span data-stu-id="7d629-124">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="7d629-125">参数修饰符关键字，如 `ByRef` 和`Optional`</span><span class="sxs-lookup"><span data-stu-id="7d629-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="7d629-126">是否返回值</span><span class="sxs-lookup"><span data-stu-id="7d629-126">Whether it returns a value</span></span>

  - <span data-ttu-id="7d629-127">返回值的数据类型（转换运算符除外）</span><span class="sxs-lookup"><span data-stu-id="7d629-127">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="7d629-128">前面列表中的项不是签名的一部分。</span><span class="sxs-lookup"><span data-stu-id="7d629-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="7d629-129">尽管不能使用它们来区分重载版本，但你可以根据其签名正确区分的重载版本来区分它们。</span><span class="sxs-lookup"><span data-stu-id="7d629-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="7d629-130">**后期绑定参数**。</span><span class="sxs-lookup"><span data-stu-id="7d629-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="7d629-131">如果打算将后期绑定对象变量传递到重载版本，则必须将相应的参数声明为 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="7d629-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="7d629-132">一个过程的多个版本</span><span class="sxs-lookup"><span data-stu-id="7d629-132">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="7d629-133">假设您正在编写一个 `Sub` 过程，以便在客户的余额中发布事务，并且您希望能够按名称或帐号来引用客户。</span><span class="sxs-lookup"><span data-stu-id="7d629-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="7d629-134">为此，可以定义两个不同的 `Sub` 过程，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="7d629-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="7d629-135">重载版本</span><span class="sxs-lookup"><span data-stu-id="7d629-135">Overloaded Versions</span></span>

<span data-ttu-id="7d629-136">一种替代方法是重载单个过程名称。</span><span class="sxs-lookup"><span data-stu-id="7d629-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="7d629-137">您可以使用[Overloads](../../../language-reference/modifiers/overloads.md)关键字为每个参数列表定义过程的版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7d629-137">You can use the [Overloads](../../../language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="7d629-138">其他重载</span><span class="sxs-lookup"><span data-stu-id="7d629-138">Additional Overloads</span></span>

<span data-ttu-id="7d629-139">如果还想要在或中接受事务量 `Decimal` ，可以 `Single` 进一步重载 `post` 以允许进行此变体。</span><span class="sxs-lookup"><span data-stu-id="7d629-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="7d629-140">如果对上述示例中的每个重载执行了此操作，则会有四个 `Sub` 过程，它们都具有相同的名称，但具有四个不同的签名。</span><span class="sxs-lookup"><span data-stu-id="7d629-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="7d629-141">重载的优点</span><span class="sxs-lookup"><span data-stu-id="7d629-141">Advantages of Overloading</span></span>

<span data-ttu-id="7d629-142">重载过程的优点是调用的灵活性。</span><span class="sxs-lookup"><span data-stu-id="7d629-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="7d629-143">若要使用 `post` 前面的示例中声明的过程，调用代码可以获取客户标识作为 `String` 或 `Integer` ，然后在这两种情况下调用相同的过程。</span><span class="sxs-lookup"><span data-stu-id="7d629-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="7d629-144">以下示例对此进行了说明：</span><span class="sxs-lookup"><span data-stu-id="7d629-144">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="7d629-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d629-145">See also</span></span>

- [<span data-ttu-id="7d629-146">过程</span><span class="sxs-lookup"><span data-stu-id="7d629-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7d629-147">如何：定义一个过程的多个版本</span><span class="sxs-lookup"><span data-stu-id="7d629-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="7d629-148">如何：调用重载过程</span><span class="sxs-lookup"><span data-stu-id="7d629-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="7d629-149">如何：重载带有可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="7d629-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="7d629-150">如何：重载参数数量不确定的过程</span><span class="sxs-lookup"><span data-stu-id="7d629-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="7d629-151">重载过程注意事项</span><span class="sxs-lookup"><span data-stu-id="7d629-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="7d629-152">重载决策</span><span class="sxs-lookup"><span data-stu-id="7d629-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="7d629-153">重载</span><span class="sxs-lookup"><span data-stu-id="7d629-153">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="7d629-154">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d629-154">Generic Types in Visual Basic</span></span>](../data-types/generic-types.md)
