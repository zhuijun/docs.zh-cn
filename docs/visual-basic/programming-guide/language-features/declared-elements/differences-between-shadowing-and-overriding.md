---
title: 隐藏和重写之间的差异
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: a6ea83fadf18ef3be778e6de31c0eb4e65e74824
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392865"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="0c4cf-102">隐藏和重写之间的差异 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c4cf-102">Differences Between Shadowing and Overriding (Visual Basic)</span></span>
<span data-ttu-id="0c4cf-103">在定义继承自基类的类时，有时需要重新定义派生类中的一个或多个基类元素。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-103">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="0c4cf-104">隐藏和重写都可用于此目的。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-104">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="0c4cf-105">比较</span><span class="sxs-lookup"><span data-stu-id="0c4cf-105">Comparison</span></span>  
 <span data-ttu-id="0c4cf-106">当派生类从基类继承时使用隐藏和重写，并且这两种方法都将一个已声明的元素重定义为另一个。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-106">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="0c4cf-107">但两者之间存在重大差异。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-107">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="0c4cf-108">下表将隐藏与重写进行比较。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-108">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="0c4cf-109">比较点</span><span class="sxs-lookup"><span data-stu-id="0c4cf-109">Point of comparison</span></span>|<span data-ttu-id="0c4cf-110">阴影操作</span><span class="sxs-lookup"><span data-stu-id="0c4cf-110">Shadowing</span></span>|<span data-ttu-id="0c4cf-111">替代</span><span class="sxs-lookup"><span data-stu-id="0c4cf-111">Overriding</span></span>|  
|<span data-ttu-id="0c4cf-112">用途</span><span class="sxs-lookup"><span data-stu-id="0c4cf-112">Purpose</span></span>|<span data-ttu-id="0c4cf-113">针对引入已在派生类中定义的成员的后续基类修改进行保护</span><span class="sxs-lookup"><span data-stu-id="0c4cf-113">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="0c4cf-114">通过定义具有相同调用序列的过程或属性的不同实现来实现多态性<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0c4cf-114">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="0c4cf-115">重新定义的元素</span><span class="sxs-lookup"><span data-stu-id="0c4cf-115">Redefined element</span></span>|<span data-ttu-id="0c4cf-116">任何声明的元素类型</span><span class="sxs-lookup"><span data-stu-id="0c4cf-116">Any declared element type</span></span>|<span data-ttu-id="0c4cf-117">仅过程（ `Function` 、 `Sub` 或 `Operator` ）或属性</span><span class="sxs-lookup"><span data-stu-id="0c4cf-117">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="0c4cf-118">重定义元素</span><span class="sxs-lookup"><span data-stu-id="0c4cf-118">Redefining element</span></span>|<span data-ttu-id="0c4cf-119">任何声明的元素类型</span><span class="sxs-lookup"><span data-stu-id="0c4cf-119">Any declared element type</span></span>|<span data-ttu-id="0c4cf-120">仅具有相同调用序列的过程或属性<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0c4cf-120">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="0c4cf-121">重定义元素的访问级别</span><span class="sxs-lookup"><span data-stu-id="0c4cf-121">Access level of redefining element</span></span>|<span data-ttu-id="0c4cf-122">任何访问级别</span><span class="sxs-lookup"><span data-stu-id="0c4cf-122">Any access level</span></span>|<span data-ttu-id="0c4cf-123">无法更改重写元素的访问级别</span><span class="sxs-lookup"><span data-stu-id="0c4cf-123">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="0c4cf-124">重定义元素的可读性和可写性</span><span class="sxs-lookup"><span data-stu-id="0c4cf-124">Readability and writability of redefining element</span></span>|<span data-ttu-id="0c4cf-125">任何组合</span><span class="sxs-lookup"><span data-stu-id="0c4cf-125">Any combination</span></span>|<span data-ttu-id="0c4cf-126">无法更改重写属性的可读性或可写性</span><span class="sxs-lookup"><span data-stu-id="0c4cf-126">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="0c4cf-127">控制重定义</span><span class="sxs-lookup"><span data-stu-id="0c4cf-127">Control over redefining</span></span>|<span data-ttu-id="0c4cf-128">基类元素无法强制或禁止隐藏</span><span class="sxs-lookup"><span data-stu-id="0c4cf-128">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="0c4cf-129">基类元素可以指定 `MustOverride` 、 `NotOverridable` 或`Overridable`</span><span class="sxs-lookup"><span data-stu-id="0c4cf-129">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="0c4cf-130">关键字用法</span><span class="sxs-lookup"><span data-stu-id="0c4cf-130">Keyword usage</span></span>|<span data-ttu-id="0c4cf-131">`Shadows`建议在派生类中使用;`Shadows`如果和均 `Shadows` 未 `Overrides` 指定<sup>2</sup> ，则假定</span><span class="sxs-lookup"><span data-stu-id="0c4cf-131">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="0c4cf-132">`Overridable`或 `MustOverride` 在基类中是必需的; `Overrides` 派生类中需要</span><span class="sxs-lookup"><span data-stu-id="0c4cf-132">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="0c4cf-133">从派生类派生的类的重定义元素的继承</span><span class="sxs-lookup"><span data-stu-id="0c4cf-133">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="0c4cf-134">由进一步的派生类继承的隐藏元素;隐藏的元素仍隐藏<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0c4cf-134">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="0c4cf-135">重写由进一步派生的类继承的元素;重写的元素仍将被重写</span><span class="sxs-lookup"><span data-stu-id="0c4cf-135">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="0c4cf-136"><sup>1</sup> *调用序列*包含元素类型（ `Function` 、 `Sub` 、 `Operator` 或 `Property` ）、名称、参数列表和返回类型。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-136"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="0c4cf-137">不能使用属性或其他方法来重写过程。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-137">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="0c4cf-138">不能用另一种类型的过程（ `Function` 、 `Sub` 或）重写 `Operator` 。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-138">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="0c4cf-139"><sup>2</sup>如果未指定 `Shadows` 或 `Overrides` ，则编译器会发出警告消息，帮助您确定要使用哪种重新定义。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-139"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="0c4cf-140">如果忽略该警告，则使用隐藏机制。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-140">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="0c4cf-141"><sup>3</sup>如果无法在进一步的派生类中访问隐藏元素，则不会继承隐藏。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-141"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="0c4cf-142">例如，如果将隐藏元素声明为 `Private` ，派生自派生类的类将继承原始元素，而不是隐藏元素。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-142">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="0c4cf-143">指南</span><span class="sxs-lookup"><span data-stu-id="0c4cf-143">Guidelines</span></span>  
 <span data-ttu-id="0c4cf-144">在以下情况下，通常使用重写：</span><span class="sxs-lookup"><span data-stu-id="0c4cf-144">You normally use overriding in the following cases:</span></span>  
  
- <span data-ttu-id="0c4cf-145">你要定义多态派生类。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-145">You are defining polymorphic derived classes.</span></span>  
  
- <span data-ttu-id="0c4cf-146">您希望安全地让编译器强制执行相同的元素类型和调用序列。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-146">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="0c4cf-147">通常会在以下情况下使用隐藏：</span><span class="sxs-lookup"><span data-stu-id="0c4cf-147">You normally use shadowing in the following cases:</span></span>  
  
- <span data-ttu-id="0c4cf-148">你预计可能会修改基类，并使用与你的名称相同的名称来定义元素。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-148">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
- <span data-ttu-id="0c4cf-149">您希望自由更改元素类型或调用序列。</span><span class="sxs-lookup"><span data-stu-id="0c4cf-149">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c4cf-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c4cf-150">See also</span></span>

- [<span data-ttu-id="0c4cf-151">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="0c4cf-151">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="0c4cf-152">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="0c4cf-152">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="0c4cf-153">如何：隐藏与变量同名的变量</span><span class="sxs-lookup"><span data-stu-id="0c4cf-153">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="0c4cf-154">如何：隐藏继承的变量</span><span class="sxs-lookup"><span data-stu-id="0c4cf-154">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="0c4cf-155">如何：访问被派生类隐藏的变量</span><span class="sxs-lookup"><span data-stu-id="0c4cf-155">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="0c4cf-156">Shadows</span><span class="sxs-lookup"><span data-stu-id="0c4cf-156">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="0c4cf-157">替代</span><span class="sxs-lookup"><span data-stu-id="0c4cf-157">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
