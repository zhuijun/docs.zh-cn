---
title: 如何：创建供集合初始化程序使用的 Add 扩展方法
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414564"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="55ec3-102">如何：创建集合初始值设定项所使用的 Add 扩展方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55ec3-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="55ec3-103">使用集合初始值设定项创建集合时，Visual Basic 编译器会搜索集合类型的一个 `Add` 方法，该方法的方法的参数 `Add` 与集合初始值设定项中的值的类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="55ec3-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="55ec3-104">此 `Add` 方法用于在集合中填充集合初始值设定项中的值。</span><span class="sxs-lookup"><span data-stu-id="55ec3-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="55ec3-105">如果不存在匹配的 `Add` 方法，并且无法修改集合的代码，则可以添加一个名为的扩展方法， `Add` 该方法采用集合初始值设定项所需的参数。</span><span class="sxs-lookup"><span data-stu-id="55ec3-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="55ec3-106">这通常是使用泛型集合的集合初始值设定项时需要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="55ec3-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ec3-107">示例</span><span class="sxs-lookup"><span data-stu-id="55ec3-107">Example</span></span>  
 <span data-ttu-id="55ec3-108">下面的示例演示如何将扩展方法添加到泛型类型， <xref:System.Collections.Generic.List%601> 以便可以使用集合初始值设定项来添加类型的对象 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="55ec3-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="55ec3-109">通过扩展方法，可以使用简化的集合初始值设定项语法。</span><span class="sxs-lookup"><span data-stu-id="55ec3-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="55ec3-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55ec3-110">See also</span></span>

- [<span data-ttu-id="55ec3-111">集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="55ec3-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="55ec3-112">如何：创建供集合初始化程序使用的集合</span><span class="sxs-lookup"><span data-stu-id="55ec3-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
