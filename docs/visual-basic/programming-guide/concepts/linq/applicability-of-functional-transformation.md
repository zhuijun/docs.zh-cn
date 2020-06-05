---
title: 功能转换的适用性
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: db24871e3763c5acc79cf21b4afb90a93ed8bd53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383697"
---
# <a name="applicability-of-functional-transformation-visual-basic"></a><span data-ttu-id="d77b4-102">功能转换的适用性（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d77b4-102">Applicability of Functional Transformation (Visual Basic)</span></span>
<span data-ttu-id="d77b4-103">纯函数转换适用于多种情况。</span><span class="sxs-lookup"><span data-stu-id="d77b4-103">Pure functional transformations are applicable in a wide variety of situations.</span></span>  
  
 <span data-ttu-id="d77b4-104">函数转换方法最适合查询和操作结构化数据，因此它非常适合 LINQ 技术。</span><span class="sxs-lookup"><span data-stu-id="d77b4-104">The functional transformation approach is ideally suited for querying and manipulating structured data; therefore it fits well with LINQ technologies.</span></span> <span data-ttu-id="d77b4-105">但函数转换比使用 LINQ 具有更广泛的适用性。</span><span class="sxs-lookup"><span data-stu-id="d77b4-105">However, functional transformation has a much wider applicability than use with LINQ.</span></span> <span data-ttu-id="d77b4-106">任何侧重于将数据从一种形式转换为另一种形式的进程都可以考虑作为函数转换的候选项。</span><span class="sxs-lookup"><span data-stu-id="d77b4-106">Any process where the main focus is on transforming data from one form to another should probably be considered as a candidate for functional transformation.</span></span>  
  
 <span data-ttu-id="d77b4-107">此方法适用于乍看可能不是候选项的许多问题。</span><span class="sxs-lookup"><span data-stu-id="d77b4-107">This approach is applicable to many problems that might not appear at first glance to be a candidate.</span></span> <span data-ttu-id="d77b4-108">在独立或与 LINQ 一起使用时，应考虑对以下方面使用函数转换：</span><span class="sxs-lookup"><span data-stu-id="d77b4-108">Used in conjunction with or separately from LINQ, functional transformation should be considered for the following areas:</span></span>  
  
- <span data-ttu-id="d77b4-109">基于 XML 的文档。</span><span class="sxs-lookup"><span data-stu-id="d77b4-109">XML-based documents.</span></span> <span data-ttu-id="d77b4-110">使用任何 XML 方言的格式良好的数据均可以通过函数转换容易地操作。</span><span class="sxs-lookup"><span data-stu-id="d77b4-110">Well-formed data of any XML dialect can be easily manipulated through functional transformation.</span></span> <span data-ttu-id="d77b4-111">有关详细信息，请参阅[XML 的功能转换（Visual Basic）](functional-transformation-of-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="d77b4-111">For more information, see [Functional Transformation of XML (Visual Basic)](functional-transformation-of-xml.md).</span></span>  
  
- <span data-ttu-id="d77b4-112">其他结构化文件格式。</span><span class="sxs-lookup"><span data-stu-id="d77b4-112">Other structured file formats.</span></span> <span data-ttu-id="d77b4-113">从 Windows.ini 文件到纯文本文档，多数文件都有适于本身进行分析和转换的结构。</span><span class="sxs-lookup"><span data-stu-id="d77b4-113">From Windows.ini files to plain text documents, most files have some structure that lends itself to analysis and transformation.</span></span>  
  
- <span data-ttu-id="d77b4-114">数据流协议。</span><span class="sxs-lookup"><span data-stu-id="d77b4-114">Data streaming protocols.</span></span> <span data-ttu-id="d77b4-115">将数据编码为通信协议和从通信协议解码数据通常可以由简单的函数转换来表示。</span><span class="sxs-lookup"><span data-stu-id="d77b4-115">Encoding data into and decoding data from communication protocols can often be represented by a simple functional transform.</span></span>  
  
- <span data-ttu-id="d77b4-116">RDBMS 和 OODBMS 数据。</span><span class="sxs-lookup"><span data-stu-id="d77b4-116">RDBMS and OODBMS data.</span></span> <span data-ttu-id="d77b4-117">关系数据库和面向对象的数据库和 XML 一样，是广泛使用的结构化数据源。</span><span class="sxs-lookup"><span data-stu-id="d77b4-117">Relational and object-oriented databases, just like XML, are widely-used structured data sources.</span></span>  
  
- <span data-ttu-id="d77b4-118">数学、统计和科学解决方案。</span><span class="sxs-lookup"><span data-stu-id="d77b4-118">Mathematic, statistic, and science solutions.</span></span> <span data-ttu-id="d77b4-119">这些字段适用于操作大型数据集，以帮助用户处理可视化、评估或实际解决重要问题。</span><span class="sxs-lookup"><span data-stu-id="d77b4-119">These fields tend to manipulate large data sets to assist the user in visualizing, estimating, or actually solving non-trivial problems.</span></span>  
  
 <span data-ttu-id="d77b4-120">如[重构为纯函数（Visual Basic）](refactoring-into-pure-functions.md)中所述，使用纯函数是函数编程的一个示例。</span><span class="sxs-lookup"><span data-stu-id="d77b4-120">As described in [Refactoring Into Pure Functions (Visual Basic)](refactoring-into-pure-functions.md), using pure functions is an example of functional programming.</span></span> <span data-ttu-id="d77b4-121">除了直接好处外，使用纯函数还可对从函数转换角度考虑问题提供宝贵的经验。</span><span class="sxs-lookup"><span data-stu-id="d77b4-121">In additional to their immediate benefits, using pure functions provides valuable experience in thinking about problems from a functional transformation perspective.</span></span> <span data-ttu-id="d77b4-122">这种方法也可能对程序和类设计产生重要影响。</span><span class="sxs-lookup"><span data-stu-id="d77b4-122">This approach can also have major impact on program and class design.</span></span> <span data-ttu-id="d77b4-123">当问题本身适于数据转换解决方案（如上所述）时更是如此。</span><span class="sxs-lookup"><span data-stu-id="d77b4-123">This is especially true when a problem lends itself to a data transformation solution as described above.</span></span>  
  
 <span data-ttu-id="d77b4-124">虽然受函数转换透视影响的设计不在本教程的范围内，但在以进程为中心作为操作者和以对象为中心作为操作者之间，他们更倾向于前者，生成的解决方案倾向于以一系列大规模转换而不是单独的对象状态更改的形式实现。</span><span class="sxs-lookup"><span data-stu-id="d77b4-124">Although they are beyond the scope of this tutorial, designs that are influenced by the functional transformation perspective tend to center on processes more than on objects as actors, and the resulting solution tends to be implemented as series of large-scale transformations, rather than individual object state changes.</span></span>  
  
 <span data-ttu-id="d77b4-125">同样，请记住 Visual Basic 同时支持命令性方法和函数方法，因此应用程序的最佳设计可能合并了这两个方法中的元素。</span><span class="sxs-lookup"><span data-stu-id="d77b4-125">Again, remember that Visual Basic supports both imperative and functional approaches, so the best design for your application might incorporate elements of both.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77b4-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d77b4-126">See also</span></span>

- [<span data-ttu-id="d77b4-127">纯功能转换简介（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d77b4-127">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="d77b4-128">XML 的功能转换 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d77b4-128">Functional Transformation of XML (Visual Basic)</span></span>](functional-transformation-of-xml.md)
- [<span data-ttu-id="d77b4-129">重构为纯函数（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d77b4-129">Refactoring Into Pure Functions (Visual Basic)</span></span>](refactoring-into-pure-functions.md)
