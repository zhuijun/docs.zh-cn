---
title: 如何：确定对象变量引用的类型
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: d3224000f5958a8619e38c4d2f6dc5dbb275ad45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410485"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="5e796-102">如何：确定对象变量引用的类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e796-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="5e796-103">对象变量包含指向存储在其他位置的数据的指针。</span><span class="sxs-lookup"><span data-stu-id="5e796-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="5e796-104">该数据的类型在运行时可能会更改。</span><span class="sxs-lookup"><span data-stu-id="5e796-104">The type of that data can change during run time.</span></span> <span data-ttu-id="5e796-105">随时都可以使用 <xref:System.Type.GetTypeCode%2A> 方法确定当前运行时类型，或使用[TypeOf 运算符](../../../language-reference/operators/typeof-operator.md)来找出当前运行时类型是否与指定的类型兼容。</span><span class="sxs-lookup"><span data-stu-id="5e796-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="5e796-106">确定对象变量当前所引用的确切类型</span><span class="sxs-lookup"><span data-stu-id="5e796-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="5e796-107">在对象变量上，调用 <xref:System.Object.GetType%2A> 方法来检索 <xref:System.Type?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="5e796-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="5e796-108">在 <xref:System.Type?displayProperty=nameWithType> 类上，调用共享方法 <xref:System.Type.GetTypeCode%2A> 以检索 <xref:System.TypeCode> 该对象的类型的枚举值。</span><span class="sxs-lookup"><span data-stu-id="5e796-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="5e796-109">您可以 <xref:System.TypeCode> 根据任何所需的枚举成员（例如）测试枚举值 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="5e796-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="5e796-110">确定对象变量的类型是否与指定的类型兼容</span><span class="sxs-lookup"><span data-stu-id="5e796-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="5e796-111">将 `TypeOf` 运算符与[Is 运算符](../../../language-reference/operators/is-operator.md)结合使用来测试具有 `TypeOf` ... 表达式的对象 `Is` 。</span><span class="sxs-lookup"><span data-stu-id="5e796-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="5e796-112">`TypeOf` `Is` `True` 如果对象的运行时类型与指定的类型兼容，则 ... 表达式将返回。</span><span class="sxs-lookup"><span data-stu-id="5e796-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="5e796-113">兼容性的条件取决于指定的类型是类、结构还是接口。</span><span class="sxs-lookup"><span data-stu-id="5e796-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="5e796-114">通常，如果对象的类型与、继承自或实现指定的类型，则类型是兼容的。</span><span class="sxs-lookup"><span data-stu-id="5e796-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="5e796-115">有关详细信息，请参阅[TypeOf 运算符](../../../language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="5e796-115">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="5e796-116">编译代码</span><span class="sxs-lookup"><span data-stu-id="5e796-116">Compile the code</span></span>

<span data-ttu-id="5e796-117">请注意，指定的类型不能为变量或表达式。</span><span class="sxs-lookup"><span data-stu-id="5e796-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="5e796-118">它必须是已定义类型的名称，如类、结构或接口。</span><span class="sxs-lookup"><span data-stu-id="5e796-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="5e796-119">这包括内部类型，例如 `Integer` 和 `String` 。</span><span class="sxs-lookup"><span data-stu-id="5e796-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e796-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e796-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="5e796-121">对象变量</span><span class="sxs-lookup"><span data-stu-id="5e796-121">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="5e796-122">对象变量值</span><span class="sxs-lookup"><span data-stu-id="5e796-122">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="5e796-123">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="5e796-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
