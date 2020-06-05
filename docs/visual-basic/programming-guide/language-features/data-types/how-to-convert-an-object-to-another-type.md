---
title: 如何：将一个对象转换为其他类型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393956"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="244b1-102">如何：在 Visual Basic 中将一个对象转换为其他类型</span><span class="sxs-lookup"><span data-stu-id="244b1-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="244b1-103">您可以 `Object` 使用转换关键字（如[CType 函数](../../../language-reference/functions/ctype-function.md)）将变量转换为另一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="244b1-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="244b1-104">示例</span><span class="sxs-lookup"><span data-stu-id="244b1-104">Example</span></span>  
 <span data-ttu-id="244b1-105">下面的示例将 `Object` 变量转换为 `Integer` 和 `String` 。</span><span class="sxs-lookup"><span data-stu-id="244b1-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="244b1-106">如果知道变量的内容属于 `Object` 特定的数据类型，最好将该变量转换为该数据类型。</span><span class="sxs-lookup"><span data-stu-id="244b1-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="244b1-107">如果继续使用该 `Object` 变量，则会产生*装箱*和*取消装箱*（对于值类型）或*后期绑定*（对于引用类型）。</span><span class="sxs-lookup"><span data-stu-id="244b1-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="244b1-108">这些操作都需要额外的执行时间，并使性能更慢。</span><span class="sxs-lookup"><span data-stu-id="244b1-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="244b1-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="244b1-109">Compile the code</span></span>  
 <span data-ttu-id="244b1-110">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="244b1-110">This example requires:</span></span>  
  
- <span data-ttu-id="244b1-111">对 <xref:System?displayProperty=nameWithType> 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="244b1-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244b1-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="244b1-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="244b1-113">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="244b1-113">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="244b1-114">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="244b1-114">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="244b1-115">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="244b1-115">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="244b1-116">字符串和其他类型之间的转换</span><span class="sxs-lookup"><span data-stu-id="244b1-116">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="244b1-117">数组转换</span><span class="sxs-lookup"><span data-stu-id="244b1-117">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="244b1-118">结构</span><span class="sxs-lookup"><span data-stu-id="244b1-118">Structures</span></span>](structures.md)
- [<span data-ttu-id="244b1-119">数据类型</span><span class="sxs-lookup"><span data-stu-id="244b1-119">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="244b1-120">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="244b1-120">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
