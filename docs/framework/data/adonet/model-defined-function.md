---
title: 模型定义函数
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 04d27387c30d5fe09d31c1b2cc94741f21ffe8e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150773"
---
# <a name="model-defined-function"></a><span data-ttu-id="4d956-102">模型定义函数</span><span class="sxs-lookup"><span data-stu-id="4d956-102">model-defined function</span></span>

<span data-ttu-id="4d956-103">*模型定义的函数*是在概念模型中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="4d956-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="4d956-104">模型定义函数的主体以 [实体 SQL](./ef/language-reference/entity-sql-language.md)表示，这允许独立于数据源中支持的规则或语言来表示函数。</span><span class="sxs-lookup"><span data-stu-id="4d956-104">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="4d956-105">模型定义函数的定义包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="4d956-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="4d956-106">函数名称。</span><span class="sxs-lookup"><span data-stu-id="4d956-106">A function name.</span></span> <span data-ttu-id="4d956-107">（必需）</span><span class="sxs-lookup"><span data-stu-id="4d956-107">(Required)</span></span>  
  
- <span data-ttu-id="4d956-108">返回值的类型。</span><span class="sxs-lookup"><span data-stu-id="4d956-108">The type of the return value.</span></span> <span data-ttu-id="4d956-109">(可选)</span><span class="sxs-lookup"><span data-stu-id="4d956-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4d956-110">如果未指定返回类型，则返回值为 void。</span><span class="sxs-lookup"><span data-stu-id="4d956-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="4d956-111">参数信息。</span><span class="sxs-lookup"><span data-stu-id="4d956-111">Parameter information.</span></span> <span data-ttu-id="4d956-112">(可选)</span><span class="sxs-lookup"><span data-stu-id="4d956-112">(Optional)</span></span>  
  
- <span data-ttu-id="4d956-113">定义函数主体的 [实体 SQL](./ef/language-reference/entity-sql-language.md) 表达式。</span><span class="sxs-lookup"><span data-stu-id="4d956-113">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="4d956-114">请注意，模型定义函数不支持输出参数。</span><span class="sxs-lookup"><span data-stu-id="4d956-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="4d956-115">这一限制可以保证无法对模型定义函数进行编写。</span><span class="sxs-lookup"><span data-stu-id="4d956-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d956-116">示例</span><span class="sxs-lookup"><span data-stu-id="4d956-116">Example</span></span>  

 <span data-ttu-id="4d956-117">下图显示了一个具有三个实体类型的概念模型：`Book`、`Publisher` 和 `Author`。</span><span class="sxs-lookup"><span data-stu-id="4d956-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![显示具有发布日期的模型的屏幕截图。](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="4d956-119">[ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="4d956-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="4d956-120">下面的 CSDL 在概念模型中定义了一个函数，它返回自某个 `Book` 实例（如上图所示）出版以来的年数。</span><span class="sxs-lookup"><span data-stu-id="4d956-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="4d956-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="4d956-121">See also</span></span>

- [<span data-ttu-id="4d956-122">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="4d956-122">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="4d956-123">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="4d956-123">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="4d956-124">实体数据模型：基元数据类型</span><span class="sxs-lookup"><span data-stu-id="4d956-124">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
