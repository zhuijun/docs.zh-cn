---
title: 泛型委托 - C# 编程指南
description: 了解如何通过 C# 使用泛型委托。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: d99271ca9f12e95743d633caac16aaa4151e9c41
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301900"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="b11c1-104">泛型委托（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="b11c1-104">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="b11c1-105">[委托](../../language-reference/builtin-types/reference-types.md)可以定义它自己的类型参数。</span><span class="sxs-lookup"><span data-stu-id="b11c1-105">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="b11c1-106">引用泛型委托的代码可以指定类型参数以创建封闭式构造类型，就像实例化泛型类或调用泛型方法一样，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="b11c1-106">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="b11c1-107">C# 2.0 版具有一种称为方法组转换的新功能，适用于具体委托类型和泛型委托类型，使你能够使用此简化语法编写上一行：</span><span class="sxs-lookup"><span data-stu-id="b11c1-107">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="b11c1-108">在泛型类中定义的委托可以用类方法使用的相同方式来使用泛型类类型参数。</span><span class="sxs-lookup"><span data-stu-id="b11c1-108">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="b11c1-109">引用委托的代码必须指定包含类的类型参数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b11c1-109">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="b11c1-110">根据典型设计模式定义事件时，泛型委托特别有用，因为发件人参数可以为强类型，无需在它和 <xref:System.Object> 之间强制转换。</span><span class="sxs-lookup"><span data-stu-id="b11c1-110">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="b11c1-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b11c1-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b11c1-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="b11c1-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b11c1-113">泛型介绍</span><span class="sxs-lookup"><span data-stu-id="b11c1-113">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="b11c1-114">泛型方法</span><span class="sxs-lookup"><span data-stu-id="b11c1-114">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="b11c1-115">泛型类</span><span class="sxs-lookup"><span data-stu-id="b11c1-115">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="b11c1-116">泛型接口</span><span class="sxs-lookup"><span data-stu-id="b11c1-116">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="b11c1-117">委托</span><span class="sxs-lookup"><span data-stu-id="b11c1-117">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="b11c1-118">泛型</span><span class="sxs-lookup"><span data-stu-id="b11c1-118">Generics</span></span>](../../../standard/generics/index.md)
