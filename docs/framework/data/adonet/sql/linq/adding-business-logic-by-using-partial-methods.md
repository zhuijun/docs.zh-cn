---
title: 通过使用分部方法添加业务逻辑
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 9ad3329c621b8bf8eaa0fd5f986ac7e8cff97d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156155"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="5c0d0-102">通过使用分部方法添加业务逻辑</span><span class="sxs-lookup"><span data-stu-id="5c0d0-102">Adding Business Logic By Using Partial Methods</span></span>

<span data-ttu-id="5c0d0-103">您可以 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 通过使用 *分部方法*自定义项目中的 Visual Basic 和 c # 生成的代码。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="5c0d0-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 生成的代码定义签名作为分部方法的一部分。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="5c0d0-105">如果您要实现此方法，您可以添加自己的分部方法。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="5c0d0-106">如果您不添加自己的实现，编译器将丢弃分部方法签名并调用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的默认方法。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c0d0-107">如果使用的是 Visual Studio，则可以使用对象关系设计器向实体类添加验证及其他自定义项。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="5c0d0-108">例如，Northwind 示例数据库中 `Customer` 类的默认映射包括下面的分部方法：</span><span class="sxs-lookup"><span data-stu-id="5c0d0-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="5c0d0-109">您可以向自己的分部 `Customer` 类添加诸如以下内容的代码来实现自己的方法。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="5c0d0-110">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中通常使用这种方式来重写 `Insert`、`Update`、`Delete` 的默认方法以及在对象生命周期事件过程中验证属性。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="5c0d0-111">有关详细信息，请参阅 [分部方法](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) 或 [部分 (方法) ](../../../../../csharp/language-reference/keywords/partial-method.md) (c #)  (c # 引用 ) 。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-111">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c0d0-112">示例</span><span class="sxs-lookup"><span data-stu-id="5c0d0-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5c0d0-113">描述</span><span class="sxs-lookup"><span data-stu-id="5c0d0-113">Description</span></span>  

 <span data-ttu-id="5c0d0-114">下面的示例首先显示了 `ExampleClass`，因为它可能是由像 SQLMetal 这样的代码生成工具定义的；然后，此示例演示了如何只实现两个方法之一。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5c0d0-115">代码</span><span class="sxs-lookup"><span data-stu-id="5c0d0-115">Code</span></span>  

 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="5c0d0-116">示例</span><span class="sxs-lookup"><span data-stu-id="5c0d0-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5c0d0-117">描述</span><span class="sxs-lookup"><span data-stu-id="5c0d0-117">Description</span></span>  

 <span data-ttu-id="5c0d0-118">下面的示例用到了 `Shipper` 和 `Order` 实体之间的关系。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="5c0d0-119">请注意这些方法中的分部方法 `InsertShipper` 和 `DeleteShipper`。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="5c0d0-120">这些方法重写了由 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 映射提供的默认分部方法。</span><span class="sxs-lookup"><span data-stu-id="5c0d0-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5c0d0-121">代码</span><span class="sxs-lookup"><span data-stu-id="5c0d0-121">Code</span></span>  

 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5c0d0-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="5c0d0-122">See also</span></span>

- [<span data-ttu-id="5c0d0-123">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="5c0d0-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="5c0d0-124">自定义插入、更新和删除操作</span><span class="sxs-lookup"><span data-stu-id="5c0d0-124">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
