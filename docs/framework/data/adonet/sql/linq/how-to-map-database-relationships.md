---
title: 如何：映射数据库关系
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 2f612877f5e7da6442c242aa0d56d811c0aa7cf8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166451"
---
# <a name="how-to-map-database-relationships"></a><span data-ttu-id="049bb-102">如何：映射数据库关系</span><span class="sxs-lookup"><span data-stu-id="049bb-102">How to: Map Database Relationships</span></span>

<span data-ttu-id="049bb-103">可以在您的实体类中将始终相同的任何数据关系编码为属性引用。</span><span class="sxs-lookup"><span data-stu-id="049bb-103">You can encode as property references in your entity class any data relationships that will always be the same.</span></span> <span data-ttu-id="049bb-104">例如，在 Northwind 示例数据库中，由于客户通常会下订单，因此在模型中客户与其订单之间始终存在关系。</span><span class="sxs-lookup"><span data-stu-id="049bb-104">In the Northwind sample database, for example, because customers typically place orders, there is always a relationship in the model between customers and their orders.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="049bb-105">定义了 <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性来帮助表示此类关系。</span><span class="sxs-lookup"><span data-stu-id="049bb-105">defines an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute to help represent such relationships.</span></span> <span data-ttu-id="049bb-106">此属性与 <xref:System.Data.Linq.EntitySet%601> 和 <xref:System.Data.Linq.EntityRef%601> 类型一起使用，来表示将作为数据库中的外键关系的内容。</span><span class="sxs-lookup"><span data-stu-id="049bb-106">This attribute is used together with the <xref:System.Data.Linq.EntitySet%601> and <xref:System.Data.Linq.EntityRef%601> types to represent what would be a foreign key relationship in a database.</span></span> <span data-ttu-id="049bb-107">有关详细信息，请参阅 [基于属性的映射](attribute-based-mapping.md)的关联特性部分。</span><span class="sxs-lookup"><span data-stu-id="049bb-107">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="049bb-108">AssociationAttribute 和 ColumnAttribute Storage 属性值区分大小写。</span><span class="sxs-lookup"><span data-stu-id="049bb-108">AssociationAttribute and ColumnAttribute Storage property values are case sensitive.</span></span> <span data-ttu-id="049bb-109">例如，请确保 AssociationAttribute.Storage 属性 (Property) 的属性 (Attribute) 中使用的值与代码中其他位置使用的相应属性 (Property) 名称值的大小写相匹配。</span><span class="sxs-lookup"><span data-stu-id="049bb-109">For example, ensure that values used in the attribute for the AssociationAttribute.Storage property match the case for the corresponding property names used elsewhere in the code.</span></span> <span data-ttu-id="049bb-110">这适用于所有 .NET 编程语言，甚至不是通常区分大小写的语言，包括 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="049bb-110">This applies to all .NET programming languages, even those which are not typically case sensitive, including Visual Basic.</span></span> <span data-ttu-id="049bb-111">有关 Storage 属性的更多信息，请参见 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="049bb-111">For more information about the Storage property, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="049bb-112">大多数关系都是一对多关系，这一点在本主题后面部分的示例中会有所体现。</span><span class="sxs-lookup"><span data-stu-id="049bb-112">Most relationships are one-to-many, as in the example later in this topic.</span></span> <span data-ttu-id="049bb-113">您还可以按如下方式来表示一对一和多对多关系：</span><span class="sxs-lookup"><span data-stu-id="049bb-113">You can also represent one-to-one and many-to-many relationships as follows:</span></span>  
  
- <span data-ttu-id="049bb-114">一对一：通过向双方添加 <xref:System.Data.Linq.EntitySet%601> 来表示此类关系。</span><span class="sxs-lookup"><span data-stu-id="049bb-114">One-to-one: Represent this kind of relationship by including <xref:System.Data.Linq.EntitySet%601> on both sides.</span></span>  
  
     <span data-ttu-id="049bb-115">例如，请考虑建立 `Customer` - `SecurityCode` 关系，以便在表中找不到客户的安全代码 `Customer` ，只能由授权人员进行访问。</span><span class="sxs-lookup"><span data-stu-id="049bb-115">For example, consider a `Customer`-`SecurityCode` relationship, created so that the customer's security code will not be found in the `Customer` table and can be accessed only by authorized persons.</span></span>  
  
- <span data-ttu-id="049bb-116">多对多：在多对多关系中，链接表的主键 (也称为 *联接* 表) 通常由其他两个表中的外键组合构成。</span><span class="sxs-lookup"><span data-stu-id="049bb-116">Many-to-many: In many-to-many relationships, the primary key of the link table (also named the *junction* table) is often formed by a composite of the foreign keys from the other two tables.</span></span>  
  
     <span data-ttu-id="049bb-117">例如，考虑 `Employee` - `Project` 使用链接表构成的多对多关系 `EmployeeProject` 。</span><span class="sxs-lookup"><span data-stu-id="049bb-117">For example, consider an `Employee`-`Project` many-to-many relationship formed by using link table `EmployeeProject`.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="049bb-118">要求使用以下三个类对这种关系进行建模：`Employee`、`Project` 和 `EmployeeProject`。</span><span class="sxs-lookup"><span data-stu-id="049bb-118">requires that such a relationship be modeled by using three classes: `Employee`, `Project`, and `EmployeeProject`.</span></span> <span data-ttu-id="049bb-119">在这种情况下，更改 `Employee` 和 `Project` 之间的关系似乎需要更新主键 `EmployeeProject`。</span><span class="sxs-lookup"><span data-stu-id="049bb-119">In this case, changing the relationship between an `Employee` and a `Project` can appear to require an update of the primary key `EmployeeProject`.</span></span> <span data-ttu-id="049bb-120">但是，这种情况最好的模型化处理方法是删除现有 `EmployeeProject`，然后创建新的 `EmployeeProject`。</span><span class="sxs-lookup"><span data-stu-id="049bb-120">However, this situation is best modeled as deleting an existing `EmployeeProject` and the creating a new `EmployeeProject`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="049bb-121">关系数据库中的关系通常模型化成引用其他表中主键的外键值。</span><span class="sxs-lookup"><span data-stu-id="049bb-121">Relationships in relational databases are typically modeled as foreign key values that refer to primary keys in other tables.</span></span> <span data-ttu-id="049bb-122">若要在它们之间导航，请使用关系 *联接* 操作显式关联两个表。</span><span class="sxs-lookup"><span data-stu-id="049bb-122">To navigate between them you explicitly associate the two tables by using a relational *join* operation.</span></span>  
    >
    >  <span data-ttu-id="049bb-123">另一方面，中的对象 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 通过使用属性引用或使用 *点* 表示法导航的引用集合来彼此引用。</span><span class="sxs-lookup"><span data-stu-id="049bb-123">Objects in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], on the other hand, refer to each other by using property references or collections of references that you navigate by using *dot* notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="049bb-124">示例</span><span class="sxs-lookup"><span data-stu-id="049bb-124">Example</span></span>  

 <span data-ttu-id="049bb-125">在下面的一对多示例中，`Customer` 类具有一个声明客户与其订单之间的关系的属性。</span><span class="sxs-lookup"><span data-stu-id="049bb-125">In the following one-to-many example, the `Customer` class has a property that declares the relationship between customers and their orders.</span></span>  <span data-ttu-id="049bb-126">`Orders` 属性为 <xref:System.Data.Linq.EntitySet%601> 类型。</span><span class="sxs-lookup"><span data-stu-id="049bb-126">The `Orders` property is of type <xref:System.Data.Linq.EntitySet%601>.</span></span> <span data-ttu-id="049bb-127">此类型表明这种关系是一对多的（一个客户对多个订单）。</span><span class="sxs-lookup"><span data-stu-id="049bb-127">This type signifies that this relationship is one-to-many (one customer to many orders).</span></span> <span data-ttu-id="049bb-128"><xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> 属性用来说明如何实现这种关联，即通过指定相关类中要与此属性比较的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="049bb-128">The <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> property is used to describe how this association is accomplished, namely, by specifying the name of the property in the related class to be compared with this one.</span></span> <span data-ttu-id="049bb-129">在此示例中，将 `CustomerID` 比较属性，就像数据库 *联接* 会比较该列的值一样。</span><span class="sxs-lookup"><span data-stu-id="049bb-129">In this example, the `CustomerID` property is compared, just as a database *join* would compare that column value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="049bb-130">如果使用的是 Visual Studio，则可以使用对象关系设计器来创建类之间的关联。</span><span class="sxs-lookup"><span data-stu-id="049bb-130">If you are using Visual Studio, you can use the Object Relational Designer to create an association between classes.</span></span>  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="049bb-131">示例</span><span class="sxs-lookup"><span data-stu-id="049bb-131">Example</span></span>  

 <span data-ttu-id="049bb-132">这种情况也可以反过来处理。</span><span class="sxs-lookup"><span data-stu-id="049bb-132">You can also reverse the situation.</span></span> <span data-ttu-id="049bb-133">您可以不使用 `Customer` 类来说明客户与订单之间的关联，而改用 `Order` 类。</span><span class="sxs-lookup"><span data-stu-id="049bb-133">Instead of using the `Customer` class to describe the association between customers and orders, you can use the `Order` class.</span></span> <span data-ttu-id="049bb-134">`Order` 类使用 <xref:System.Data.Linq.EntityRef%601> 类型反向说明与客户的关系，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="049bb-134">The `Order` class uses the <xref:System.Data.Linq.EntityRef%601> type to describe the relationship back to the customer, as in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="049bb-135"><xref:System.Data.Linq.EntityRef%601>类支持*延迟加载*。</span><span class="sxs-lookup"><span data-stu-id="049bb-135">The <xref:System.Data.Linq.EntityRef%601> class supports *deferred loading*.</span></span> <span data-ttu-id="049bb-136">有关详细信息，*请参阅*[延迟与立即加载](deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="049bb-136">For more information, *see* [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="049bb-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="049bb-137">See also</span></span>

- [<span data-ttu-id="049bb-138">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="049bb-138">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="049bb-139">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="049bb-139">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
