---
title: 何时使用枚举
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 7b1b269a5d28d89cd491bac88fbefd4547fdc3c3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095624"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="e4c86-102">何时使用枚举 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4c86-102">When to Use an Enumeration (Visual Basic)</span></span>

<span data-ttu-id="e4c86-103">枚举提供了一种简单的方法来处理相关的常量集。</span><span class="sxs-lookup"><span data-stu-id="e4c86-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="e4c86-104">枚举（或 `Enum` ）是一组值的符号名称。</span><span class="sxs-lookup"><span data-stu-id="e4c86-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="e4c86-105">枚举被视为数据类型，可以使用它们来创建用于变量和属性的常量集。</span><span class="sxs-lookup"><span data-stu-id="e4c86-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="e4c86-106">何时使用枚举</span><span class="sxs-lookup"><span data-stu-id="e4c86-106">When to Use an Enumeration</span></span>  

 <span data-ttu-id="e4c86-107">只要过程接受有限的一组变量，就应考虑使用枚举。</span><span class="sxs-lookup"><span data-stu-id="e4c86-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="e4c86-108">枚举可用于更清晰且更易读的代码，特别是在使用有意义的名称时。</span><span class="sxs-lookup"><span data-stu-id="e4c86-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="e4c86-109">使用枚举的优点包括：</span><span class="sxs-lookup"><span data-stu-id="e4c86-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="e4c86-110">减少由转置或错误错误导致的错误。</span><span class="sxs-lookup"><span data-stu-id="e4c86-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="e4c86-111">以后可以轻松地更改值。</span><span class="sxs-lookup"><span data-stu-id="e4c86-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="e4c86-112">使代码更易于阅读，这意味着错误会在其中蔓延。</span><span class="sxs-lookup"><span data-stu-id="e4c86-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="e4c86-113">确保向前兼容性。</span><span class="sxs-lookup"><span data-stu-id="e4c86-113">Ensures forward compatibility.</span></span> <span data-ttu-id="e4c86-114">对于枚举，如果将来有人更改了与成员名称相对应的值，你的代码将不太可能失败。</span><span class="sxs-lookup"><span data-stu-id="e4c86-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="e4c86-115">命名枚举</span><span class="sxs-lookup"><span data-stu-id="e4c86-115">Naming Enumerations</span></span>  

 <span data-ttu-id="e4c86-116">为枚举成员使用命名约定。</span><span class="sxs-lookup"><span data-stu-id="e4c86-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="e4c86-117">当 Visual Basic 遇到枚举成员名称时，如果其他引用的类型库包含相同的名称，可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="e4c86-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="e4c86-118">使用唯一的前缀来标识应用程序或组件中的值。</span><span class="sxs-lookup"><span data-stu-id="e4c86-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="e4c86-119">当引用枚举的成员时，必须使用枚举名称限定成员名称，否则请使用 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="e4c86-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="e4c86-120">有关详细信息，请参阅 [枚举和名称限定](enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="e4c86-120">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="e4c86-121">预定义枚举</span><span class="sxs-lookup"><span data-stu-id="e4c86-121">Predefined Enumerations</span></span>  

 <span data-ttu-id="e4c86-122">Visual Basic 提供了许多预定义的枚举（如 `FirstDayOfWeek` 和 `MsgBoxResult` ），以方便您的代码。</span><span class="sxs-lookup"><span data-stu-id="e4c86-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="e4c86-123">有关这些变量的列表，请参阅 [常量和枚举](../../../language-reference/constants-and-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="e4c86-123">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c86-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="e4c86-124">See also</span></span>

- [<span data-ttu-id="e4c86-125">如何：声明枚举</span><span class="sxs-lookup"><span data-stu-id="e4c86-125">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="e4c86-126">如何：引用枚举成员</span><span class="sxs-lookup"><span data-stu-id="e4c86-126">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="e4c86-127">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="e4c86-127">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="e4c86-128">如何：在 Visual Basic 中循环访问枚举</span><span class="sxs-lookup"><span data-stu-id="e4c86-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="e4c86-129">如何：确定与枚举值关联的字符串</span><span class="sxs-lookup"><span data-stu-id="e4c86-129">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="e4c86-130">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="e4c86-130">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="e4c86-131">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="e4c86-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
