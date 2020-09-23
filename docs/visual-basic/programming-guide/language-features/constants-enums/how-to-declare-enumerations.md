---
title: 如何：声明枚举
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 752b425ba32efe41a1ab1aa75de20039d36f5e50
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058893"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="6d467-102">如何：声明枚举 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d467-102">How to: Declare Enumerations (Visual Basic)</span></span>

<span data-ttu-id="6d467-103">使用 `Enum` 类或模块的声明部分中的语句创建枚举。</span><span class="sxs-lookup"><span data-stu-id="6d467-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="6d467-104">不能在方法中声明枚举。</span><span class="sxs-lookup"><span data-stu-id="6d467-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="6d467-105">若要指定适当的访问级别，请使用 `Private` 、、 `Protected` `Friend` 或 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="6d467-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="6d467-106">`Enum`类型具有名称、基础类型和字段集，每个字段表示一个常量。</span><span class="sxs-lookup"><span data-stu-id="6d467-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="6d467-107">该名称必须是有效的 Visual Basic .NET 限定符。</span><span class="sxs-lookup"><span data-stu-id="6d467-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="6d467-108">基础类型必须是整数类型之一： `Byte` 、 `Short` `Long` 或 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="6d467-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="6d467-109">`Integer` 为默认值。</span><span class="sxs-lookup"><span data-stu-id="6d467-109">`Integer` is the default.</span></span> <span data-ttu-id="6d467-110">枚举总是强类型化的，并且不能与整数类型互换。</span><span class="sxs-lookup"><span data-stu-id="6d467-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="6d467-111">枚举的值不能为浮点值。</span><span class="sxs-lookup"><span data-stu-id="6d467-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="6d467-112">如果为枚举分配一个浮点值，则会 `Option Strict On` 产生编译器错误。</span><span class="sxs-lookup"><span data-stu-id="6d467-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="6d467-113">如果 `Option Strict` 为 `Off` ，则将值自动转换为 `Enum` 类型。</span><span class="sxs-lookup"><span data-stu-id="6d467-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="6d467-114">有关名称的信息，以及如何使用 `Imports` 语句使名称限定不必要，请参阅 [枚举和名称限定](enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="6d467-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="6d467-115">声明枚举</span><span class="sxs-lookup"><span data-stu-id="6d467-115">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="6d467-116">编写包含代码访问级别、 `Enum` 关键字和有效名称的声明，如下面的示例所示，其中每个都声明了不同的 `Enum` 。</span><span class="sxs-lookup"><span data-stu-id="6d467-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="6d467-117">定义枚举中的常量。</span><span class="sxs-lookup"><span data-stu-id="6d467-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="6d467-118">默认情况下，枚举中的第一个常量被初始化为 `0` ，后面的常量被初始化为比上一个常数大1的值。</span><span class="sxs-lookup"><span data-stu-id="6d467-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="6d467-119">例如，下面的枚举包含一个名为、值为、值为、值为、 `Days` `Sunday` `0` `Monday` `1` `Tuesday` 、值为的 `2` 常量等的常量。</span><span class="sxs-lookup"><span data-stu-id="6d467-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="6d467-120">可以使用赋值语句将值显式分配给枚举中的常量。</span><span class="sxs-lookup"><span data-stu-id="6d467-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="6d467-121">可以分配任何整数值，包括负数。</span><span class="sxs-lookup"><span data-stu-id="6d467-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="6d467-122">例如，您可能希望值小于零的常量表示错误条件。</span><span class="sxs-lookup"><span data-stu-id="6d467-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="6d467-123">在下面的枚举中，将 `Invalid` 显式赋给常数 `–1` ，并为该常数 `Sunday` 分配值 `0` 。</span><span class="sxs-lookup"><span data-stu-id="6d467-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="6d467-124">由于它是枚举中的第一个常数，因此 `Saturday` 也会初始化为值 `0` 。</span><span class="sxs-lookup"><span data-stu-id="6d467-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="6d467-125">的值 `Monday` `1` (一个大于) 的值 `Sunday` ; 的值 `Tuesday` 为 `2` ，依此类推。</span><span class="sxs-lookup"><span data-stu-id="6d467-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="6d467-126">将枚举声明为显式类型</span><span class="sxs-lookup"><span data-stu-id="6d467-126">To declare an enumeration as an explicit type</span></span>  
  
- <span data-ttu-id="6d467-127">使用子句指定枚举的类型 `As` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="6d467-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6d467-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="6d467-128">See also</span></span>

- [<span data-ttu-id="6d467-129">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="6d467-129">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="6d467-130">如何：引用枚举成员</span><span class="sxs-lookup"><span data-stu-id="6d467-130">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="6d467-131">如何：在 Visual Basic 中循环访问枚举</span><span class="sxs-lookup"><span data-stu-id="6d467-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="6d467-132">如何：确定与枚举值关联的字符串</span><span class="sxs-lookup"><span data-stu-id="6d467-132">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="6d467-133">何时使用枚举</span><span class="sxs-lookup"><span data-stu-id="6d467-133">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="6d467-134">常量概述</span><span class="sxs-lookup"><span data-stu-id="6d467-134">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="6d467-135">常数和文本数据类型</span><span class="sxs-lookup"><span data-stu-id="6d467-135">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="6d467-136">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="6d467-136">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
