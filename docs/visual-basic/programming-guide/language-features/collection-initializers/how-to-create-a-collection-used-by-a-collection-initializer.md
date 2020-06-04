---
title: 如何：创建供集合初始化程序使用的集合
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 7cba290b92f41125a93d1ed022e4db5ef62da789
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414551"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="05e40-102">如何：创建集合初始值设定项所使用的集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05e40-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="05e40-103">使用集合初始值设定项创建集合时，Visual Basic 编译器会搜索集合类型的一个 `Add` 方法，该方法的方法的参数 `Add` 与集合初始值设定项中的值的类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="05e40-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="05e40-104">此 `Add` 方法用于在集合中填充集合初始值设定项中的值。</span><span class="sxs-lookup"><span data-stu-id="05e40-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05e40-105">示例</span><span class="sxs-lookup"><span data-stu-id="05e40-105">Example</span></span>  
 <span data-ttu-id="05e40-106">下面的示例演示一个 `OrderCollection` 集合，该集合包含一个公共 `Add` 方法，集合初始值设定项可以使用该方法来添加类型的对象 `Order` 。</span><span class="sxs-lookup"><span data-stu-id="05e40-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="05e40-107">`Add`方法使您可以使用简化的集合初始值设定项语法。</span><span class="sxs-lookup"><span data-stu-id="05e40-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="05e40-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05e40-108">See also</span></span>

- [<span data-ttu-id="05e40-109">集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="05e40-109">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="05e40-110">如何：创建供集合初始化程序使用的 Add 扩展方法</span><span class="sxs-lookup"><span data-stu-id="05e40-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
