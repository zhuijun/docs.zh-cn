---
title: 创建自定义特性 (C#)
description: 了解如何通过定义从特性类派生的特性类，在 C# 中创建自定义特性。
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 6946b707134b2bdbc245b8786f144517a5870440
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202599"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="2144a-103">创建自定义特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2144a-103">Creating Custom Attributes (C#)</span></span>

<span data-ttu-id="2144a-104">可通过定义特性类创建自己的自定义特性，特性类是直接或间接派生自 <xref:System.Attribute> 的类，可快速轻松地识别元数据中的特性定义。</span><span class="sxs-lookup"><span data-stu-id="2144a-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="2144a-105">假设希望使用编写类型的程序员的姓名来标记该类型。</span><span class="sxs-lookup"><span data-stu-id="2144a-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="2144a-106">可能需要定义一个自定义 `Author` 特性类：</span><span class="sxs-lookup"><span data-stu-id="2144a-106">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="2144a-107">类名 `AuthorAttribute` 是该特性的名称，即 `Author` 加上 `Attribute` 后缀。</span><span class="sxs-lookup"><span data-stu-id="2144a-107">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="2144a-108">由于该类派生自 `System.Attribute`，因此它是一个自定义特性类。</span><span class="sxs-lookup"><span data-stu-id="2144a-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="2144a-109">构造函数的参数是自定义特性的位置参数。</span><span class="sxs-lookup"><span data-stu-id="2144a-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="2144a-110">在此示例中，`name` 是位置参数。</span><span class="sxs-lookup"><span data-stu-id="2144a-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="2144a-111">所有公共读写字段或属性都是命名参数。</span><span class="sxs-lookup"><span data-stu-id="2144a-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="2144a-112">在本例中，`version` 是唯一的命名参数。</span><span class="sxs-lookup"><span data-stu-id="2144a-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="2144a-113">请注意，使用 `AttributeUsage` 特性可使 `Author` 特性仅对类和 `struct` 声明有效。</span><span class="sxs-lookup"><span data-stu-id="2144a-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="2144a-114">可按如下方式使用这一新特性：</span><span class="sxs-lookup"><span data-stu-id="2144a-114">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="2144a-115">`AttributeUsage` 有一个命名参数 `AllowMultiple`，通过此命名参数可一次或多次使用自定义特性。</span><span class="sxs-lookup"><span data-stu-id="2144a-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="2144a-116">下面的代码示例创建了一个多用特性。</span><span class="sxs-lookup"><span data-stu-id="2144a-116">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="2144a-117">在下面的代码示例中，某个类应用了同一类型的多个特性。</span><span class="sxs-lookup"><span data-stu-id="2144a-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2144a-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="2144a-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="2144a-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2144a-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="2144a-120">编写自定义特性</span><span class="sxs-lookup"><span data-stu-id="2144a-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="2144a-121">反射 (C#)</span><span class="sxs-lookup"><span data-stu-id="2144a-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="2144a-122">特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2144a-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="2144a-123">使用反射访问特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="2144a-123">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="2144a-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="2144a-124">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
