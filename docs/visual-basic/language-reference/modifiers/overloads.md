---
title: 重载
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392101"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="2c25e-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c25e-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="2c25e-103">指定某一属性或过程重新声明一个或多个具有相同名称的现有属性或过程。</span><span class="sxs-lookup"><span data-stu-id="2c25e-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c25e-104">备注</span><span class="sxs-lookup"><span data-stu-id="2c25e-104">Remarks</span></span>

<span data-ttu-id="2c25e-105">*重载*是为同一范围内的给定属性或过程名称提供多个定义的做法。</span><span class="sxs-lookup"><span data-stu-id="2c25e-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="2c25e-106">重新声明具有不同签名的属性或过程有时称为 "*按签名隐藏*"。</span><span class="sxs-lookup"><span data-stu-id="2c25e-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="2c25e-107">规则</span><span class="sxs-lookup"><span data-stu-id="2c25e-107">Rules</span></span>

- <span data-ttu-id="2c25e-108">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="2c25e-108">**Declaration Context.**</span></span> <span data-ttu-id="2c25e-109">`Overloads`只能在属性或过程声明语句中使用。</span><span class="sxs-lookup"><span data-stu-id="2c25e-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="2c25e-110">**组合修饰符。**</span><span class="sxs-lookup"><span data-stu-id="2c25e-110">**Combined Modifiers.**</span></span> <span data-ttu-id="2c25e-111">不能 `Overloads` 在同一过程声明中同时指定和[阴影](shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="2c25e-111">You cannot specify `Overloads` together with [Shadows](shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="2c25e-112">**必需的差异。**</span><span class="sxs-lookup"><span data-stu-id="2c25e-112">**Required Differences.**</span></span> <span data-ttu-id="2c25e-113">此声明中的*签名*必须与它重载的每个属性或过程的签名不同。</span><span class="sxs-lookup"><span data-stu-id="2c25e-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="2c25e-114">签名包含属性或过程名以及以下内容：</span><span class="sxs-lookup"><span data-stu-id="2c25e-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="2c25e-115">参数的数量</span><span class="sxs-lookup"><span data-stu-id="2c25e-115">the number of parameters</span></span>

  - <span data-ttu-id="2c25e-116">参数顺序</span><span class="sxs-lookup"><span data-stu-id="2c25e-116">the order of the parameters</span></span>

  - <span data-ttu-id="2c25e-117">参数的数据类型</span><span class="sxs-lookup"><span data-stu-id="2c25e-117">the data types of the parameters</span></span>

  - <span data-ttu-id="2c25e-118">类型参数的数量（针对泛型过程）</span><span class="sxs-lookup"><span data-stu-id="2c25e-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="2c25e-119">返回类型（仅针对转换运算符过程）</span><span class="sxs-lookup"><span data-stu-id="2c25e-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="2c25e-120">所有重载都必须有相同的名称，但每个重载必须在上面的一个或多个方面与所有其他重载不同。</span><span class="sxs-lookup"><span data-stu-id="2c25e-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="2c25e-121">这使编译器在代码调用属性或过程时可以区分要使用哪个版本。</span><span class="sxs-lookup"><span data-stu-id="2c25e-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="2c25e-122">**不允许的差异。**</span><span class="sxs-lookup"><span data-stu-id="2c25e-122">**Disallowed Differences.**</span></span> <span data-ttu-id="2c25e-123">对于重载属性或过程而言，更改下面的一项或多项无效，因为它们不是签名的一部分：</span><span class="sxs-lookup"><span data-stu-id="2c25e-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="2c25e-124">它是否返回值（针对过程）</span><span class="sxs-lookup"><span data-stu-id="2c25e-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="2c25e-125">返回值的数据类型（除转换运算符之外）</span><span class="sxs-lookup"><span data-stu-id="2c25e-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="2c25e-126">参数或类型参数的名称</span><span class="sxs-lookup"><span data-stu-id="2c25e-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="2c25e-127">对类型参数的约束（针对泛型过程）</span><span class="sxs-lookup"><span data-stu-id="2c25e-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="2c25e-128">参数修饰符关键字（如 `ByRef` 或 `Optional`）</span><span class="sxs-lookup"><span data-stu-id="2c25e-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="2c25e-129">属性或过程修饰符关键字（如 `Public` 或 `Shared`）</span><span class="sxs-lookup"><span data-stu-id="2c25e-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="2c25e-130">**可选修饰符。**</span><span class="sxs-lookup"><span data-stu-id="2c25e-130">**Optional Modifier.**</span></span> <span data-ttu-id="2c25e-131">在 `Overloads` 同一个类中定义多个重载属性或过程时，无需使用修饰符。</span><span class="sxs-lookup"><span data-stu-id="2c25e-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="2c25e-132">然而，如果在某个声明中使用 `Overloads`，则必须在所有的声明中使用它。</span><span class="sxs-lookup"><span data-stu-id="2c25e-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="2c25e-133">**隐藏和重载。**</span><span class="sxs-lookup"><span data-stu-id="2c25e-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="2c25e-134">`Overloads`还可用于在基类中隐藏现有成员或重载成员集。</span><span class="sxs-lookup"><span data-stu-id="2c25e-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="2c25e-135">以这种方式使用 `Overloads` 时，应使用与基类成员相同的名称和参数列表来声明属性或方法，并且不提供 `Shadows` 关键字。</span><span class="sxs-lookup"><span data-stu-id="2c25e-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="2c25e-136">如果使用 `Overrides`，编译器将隐式添加 `Overloads`，以便库 API 更轻松地使用 C#。</span><span class="sxs-lookup"><span data-stu-id="2c25e-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="2c25e-137">`Overloads` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="2c25e-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="2c25e-138">Function 语句</span><span class="sxs-lookup"><span data-stu-id="2c25e-138">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="2c25e-139">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="2c25e-139">Operator Statement</span></span>](../statements/operator-statement.md)

- [<span data-ttu-id="2c25e-140">Property Statement</span><span class="sxs-lookup"><span data-stu-id="2c25e-140">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="2c25e-141">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="2c25e-141">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="2c25e-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c25e-142">See also</span></span>

- [<span data-ttu-id="2c25e-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="2c25e-143">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="2c25e-144">过程重载</span><span class="sxs-lookup"><span data-stu-id="2c25e-144">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="2c25e-145">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c25e-145">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="2c25e-146">运算符过程</span><span class="sxs-lookup"><span data-stu-id="2c25e-146">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="2c25e-147">如何：定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="2c25e-147">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
