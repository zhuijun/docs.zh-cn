---
title: “<typename>”是委托类型
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4cc0a1221dcf65aa2a16fd7d82568c8544f27fdb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875087"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="5353b-102">“\<typename>”是委托类型</span><span class="sxs-lookup"><span data-stu-id="5353b-102">'\<typename>' is a delegate type</span></span>

<span data-ttu-id="5353b-103">" \<typename> " 是委托类型。</span><span class="sxs-lookup"><span data-stu-id="5353b-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="5353b-104">委托构造仅允许将单个 AddressOf 表达式作为参数列表。</span><span class="sxs-lookup"><span data-stu-id="5353b-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="5353b-105">通常可以使用 AddressOf 表达式，而不是委托构造。</span><span class="sxs-lookup"><span data-stu-id="5353b-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="5353b-106">`New`创建委托类的实例的子句为委托构造函数提供了无效的参数列表。</span><span class="sxs-lookup"><span data-stu-id="5353b-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="5353b-107">`AddressOf`创建新的委托实例时，只能提供单个表达式。</span><span class="sxs-lookup"><span data-stu-id="5353b-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="5353b-108">如果传递多个参数，或者传递的单个自变量不是有效的表达式，则可能会导致此错误的原因 `AddressOf` 。</span><span class="sxs-lookup"><span data-stu-id="5353b-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="5353b-109">**错误 ID：** BC32008</span><span class="sxs-lookup"><span data-stu-id="5353b-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5353b-110">更正此错误</span><span class="sxs-lookup"><span data-stu-id="5353b-110">To correct this error</span></span>  
  
- <span data-ttu-id="5353b-111">使用子句中的 `AddressOf` 委托类的参数列表中的单个表达式 `New` 。</span><span class="sxs-lookup"><span data-stu-id="5353b-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5353b-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5353b-112">See also</span></span>

- [<span data-ttu-id="5353b-113">New 运算符</span><span class="sxs-lookup"><span data-stu-id="5353b-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="5353b-114">AddressOf 运算符</span><span class="sxs-lookup"><span data-stu-id="5353b-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="5353b-115">委托</span><span class="sxs-lookup"><span data-stu-id="5353b-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="5353b-116">如何：调用委托方法</span><span class="sxs-lookup"><span data-stu-id="5353b-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
