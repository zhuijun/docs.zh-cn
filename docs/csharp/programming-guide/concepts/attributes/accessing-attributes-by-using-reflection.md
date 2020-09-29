---
title: 使用反射访问特性 (C#)
description: 通过使用 GetCustomAttributes 方法，使用反射获取 C# 中使用自定义特性定义的信息。
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 2ed4e844d1c98bcf265572f201bce6679fd642e9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202625"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="91d87-103">使用反射访问特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="91d87-103">Accessing Attributes by Using Reflection (C#)</span></span>

<span data-ttu-id="91d87-104">你可以定义自定义特性并将其放入源代码中这一事实，在没有检索该信息并对其进行操作的方法的情况下将没有任何价值。</span><span class="sxs-lookup"><span data-stu-id="91d87-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="91d87-105">通过使用反射，可以检索通过自定义特性定义的信息。</span><span class="sxs-lookup"><span data-stu-id="91d87-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="91d87-106">主要方法是 `GetCustomAttributes`，它返回对象数组，这些对象在运行时等效于源代码特性。</span><span class="sxs-lookup"><span data-stu-id="91d87-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="91d87-107">此方法有多个重载版本。</span><span class="sxs-lookup"><span data-stu-id="91d87-107">This method has several overloaded versions.</span></span> <span data-ttu-id="91d87-108">有关详细信息，请参阅 <xref:System.Attribute>。</span><span class="sxs-lookup"><span data-stu-id="91d87-108">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="91d87-109">特性规范，例如：</span><span class="sxs-lookup"><span data-stu-id="91d87-109">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="91d87-110">在概念上等效于此：</span><span class="sxs-lookup"><span data-stu-id="91d87-110">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="91d87-111">但是，在为特性查询 `SampleClass` 之前，代码将不会执行。</span><span class="sxs-lookup"><span data-stu-id="91d87-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="91d87-112">对 `SampleClass` 调用 `GetCustomAttributes` 会导致按上述方式构造并初始化一个 `Author` 对象。</span><span class="sxs-lookup"><span data-stu-id="91d87-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="91d87-113">如果该类具有其他特性，则将以类似方式构造其他特性对象。</span><span class="sxs-lookup"><span data-stu-id="91d87-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="91d87-114">然后 `GetCustomAttributes` 会以数组形式返回 `Author` 对象和任何其他特性对象。</span><span class="sxs-lookup"><span data-stu-id="91d87-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="91d87-115">之后你便可以循环访问此数组，根据每个数组元素的类型确定所应用的特性，并从特性对象中提取信息。</span><span class="sxs-lookup"><span data-stu-id="91d87-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d87-116">示例</span><span class="sxs-lookup"><span data-stu-id="91d87-116">Example</span></span>  

 <span data-ttu-id="91d87-117">此处是一个完整的示例。</span><span class="sxs-lookup"><span data-stu-id="91d87-117">Here is a complete example.</span></span> <span data-ttu-id="91d87-118">定义自定义特性、将其应用于多个实体，并通过反射对其进行检索。</span><span class="sxs-lookup"><span data-stu-id="91d87-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="91d87-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="91d87-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="91d87-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="91d87-120">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="91d87-121">检索存储在特性中的信息</span><span class="sxs-lookup"><span data-stu-id="91d87-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="91d87-122">反射 (C#)</span><span class="sxs-lookup"><span data-stu-id="91d87-122">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="91d87-123">特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="91d87-123">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="91d87-124">创建自定义特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="91d87-124">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
