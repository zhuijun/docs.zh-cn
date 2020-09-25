---
title: 构造类型 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 82c8e3f2bac0d13da4870e90878e0de6fc9ec063
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177516"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="8928e-102">构造类型 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8928e-102">Constructing Types (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8928e-103">提供了三种构造函数：行构造函数、命名类型构造函数和集合构造函数。</span><span class="sxs-lookup"><span data-stu-id="8928e-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="8928e-104">行构造函数</span><span class="sxs-lookup"><span data-stu-id="8928e-104">Row Constructors</span></span>  

 <span data-ttu-id="8928e-105">使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的行构造函数可以从一个或多个值构造结构上类型化的匿名记录。</span><span class="sxs-lookup"><span data-stu-id="8928e-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="8928e-106">行构造函数的结果类型为行类型，其字段类型对应于用于构造该行的值的类型。</span><span class="sxs-lookup"><span data-stu-id="8928e-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="8928e-107">例如，下面的表达式构造一个类型为的值 `Record(a int, b string, c int)` ：</span><span class="sxs-lookup"><span data-stu-id="8928e-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="8928e-108">如果没有为行构造函数中的表达式提供别名，则实体框架会尝试生成一个别名。</span><span class="sxs-lookup"><span data-stu-id="8928e-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="8928e-109">有关详细信息，请参阅 [标识符](identifiers-entity-sql.md)中的 "别名规则" 一节。</span><span class="sxs-lookup"><span data-stu-id="8928e-109">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="8928e-110">以下规则适用于在行构造函数中指定表达式别名：</span><span class="sxs-lookup"><span data-stu-id="8928e-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="8928e-111">行构造函数中的表达式不能引用同一构造函数中的其他别名。</span><span class="sxs-lookup"><span data-stu-id="8928e-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="8928e-112">同一行构造函数中的两个表达式不能具有相同别名。</span><span class="sxs-lookup"><span data-stu-id="8928e-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="8928e-113">有关行构造函数的详细信息，请参阅 [row](row-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8928e-113">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="8928e-114">集合构造函数</span><span class="sxs-lookup"><span data-stu-id="8928e-114">Collection Constructors</span></span>  

 <span data-ttu-id="8928e-115">使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的集合构造函数可以从值列表创建多重集实例。</span><span class="sxs-lookup"><span data-stu-id="8928e-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="8928e-116">该构造函数中的所有值都必须为互兼容的 `T` 类型，并且该构造函数生成 `Multiset<T>` 类型的集合。</span><span class="sxs-lookup"><span data-stu-id="8928e-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="8928e-117">例如，下面的表达式创建整数集合：</span><span class="sxs-lookup"><span data-stu-id="8928e-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="8928e-118">因为无法确定元素类型，所以不能使用空的多重集构造函数。</span><span class="sxs-lookup"><span data-stu-id="8928e-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="8928e-119">下面的表达式无效：</span><span class="sxs-lookup"><span data-stu-id="8928e-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="8928e-120">有关详细信息，请参阅 [多重集](multiset-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8928e-120">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="8928e-121">命名类型构造函数（NamedType 初始值设定项）</span><span class="sxs-lookup"><span data-stu-id="8928e-121">Named Type Constructors (NamedType Initializers)</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8928e-122">允许类型构造函数（初始值设定项）创建命名复杂类型和命名实体类型的实例。</span><span class="sxs-lookup"><span data-stu-id="8928e-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="8928e-123">例如，下面的表达式创建 `Person` 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="8928e-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="8928e-124">下面的表达式创建复杂类型的实例。</span><span class="sxs-lookup"><span data-stu-id="8928e-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="8928e-125">下面的表达式创建嵌套复杂类型的实例。</span><span class="sxs-lookup"><span data-stu-id="8928e-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="8928e-126">下面的表达式创建具有嵌套复杂类型的实体的实例。</span><span class="sxs-lookup"><span data-stu-id="8928e-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="8928e-127">下面的示例演示如何将复杂类型的属性初始化为 null。</span><span class="sxs-lookup"><span data-stu-id="8928e-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="8928e-128">假定该构造函数的参数的顺序与该类型的属性的声明顺序相同。</span><span class="sxs-lookup"><span data-stu-id="8928e-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="8928e-129">有关详细信息，请参阅 [命名类型构造函数](named-type-constructor-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8928e-129">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8928e-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="8928e-130">See also</span></span>

- [<span data-ttu-id="8928e-131">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="8928e-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8928e-132">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="8928e-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="8928e-133">类型系统</span><span class="sxs-lookup"><span data-stu-id="8928e-133">Type System</span></span>](type-system-entity-sql.md)
