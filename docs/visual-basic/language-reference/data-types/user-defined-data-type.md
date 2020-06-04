---
title: 用户定义的数据类型
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: fbd9536a54d7fb471d6cb2e130b14a84e40a4940
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415487"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="77ce8-102">用户定义的数据类型</span><span class="sxs-lookup"><span data-stu-id="77ce8-102">User-Defined Data Type</span></span>

<span data-ttu-id="77ce8-103">以您定义的格式保存数据。</span><span class="sxs-lookup"><span data-stu-id="77ce8-103">Holds data in a format you define.</span></span> <span data-ttu-id="77ce8-104">`Structure`语句定义格式。</span><span class="sxs-lookup"><span data-stu-id="77ce8-104">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="77ce8-105">以前版本的 Visual Basic 支持用户定义的类型（UDT）。</span><span class="sxs-lookup"><span data-stu-id="77ce8-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="77ce8-106">当前版本将 UDT 扩展到*结构*。</span><span class="sxs-lookup"><span data-stu-id="77ce8-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="77ce8-107">结构是一种或多种数据类型*成员*的串联。</span><span class="sxs-lookup"><span data-stu-id="77ce8-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="77ce8-108">Visual Basic 将结构视为单个单元，但你也可以单独访问其成员。</span><span class="sxs-lookup"><span data-stu-id="77ce8-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="77ce8-109">备注</span><span class="sxs-lookup"><span data-stu-id="77ce8-109">Remarks</span></span>

<span data-ttu-id="77ce8-110">当需要将各种数据类型组合成单个单元时，或在没有任何基本数据类型满足您的需求时，可定义和使用结构数据类型。</span><span class="sxs-lookup"><span data-stu-id="77ce8-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="77ce8-111">结构数据类型的默认值由其每个成员的默认值组合而成。</span><span class="sxs-lookup"><span data-stu-id="77ce8-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="77ce8-112">声明格式</span><span class="sxs-lookup"><span data-stu-id="77ce8-112">Declaration Format</span></span>

<span data-ttu-id="77ce8-113">结构声明以[结构语句](../statements/structure-statement.md)开头，以 `End Structure` 语句结尾。</span><span class="sxs-lookup"><span data-stu-id="77ce8-113">A structure declaration starts with the [Structure Statement](../statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="77ce8-114">`Structure`语句提供结构的名称，该结构也是结构正在定义的数据类型的标识符。</span><span class="sxs-lookup"><span data-stu-id="77ce8-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="77ce8-115">代码的其他部分可以使用此标识符来声明变量、参数和函数返回值，使其成为此结构的数据类型。</span><span class="sxs-lookup"><span data-stu-id="77ce8-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="77ce8-116">和语句之间的 `Structure` 声明 `End Structure` 定义结构的成员。</span><span class="sxs-lookup"><span data-stu-id="77ce8-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="77ce8-117">成员访问级别</span><span class="sxs-lookup"><span data-stu-id="77ce8-117">Member Access Levels</span></span>

<span data-ttu-id="77ce8-118">必须使用[Dim 语句](../statements/dim-statement.md)或指定访问级别的语句（如[Public](../modifiers/public.md)、 [Friend](../modifiers/friend.md)或[Private](../modifiers/private.md)）声明每个成员。</span><span class="sxs-lookup"><span data-stu-id="77ce8-118">You must declare every member using a [Dim Statement](../statements/dim-statement.md) or a statement that specifies access level, such as [Public](../modifiers/public.md), [Friend](../modifiers/friend.md), or [Private](../modifiers/private.md).</span></span> <span data-ttu-id="77ce8-119">如果使用 `Dim` 语句，则访问级别默认为 "公共"。</span><span class="sxs-lookup"><span data-stu-id="77ce8-119">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="77ce8-120">编程提示</span><span class="sxs-lookup"><span data-stu-id="77ce8-120">Programming Tips</span></span>

- <span data-ttu-id="77ce8-121">**内存消耗。**</span><span class="sxs-lookup"><span data-stu-id="77ce8-121">**Memory Consumption.**</span></span> <span data-ttu-id="77ce8-122">与所有复合数据类型一样，不能通过将其成员的标称存储分配相加来安全地计算结构的总内存消耗量。</span><span class="sxs-lookup"><span data-stu-id="77ce8-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="77ce8-123">而且，不能安全地假设内存中的存储顺序与声明顺序相同。</span><span class="sxs-lookup"><span data-stu-id="77ce8-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="77ce8-124">如果需要控制结构的存储布局，则可以将属性应用于 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 该 `Structure` 语句。</span><span class="sxs-lookup"><span data-stu-id="77ce8-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="77ce8-125">**互操作注意事项。**</span><span class="sxs-lookup"><span data-stu-id="77ce8-125">**Interop Considerations.**</span></span> <span data-ttu-id="77ce8-126">如果与不是为 .NET Framework 编写的组件（如自动化或 COM 对象）交互，请记住，其他环境中的用户定义类型与 Visual Basic 结构类型不兼容。</span><span class="sxs-lookup"><span data-stu-id="77ce8-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="77ce8-127">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="77ce8-127">**Widening.**</span></span> <span data-ttu-id="77ce8-128">不会与任何结构数据类型自动转换。</span><span class="sxs-lookup"><span data-stu-id="77ce8-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="77ce8-129">您可以使用[Operator 语句](../statements/operator-statement.md)在结构上定义转换运算符，并且可以将每个转换运算符声明为 `Widening` 或 `Narrowing` 。</span><span class="sxs-lookup"><span data-stu-id="77ce8-129">You can define conversion operators on your structure using the [Operator Statement](../statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="77ce8-130">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="77ce8-130">**Type Characters.**</span></span> <span data-ttu-id="77ce8-131">结构数据类型没有文本类型字符或标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="77ce8-131">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="77ce8-132">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="77ce8-132">**Framework Type.**</span></span> <span data-ttu-id="77ce8-133">.NET Framework 中没有相应的类型。</span><span class="sxs-lookup"><span data-stu-id="77ce8-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="77ce8-134">所有结构都继承自 .NET Framework 类 <xref:System.ValueType?displayProperty=nameWithType> ，但没有单个结构对应于 <xref:System.ValueType?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="77ce8-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="77ce8-135">示例</span><span class="sxs-lookup"><span data-stu-id="77ce8-135">Example</span></span>

<span data-ttu-id="77ce8-136">以下范例显示了结构声明的轮廓。</span><span class="sxs-lookup"><span data-stu-id="77ce8-136">The following paradigm shows the outline of the declaration of a structure.</span></span>

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="77ce8-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77ce8-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="77ce8-138">数据类型</span><span class="sxs-lookup"><span data-stu-id="77ce8-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="77ce8-139">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="77ce8-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="77ce8-140">转换摘要</span><span class="sxs-lookup"><span data-stu-id="77ce8-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="77ce8-141">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="77ce8-141">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="77ce8-142">Widening</span><span class="sxs-lookup"><span data-stu-id="77ce8-142">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="77ce8-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="77ce8-143">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="77ce8-144">结构</span><span class="sxs-lookup"><span data-stu-id="77ce8-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="77ce8-145">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="77ce8-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
