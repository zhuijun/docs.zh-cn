---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 8eec54a12c7fb748df46e8c48a8b07eab983cc72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867871"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="f7412-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7412-102">NotOverridable (Visual Basic)</span></span>

<span data-ttu-id="f7412-103">指定不能在派生类中重写属性或过程。</span><span class="sxs-lookup"><span data-stu-id="f7412-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7412-104">备注</span><span class="sxs-lookup"><span data-stu-id="f7412-104">Remarks</span></span>  

 <span data-ttu-id="f7412-105">`NotOverridable`修饰符可防止在派生类中重写属性或方法。</span><span class="sxs-lookup"><span data-stu-id="f7412-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="f7412-106">可 [重写](overridable.md) 的修饰符允许在派生类中重写类中的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="f7412-106">The [Overridable](overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="f7412-107">有关详细信息，请参阅[继承基础知识](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="f7412-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="f7412-108">如果 `Overridable` `NotOverridable` 未指定或修饰符，则默认设置取决于属性或方法是重写基类属性还是替代方法。</span><span class="sxs-lookup"><span data-stu-id="f7412-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="f7412-109">如果属性或方法重写基类属性或方法，则默认设置为 `Overridable` ; 否则为 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="f7412-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="f7412-110">不能重写的元素有时称为 *密封* 元素。</span><span class="sxs-lookup"><span data-stu-id="f7412-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="f7412-111">`NotOverridable`只能在属性或过程声明语句中使用。</span><span class="sxs-lookup"><span data-stu-id="f7412-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="f7412-112">只能 `NotOverridable` 在替代另一个属性或过程的属性或过程上指定，即，只能与一起使用 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="f7412-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="f7412-113">组合修饰符</span><span class="sxs-lookup"><span data-stu-id="f7412-113">Combined Modifiers</span></span>  

 <span data-ttu-id="f7412-114">不能 `Overridable` `NotOverridable` 为方法指定或 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="f7412-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="f7412-115">不能 `NotOverridable` `MustOverride` `Overridable` `Shared` 在同一声明中同时指定、或。</span><span class="sxs-lookup"><span data-stu-id="f7412-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f7412-116">使用情况</span><span class="sxs-lookup"><span data-stu-id="f7412-116">Usage</span></span>  

 <span data-ttu-id="f7412-117">`NotOverridable` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="f7412-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f7412-118">Function 语句</span><span class="sxs-lookup"><span data-stu-id="f7412-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="f7412-119">Property Statement</span><span class="sxs-lookup"><span data-stu-id="f7412-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="f7412-120">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="f7412-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7412-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7412-121">See also</span></span>

- [<span data-ttu-id="f7412-122">修饰符</span><span class="sxs-lookup"><span data-stu-id="f7412-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f7412-123">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="f7412-123">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="f7412-124">New</span><span class="sxs-lookup"><span data-stu-id="f7412-124">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="f7412-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="f7412-125">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="f7412-126">替代</span><span class="sxs-lookup"><span data-stu-id="f7412-126">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="f7412-127">关键字</span><span class="sxs-lookup"><span data-stu-id="f7412-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="f7412-128">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="f7412-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
