---
title: 自动实现的属性 - C# 编程指南
description: 对于 C# 中自动实现的属性，编译器将创建仅通过属性的 get 和 set 访问器访问的专用、匿名支持字段。
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 72f774d84266292412be9b954fc206debc8ac55e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555895"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="581f8-103">自动实现的属性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="581f8-103">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="581f8-104">在 C# 3.0 及更高版本，当属性访问器中不需要任何其他逻辑时，自动实现的属性会使属性声明更加简洁。</span><span class="sxs-lookup"><span data-stu-id="581f8-104">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="581f8-105">它们还允许客户端代码创建对象。</span><span class="sxs-lookup"><span data-stu-id="581f8-105">They also enable client code to create objects.</span></span> <span data-ttu-id="581f8-106">当你声明以下示例中所示的属性时，编译器将创建仅可以通过该属性的 `get` 和 `set` 访问器访问的专用、匿名支持字段。</span><span class="sxs-lookup"><span data-stu-id="581f8-106">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="581f8-107">示例</span><span class="sxs-lookup"><span data-stu-id="581f8-107">Example</span></span>

<span data-ttu-id="581f8-108">下列示例演示一个简单的类，它具有某些自动实现的属性：</span><span class="sxs-lookup"><span data-stu-id="581f8-108">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="581f8-109">不能在接口中声明自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="581f8-109">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="581f8-110">自动实现的属性声明一个私有实例支持字段，并且接口可能不声明实例字段。</span><span class="sxs-lookup"><span data-stu-id="581f8-110">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="581f8-111">如果在接口中声明属性而不定义主体，请使用访问器声明属性，访问器必须由实现该接口的每个类型实现。</span><span class="sxs-lookup"><span data-stu-id="581f8-111">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="581f8-112">在 C# 6 和更高版本中，你可以像字段一样初始化自动实现属性：</span><span class="sxs-lookup"><span data-stu-id="581f8-112">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="581f8-113">上一示例中所示的类是可变的。</span><span class="sxs-lookup"><span data-stu-id="581f8-113">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="581f8-114">客户端代码在创建后可以更改对象中的值。</span><span class="sxs-lookup"><span data-stu-id="581f8-114">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="581f8-115">在包含重要行为（方法）以及数据的复杂类中，通常有必要具有公共属性。</span><span class="sxs-lookup"><span data-stu-id="581f8-115">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="581f8-116">但是，对于较小类或仅封装一组值（数据）且只有很少行为或没有行为的结构，则应该通过声明 set 访问器为[专用](../../language-reference/keywords/private.md)（对使用者的不可变）或通过声明仅一个 get 访问器（除构造函数外都不可变），使对象不可变。</span><span class="sxs-lookup"><span data-stu-id="581f8-116">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="581f8-117">有关详细信息，请参阅[如何使用自动实现的属性实现轻量类](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="581f8-117">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="581f8-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="581f8-118">See also</span></span>

- [<span data-ttu-id="581f8-119">属性</span><span class="sxs-lookup"><span data-stu-id="581f8-119">Properties</span></span>](./properties.md)
- [<span data-ttu-id="581f8-120">修饰符</span><span class="sxs-lookup"><span data-stu-id="581f8-120">Modifiers</span></span>](../../language-reference/keywords/index.md)
