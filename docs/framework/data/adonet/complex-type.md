---
title: Complex Type — 复杂类型
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: ef20de6a9e72d3123d745ef5501ecdb7fa63967d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203782"
---
# <a name="complex-type"></a><span data-ttu-id="27ae3-102">Complex Type — 复杂类型</span><span class="sxs-lookup"><span data-stu-id="27ae3-102">complex type</span></span>

<span data-ttu-id="27ae3-103">" *复杂类型* " 是用于定义 [实体类型](entity-type.md) 或其他复杂类型上的丰富的结构化属性的模板。</span><span class="sxs-lookup"><span data-stu-id="27ae3-103">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="27ae3-104">每个模板都包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="27ae3-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="27ae3-105">唯一名称。</span><span class="sxs-lookup"><span data-stu-id="27ae3-105">A unique name.</span></span> <span data-ttu-id="27ae3-106">（必需）</span><span class="sxs-lookup"><span data-stu-id="27ae3-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="27ae3-107">复杂类型的名称不能与同一命名空间中的实体类型的名称相同。</span><span class="sxs-lookup"><span data-stu-id="27ae3-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="27ae3-108">采用一个或多个 [属性](property.md)格式的数据。</span><span class="sxs-lookup"><span data-stu-id="27ae3-108">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="27ae3-109">（可选。）</span><span class="sxs-lookup"><span data-stu-id="27ae3-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="27ae3-110">复杂类型的属性可以是另一个复杂类型。</span><span class="sxs-lookup"><span data-stu-id="27ae3-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="27ae3-111">复杂类型与实体类型相似，因为复杂类型可以以基元类型属性或其他复杂类型的形式携带数据负载。</span><span class="sxs-lookup"><span data-stu-id="27ae3-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="27ae3-112">但是，在复杂类型与实体类型之间仍存在着一些重要区别：</span><span class="sxs-lookup"><span data-stu-id="27ae3-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="27ae3-113">复杂类型没有标识，因此不能独立存在。</span><span class="sxs-lookup"><span data-stu-id="27ae3-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="27ae3-114">复杂类型只能作为实体类型或其他复杂类型的属性而存在。</span><span class="sxs-lookup"><span data-stu-id="27ae3-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="27ae3-115">复杂类型不能参与 [关联](association-type.md)。</span><span class="sxs-lookup"><span data-stu-id="27ae3-115">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="27ae3-116">关联的两端都不能是复杂类型，因此不能为复杂类型定义 [导航属性](navigation-property.md) 。</span><span class="sxs-lookup"><span data-stu-id="27ae3-116">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27ae3-117">示例</span><span class="sxs-lookup"><span data-stu-id="27ae3-117">Example</span></span>  

 <span data-ttu-id="27ae3-118">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="27ae3-118">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="27ae3-119">下面的 CSDL 定义了一个复杂类型 Address，它具有基元类型属性 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode`。</span><span class="sxs-lookup"><span data-stu-id="27ae3-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="27ae3-120">若要将复杂类型 `Address`（如上所示）定义为某个实体类型的属性，必须在实体类型定义中声明该属性类型。</span><span class="sxs-lookup"><span data-stu-id="27ae3-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="27ae3-121">下面的 CSDL 将 `Address` 属性声明为实体类型 (Publisher) 的复杂类型：</span><span class="sxs-lookup"><span data-stu-id="27ae3-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="27ae3-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="27ae3-122">See also</span></span>

- [<span data-ttu-id="27ae3-123">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="27ae3-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="27ae3-124">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="27ae3-124">Entity Data Model</span></span>](entity-data-model.md)
