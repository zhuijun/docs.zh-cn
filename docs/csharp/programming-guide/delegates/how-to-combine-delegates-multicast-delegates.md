---
title: 如何合并委托（多播委托）- C# 编程指南
description: 了解如何合并委托以创建多播委托。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 3e86c8ed4b7b091ee8c75930d427c22aa5bc0c52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185946"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="06f95-104">如何合并委托（多播委托）（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="06f95-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>

<span data-ttu-id="06f95-105">此示例演示如何创建多播委托。</span><span class="sxs-lookup"><span data-stu-id="06f95-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="06f95-106">[委托](../../language-reference/builtin-types/reference-types.md)对象的一个有用属性在于可通过使用 `+` 运算符将多个对象分配到一个委托实例。</span><span class="sxs-lookup"><span data-stu-id="06f95-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="06f95-107">多播委托包含已分配委托列表。</span><span class="sxs-lookup"><span data-stu-id="06f95-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="06f95-108">此多播委托被调用时会依次调用列表中的委托。</span><span class="sxs-lookup"><span data-stu-id="06f95-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="06f95-109">仅可合并类型相同的委托。</span><span class="sxs-lookup"><span data-stu-id="06f95-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="06f95-110">`-` 运算符可用于从多播委托中删除组件委托。</span><span class="sxs-lookup"><span data-stu-id="06f95-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06f95-111">示例</span><span class="sxs-lookup"><span data-stu-id="06f95-111">Example</span></span>  

 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="06f95-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06f95-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="06f95-113">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="06f95-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="06f95-114">事件</span><span class="sxs-lookup"><span data-stu-id="06f95-114">Events</span></span>](../events/index.md)
