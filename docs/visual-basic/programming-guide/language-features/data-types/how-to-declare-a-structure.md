---
title: 如何：声明结构
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: bffdc5974eff6b71e0abc4780a61aa300769eed6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058542"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="6a03f-102">如何：声明结构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a03f-102">How to: Declare a Structure (Visual Basic)</span></span>

<span data-ttu-id="6a03f-103">使用 [Structure 语句](../../../language-reference/statements/structure-statement.md)开始结构声明，并使用 `End Structure` 语句结束。</span><span class="sxs-lookup"><span data-stu-id="6a03f-103">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="6a03f-104">在这两个语句之间必须至少声明一个 *元素*。</span><span class="sxs-lookup"><span data-stu-id="6a03f-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="6a03f-105">元素可以是任何数据类型，但必须至少有一个是非共享变量或非共享、非自定义事件。</span><span class="sxs-lookup"><span data-stu-id="6a03f-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="6a03f-106">不能在结构声明中初始化任何结构元素。</span><span class="sxs-lookup"><span data-stu-id="6a03f-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="6a03f-107">将变量声明为结构类型时，可以通过变量访问元素，为这些元素赋值。</span><span class="sxs-lookup"><span data-stu-id="6a03f-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="6a03f-108">有关结构和类之间的差异的讨论，请参阅 [结构和类](structures-and-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="6a03f-108">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="6a03f-109">出于演示目的，请考虑要跟踪员工姓名、电话分机和薪金的情况。</span><span class="sxs-lookup"><span data-stu-id="6a03f-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="6a03f-110">结构允许在单个变量中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="6a03f-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="6a03f-111">声明结构</span><span class="sxs-lookup"><span data-stu-id="6a03f-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="6a03f-112">为结构创建开始语句和结束语句。</span><span class="sxs-lookup"><span data-stu-id="6a03f-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="6a03f-113">您可以使用 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)或 [Private](../../../language-reference/modifiers/private.md) 关键字指定结构的访问级别，也可以让它默认为 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="6a03f-113">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="6a03f-114">向结构的主体中添加元素。</span><span class="sxs-lookup"><span data-stu-id="6a03f-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="6a03f-115">结构中必须至少有一个元素。</span><span class="sxs-lookup"><span data-stu-id="6a03f-115">A structure must have at least one element.</span></span> <span data-ttu-id="6a03f-116">必须声明每个元素并为其指定访问级别。</span><span class="sxs-lookup"><span data-stu-id="6a03f-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="6a03f-117">如果使用不带任何关键字的 [Dim 语句](../../../language-reference/statements/dim-statement.md) ，可访问性默认为 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="6a03f-117">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="6a03f-118">`salary`前面的示例中的字段是 `Private` ，这意味着它在结构外部不可访问，甚至是从包含类中访问。</span><span class="sxs-lookup"><span data-stu-id="6a03f-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="6a03f-119">但是，该 `giveRaise` 过程是 `Public` ，因此可以从结构外部调用它。</span><span class="sxs-lookup"><span data-stu-id="6a03f-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="6a03f-120">同样，您可以 `salaryReviewTime` 从结构外部引发事件。</span><span class="sxs-lookup"><span data-stu-id="6a03f-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="6a03f-121">除了变量、 `Sub` 过程和事件外，还可以在结构中定义常量、 `Function` 过程和属性。</span><span class="sxs-lookup"><span data-stu-id="6a03f-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="6a03f-122">最多可以将一个属性指定为 *默认属性*，前提是它至少采用一个参数。</span><span class="sxs-lookup"><span data-stu-id="6a03f-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="6a03f-123">您可以使用共享过程处理事件[Shared](../../../language-reference/modifiers/shared.md) `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="6a03f-123">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="6a03f-124">有关详细信息，请参阅 [如何：在 Visual Basic 中声明和调用默认属性](../procedures/how-to-declare-and-call-a-default-property.md)。</span><span class="sxs-lookup"><span data-stu-id="6a03f-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a03f-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a03f-125">See also</span></span>

- [<span data-ttu-id="6a03f-126">数据类型</span><span class="sxs-lookup"><span data-stu-id="6a03f-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="6a03f-127">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="6a03f-127">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="6a03f-128">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="6a03f-128">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="6a03f-129">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="6a03f-129">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="6a03f-130">结构</span><span class="sxs-lookup"><span data-stu-id="6a03f-130">Structures</span></span>](structures.md)
- [<span data-ttu-id="6a03f-131">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="6a03f-131">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="6a03f-132">结构变量</span><span class="sxs-lookup"><span data-stu-id="6a03f-132">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="6a03f-133">结构和其他编程元素</span><span class="sxs-lookup"><span data-stu-id="6a03f-133">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="6a03f-134">结构和类</span><span class="sxs-lookup"><span data-stu-id="6a03f-134">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="6a03f-135">用户定义的数据类型</span><span class="sxs-lookup"><span data-stu-id="6a03f-135">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
