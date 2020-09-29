---
title: 如何测试引用相等性（标识）- C# 编程指南
description: 了解如何测试引用相等性（标识）。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 1d1a0e5d80ac8d2a689e75acbc6099b92e16f23f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151436"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="801eb-104">如何测试引用相等性（标识）（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="801eb-104">How to test for reference equality (Identity) (C# Programming Guide)</span></span>

<span data-ttu-id="801eb-105">无需实现任何自定义逻辑，即可支持类型中的引用相等性比较。</span><span class="sxs-lookup"><span data-stu-id="801eb-105">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="801eb-106">此功能由静态 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法向所有类型提供。</span><span class="sxs-lookup"><span data-stu-id="801eb-106">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="801eb-107">以下示例演示如何确定两个变量是否具有引用相等性，即它们引用内存中的同一对象。</span><span class="sxs-lookup"><span data-stu-id="801eb-107">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="801eb-108">该示例还演示 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 为何始终为值类型返回 `false`，以及您为何不应使用 <xref:System.Object.ReferenceEquals%2A> 来确定字符串相等性。</span><span class="sxs-lookup"><span data-stu-id="801eb-108">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="801eb-109">示例</span><span class="sxs-lookup"><span data-stu-id="801eb-109">Example</span></span>  

 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="801eb-110">在 <xref:System.Object?displayProperty=nameWithType> 通用基类中实现 `Equals` 也会执行引用相等性检查，但最好不要使用这种检查，因为如果恰好某个类替代了此方法，结果可能会出乎意料。</span><span class="sxs-lookup"><span data-stu-id="801eb-110">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="801eb-111">以上情况同样适用于 `==` 和 `!=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="801eb-111">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="801eb-112">当它们作用于引用类型时，`==` 和 `!=` 的默认行为是执行引用相等性检查。</span><span class="sxs-lookup"><span data-stu-id="801eb-112">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="801eb-113">但是，派生类可重载运算符，执行值相等性检查。</span><span class="sxs-lookup"><span data-stu-id="801eb-113">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="801eb-114">为了尽量降低错误的可能性，当需要确定两个对象是否具有引用相等性时，最好始终使用 <xref:System.Object.ReferenceEquals%2A>。</span><span class="sxs-lookup"><span data-stu-id="801eb-114">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="801eb-115">运行时始终暂存同一程序集内的常量字符串。</span><span class="sxs-lookup"><span data-stu-id="801eb-115">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="801eb-116">也就是说，仅维护每个唯一文本字符串的一个实例。</span><span class="sxs-lookup"><span data-stu-id="801eb-116">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="801eb-117">但是，运行时不能保证会暂存在运行时创建的字符串，也不保证会暂存不同程序集中两个相等的常量字符串。</span><span class="sxs-lookup"><span data-stu-id="801eb-117">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="801eb-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="801eb-118">See also</span></span>

- [<span data-ttu-id="801eb-119">相等比较</span><span class="sxs-lookup"><span data-stu-id="801eb-119">Equality Comparisons</span></span>](./equality-comparisons.md)
