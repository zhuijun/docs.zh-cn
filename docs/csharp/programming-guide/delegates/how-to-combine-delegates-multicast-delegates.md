---
title: 如何合并委托（多播委托）- C# 编程指南
description: 了解如何合并委托以创建多播委托。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302732"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="90050-104">如何合并委托（多播委托）（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="90050-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="90050-105">此示例演示如何创建多播委托。</span><span class="sxs-lookup"><span data-stu-id="90050-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="90050-106">[委托](../../language-reference/builtin-types/reference-types.md)对象的一个有用属性在于可通过使用 `+` 运算符将多个对象分配到一个委托实例。</span><span class="sxs-lookup"><span data-stu-id="90050-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="90050-107">多播委托包含已分配委托列表。</span><span class="sxs-lookup"><span data-stu-id="90050-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="90050-108">此多播委托被调用时会依次调用列表中的委托。</span><span class="sxs-lookup"><span data-stu-id="90050-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="90050-109">仅可合并类型相同的委托。</span><span class="sxs-lookup"><span data-stu-id="90050-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="90050-110">`-` 运算符可用于从多播委托中删除组件委托。</span><span class="sxs-lookup"><span data-stu-id="90050-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90050-111">示例</span><span class="sxs-lookup"><span data-stu-id="90050-111">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="90050-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90050-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="90050-113">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="90050-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="90050-114">事件</span><span class="sxs-lookup"><span data-stu-id="90050-114">Events</span></span>](../events/index.md)
