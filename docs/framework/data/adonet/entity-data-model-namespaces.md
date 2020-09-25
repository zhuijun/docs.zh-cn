---
title: 实体数据模型：命名空间
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 1e5f9527ec208c5650c68fe35bb758e0850b7700
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194825"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="491f3-102">实体数据模型：命名空间</span><span class="sxs-lookup"><span data-stu-id="491f3-102">Entity Data Model: Namespaces</span></span>

<span data-ttu-id="491f3-103">实体数据模型 (EDM) 中的命名空间是用于 [实体类型](entity-type.md)、 [复杂类型](complex-type.md)和 [关联](association-type.md)的抽象容器。</span><span class="sxs-lookup"><span data-stu-id="491f3-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="491f3-104">EDM 中的命名空间类似于编程语言中的命名空间：它们为自己所包含的对象提供了上下文，并为消除具有相同名称（但包含在不同的命名空间中）的对象的歧义提供了一种方式。</span><span class="sxs-lookup"><span data-stu-id="491f3-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="491f3-105">示例</span><span class="sxs-lookup"><span data-stu-id="491f3-105">Example</span></span>  

 <span data-ttu-id="491f3-106">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="491f3-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="491f3-107">下面的 CSDL 代码使用命名空间来标识一个在不同概念模型中定义的类型。</span><span class="sxs-lookup"><span data-stu-id="491f3-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="491f3-108">该示例定义了一个实体类型 (`Publisher`)，它有一个从 `Address` 命名空间导入的复杂类型属性 (`ExtendedBooksModel`)。</span><span class="sxs-lookup"><span data-stu-id="491f3-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="491f3-109">请注意，`Using` 元素表明导入了一个命名空间。</span><span class="sxs-lookup"><span data-stu-id="491f3-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="491f3-110">还要注意的是，`Address` 属性的类型是使用其完全限定名称 (`ExtendedBooksModel.Address`) 定义的，表明该类型是在 `ExtendedBooksModel` 命名空间中定义的。</span><span class="sxs-lookup"><span data-stu-id="491f3-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="491f3-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="491f3-111">See also</span></span>

- [<span data-ttu-id="491f3-112">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="491f3-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="491f3-113">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="491f3-113">Entity Data Model</span></span>](entity-data-model.md)
