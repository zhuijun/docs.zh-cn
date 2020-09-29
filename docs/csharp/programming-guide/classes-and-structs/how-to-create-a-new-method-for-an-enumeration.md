---
title: 如何为枚举创建新方法 - C# 编程指南
description: 了解如何使用 C# 中的扩展方法将功能添加到枚举。 此示例演示用于名为“等级分”的枚举的名为“合格”的扩展方法。
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 2714b29d64e18250f0fe379aee1c09c242d3f63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174259"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="0538a-104">如何为枚举创建新方法（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="0538a-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>

<span data-ttu-id="0538a-105">可使用扩展方法添加特定于某个特定枚举类型的功能。</span><span class="sxs-lookup"><span data-stu-id="0538a-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0538a-106">示例</span><span class="sxs-lookup"><span data-stu-id="0538a-106">Example</span></span>  

 <span data-ttu-id="0538a-107">在下面的示例中，`Grades` 枚举表示学生可能在班里收到的字母等级分。</span><span class="sxs-lookup"><span data-stu-id="0538a-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="0538a-108">该示例将一个名为 `Passing` 的扩展方法添加到 `Grades` 类型中，以便该类型的每个实例现在都“知道”它是否表示合格的等级分。</span><span class="sxs-lookup"><span data-stu-id="0538a-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="0538a-109">请注意，`Extensions` 类还包含一个动态更新的静态变量，并且扩展方法的返回值反映了该变量的当前值。</span><span class="sxs-lookup"><span data-stu-id="0538a-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="0538a-110">这表明在幕后，将在定义扩展方法的静态类上直接调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="0538a-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0538a-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="0538a-111">See also</span></span>

- [<span data-ttu-id="0538a-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="0538a-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0538a-113">扩展方法</span><span class="sxs-lookup"><span data-stu-id="0538a-113">Extension Methods</span></span>](./extension-methods.md)
