---
title: 协变和逆变 (C#)
description: 了解协变和逆变，查看它们如何影响赋值兼容性。 查看展示两者区别的代码示例。
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: ad4b2a7d7925d7893eb5a8e1d2d7c9ee3dcbd527
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465658"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="d4df6-104">协变和逆变 (C#)</span><span class="sxs-lookup"><span data-stu-id="d4df6-104">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="d4df6-105">在 C# 中，协变和逆变能够实现数组类型、委托类型和泛型类型参数的隐式引用转换。</span><span class="sxs-lookup"><span data-stu-id="d4df6-105">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="d4df6-106">协变保留分配兼容性，逆变则与之相反。</span><span class="sxs-lookup"><span data-stu-id="d4df6-106">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="d4df6-107">以下代码演示分配兼容性、协变和逆变之间的差异。</span><span class="sxs-lookup"><span data-stu-id="d4df6-107">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="d4df6-108">数组的协变使派生程度更大的类型的数组能够隐式转换为派生程度更小的类型的数组。</span><span class="sxs-lookup"><span data-stu-id="d4df6-108">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="d4df6-109">但是此操作不是类型安全的操作，如以下代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="d4df6-109">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="d4df6-110">对方法组的协变和逆变支持允许将方法签名与委托类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="d4df6-110">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="d4df6-111">这样，不仅可以将具有匹配签名的方法分配给委托，还可以分配与委托类型指定的派生类型相比，返回派生程度更大的类型的方法（协变）或接受具有派生程度更小的类型的参数的方法（逆变）。</span><span class="sxs-lookup"><span data-stu-id="d4df6-111">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="d4df6-112">有关详细信息，请参阅[委托中的变体 (C#)](./variance-in-delegates.md) 和[使用委托中的变体 (C#)](./using-variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="d4df6-112">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="d4df6-113">以下代码示例演示对方法组的协变和逆变支持。</span><span class="sxs-lookup"><span data-stu-id="d4df6-113">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="d4df6-114">在 .NET Framework 4 或更高版本中，C# 支持在泛型接口和委托中使用协变和逆变，并允许隐式转换泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="d4df6-114">In .NET Framework 4 and later versions, C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="d4df6-115">有关详细信息，请参阅[泛型接口中的变体 (C#)](./variance-in-generic-interfaces.md) 和[委托中的变体 (C#)](./variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="d4df6-115">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="d4df6-116">以下代码示例演示泛型接口的隐式引用转换。</span><span class="sxs-lookup"><span data-stu-id="d4df6-116">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="d4df6-117">如果泛型接口或委托的泛型参数被声明为协变或逆变，该泛型接口或委托则被称为“变体”。</span><span class="sxs-lookup"><span data-stu-id="d4df6-117">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="d4df6-118">凭借 C#，能够创建自己的变体接口和委托。</span><span class="sxs-lookup"><span data-stu-id="d4df6-118">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="d4df6-119">有关详细信息，请参阅[创建变体泛型接口 (C#)](./creating-variant-generic-interfaces.md) 和[委托中的变体 (C#)](./variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="d4df6-119">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="d4df6-120">相关主题</span><span class="sxs-lookup"><span data-stu-id="d4df6-120">Related Topics</span></span>  
  
|<span data-ttu-id="d4df6-121">Title</span><span class="sxs-lookup"><span data-stu-id="d4df6-121">Title</span></span>|<span data-ttu-id="d4df6-122">描述</span><span class="sxs-lookup"><span data-stu-id="d4df6-122">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d4df6-123">泛型接口中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="d4df6-123">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="d4df6-124">讨论泛型接口中的协变和逆变，提供 .NET 中的变体泛型接口列表。</span><span class="sxs-lookup"><span data-stu-id="d4df6-124">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in .NET.</span></span>|  
|[<span data-ttu-id="d4df6-125">创建变体泛型接口 (C#)</span><span class="sxs-lookup"><span data-stu-id="d4df6-125">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="d4df6-126">演示如何创建自定义变体接口。</span><span class="sxs-lookup"><span data-stu-id="d4df6-126">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="d4df6-127">在泛型集合的接口中使用变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="d4df6-127">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="d4df6-128">演示 <xref:System.Collections.Generic.IEnumerable%601> 接口和 <xref:System.IComparable%601> 接口中对协变和逆变的支持如何帮助重复使用代码。</span><span class="sxs-lookup"><span data-stu-id="d4df6-128">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="d4df6-129">委托中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="d4df6-129">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="d4df6-130">讨论泛型委托和非泛型委托中的协变和逆变，并提供 .NET 中的变体泛型委托列表。</span><span class="sxs-lookup"><span data-stu-id="d4df6-130">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in .NET.</span></span>|  
|[<span data-ttu-id="d4df6-131">使用委托中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="d4df6-131">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="d4df6-132">演示如何使用非泛型委托中的协变和逆变支持以将方法签名与委托类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="d4df6-132">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="d4df6-133">对 Func 和 Action 泛型委托使用变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="d4df6-133">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="d4df6-134">演示 `Func` 委托和 `Action` 委托中对协变和逆变的支持如何帮助重复使用代码。</span><span class="sxs-lookup"><span data-stu-id="d4df6-134">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
