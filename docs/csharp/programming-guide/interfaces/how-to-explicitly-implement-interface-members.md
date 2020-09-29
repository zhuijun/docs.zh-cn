---
title: 如何显式实现接口成员 - C# 编程指南
description: 了解如何在此 C# 示例中显式实现接口成员。 通过接口实例访问这些成员。
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: a9c019cdcf6e229199d980a2d1913df7c72a2169
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157390"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="d5edf-104">如何显式实现接口成员（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="d5edf-104">How to explicitly implement interface members (C# Programming Guide)</span></span>

<span data-ttu-id="d5edf-105">本示例声明一个[接口](../../language-reference/keywords/interface.md)`IDimensions` 和一个类 `Box`，显式实现了接口成员 `GetLength` 和 `GetWidth`。</span><span class="sxs-lookup"><span data-stu-id="d5edf-105">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="d5edf-106">通过接口实例 `dimensions` 访问这些成员。</span><span class="sxs-lookup"><span data-stu-id="d5edf-106">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5edf-107">示例</span><span class="sxs-lookup"><span data-stu-id="d5edf-107">Example</span></span>  

 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d5edf-108">可靠编程</span><span class="sxs-lookup"><span data-stu-id="d5edf-108">Robust Programming</span></span>  
  
- <span data-ttu-id="d5edf-109">请注意，注释掉了 `Main` 方法中以下行，因为它们将产生编译错误。</span><span class="sxs-lookup"><span data-stu-id="d5edf-109">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="d5edf-110">显式实现的接口成员不能从[类](../../language-reference/keywords/class.md)实例访问：</span><span class="sxs-lookup"><span data-stu-id="d5edf-110">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="d5edf-111">另请注意 `Main` 方法中的以下行成功输出了框的尺寸，因为这些方法是从接口实例调用的：</span><span class="sxs-lookup"><span data-stu-id="d5edf-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="d5edf-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5edf-112">See also</span></span>

- [<span data-ttu-id="d5edf-113">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="d5edf-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d5edf-114">类和结构</span><span class="sxs-lookup"><span data-stu-id="d5edf-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="d5edf-115">接口</span><span class="sxs-lookup"><span data-stu-id="d5edf-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="d5edf-116">如何显式实现两个接口的成员</span><span class="sxs-lookup"><span data-stu-id="d5edf-116">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
