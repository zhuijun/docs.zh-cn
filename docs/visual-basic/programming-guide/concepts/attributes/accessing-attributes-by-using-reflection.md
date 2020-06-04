---
title: 使用反射访问特性
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: c0da5c4ae00eb2bc80b10f63f4bfd39763445e55
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400753"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="a40f2-102">使用反射访问特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a40f2-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="a40f2-103">你可以定义自定义特性并将其放入源代码中这一事实，在没有检索该信息并对其进行操作的方法的情况下将没有任何价值。</span><span class="sxs-lookup"><span data-stu-id="a40f2-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="a40f2-104">通过使用反射，可以检索通过自定义特性定义的信息。</span><span class="sxs-lookup"><span data-stu-id="a40f2-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="a40f2-105">主要方法是 `GetCustomAttributes`，它返回对象数组，这些对象在运行时等效于源代码特性。</span><span class="sxs-lookup"><span data-stu-id="a40f2-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="a40f2-106">此方法有多个重载版本。</span><span class="sxs-lookup"><span data-stu-id="a40f2-106">This method has several overloaded versions.</span></span> <span data-ttu-id="a40f2-107">有关详细信息，请参阅 <xref:System.Attribute>。</span><span class="sxs-lookup"><span data-stu-id="a40f2-107">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="a40f2-108">特性规范，例如：</span><span class="sxs-lookup"><span data-stu-id="a40f2-108">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="a40f2-109">在概念上等效于此：</span><span class="sxs-lookup"><span data-stu-id="a40f2-109">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="a40f2-110">但是，在为特性查询 `SampleClass` 之前，代码将不会执行。</span><span class="sxs-lookup"><span data-stu-id="a40f2-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="a40f2-111">对 `SampleClass` 调用 `GetCustomAttributes` 会导致按上述方式构造并初始化一个 `Author` 对象。</span><span class="sxs-lookup"><span data-stu-id="a40f2-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="a40f2-112">如果该类具有其他特性，则将以类似方式构造其他特性对象。</span><span class="sxs-lookup"><span data-stu-id="a40f2-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="a40f2-113">然后 `GetCustomAttributes` 会以数组形式返回 `Author` 对象和任何其他特性对象。</span><span class="sxs-lookup"><span data-stu-id="a40f2-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="a40f2-114">之后你便可以循环访问此数组，根据每个数组元素的类型确定所应用的特性，并从特性对象中提取信息。</span><span class="sxs-lookup"><span data-stu-id="a40f2-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="a40f2-115">示例</span><span class="sxs-lookup"><span data-stu-id="a40f2-115">Example</span></span>

<span data-ttu-id="a40f2-116">此处是一个完整的示例。</span><span class="sxs-lookup"><span data-stu-id="a40f2-116">Here is a complete example.</span></span> <span data-ttu-id="a40f2-117">定义自定义特性、将其应用于多个实体，并通过反射对其进行检索。</span><span class="sxs-lookup"><span data-stu-id="a40f2-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a><span data-ttu-id="a40f2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a40f2-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="a40f2-119">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="a40f2-119">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a40f2-120">检索存储在特性中的信息</span><span class="sxs-lookup"><span data-stu-id="a40f2-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="a40f2-121">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a40f2-121">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="a40f2-122">特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a40f2-122">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="a40f2-123">创建自定义特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a40f2-123">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
