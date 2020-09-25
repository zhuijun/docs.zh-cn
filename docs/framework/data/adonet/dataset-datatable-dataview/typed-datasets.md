---
title: 类型化数据集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 4648d49b1d7419d61a3a000404f42e0d02d25786
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198439"
---
# <a name="typed-datasets"></a><span data-ttu-id="8c1b0-102">类型化数据集</span><span class="sxs-lookup"><span data-stu-id="8c1b0-102">Typed DataSets</span></span>

<span data-ttu-id="8c1b0-103">在允许通过弱类型化变量对值进行后期绑定访问的同时，<xref:System.Data.DataSet> 还允许通过强类型化比喻对数据进行访问。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="8c1b0-104">可以使用用户友好名称和强类型化变量来访问作为 **数据集** 一部分的表和列。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="8c1b0-105">类型化 **数据集** 是从 **数据集**派生的类。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="8c1b0-106">因此，它继承了 **数据集**的所有方法、事件和属性。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="8c1b0-107">此外，类型化 **数据集** 提供强类型化的方法、事件和属性。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="8c1b0-108">这意味着可以按名称（而不是使用基于集合的方法）访问表和列。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="8c1b0-109">除了提高代码的可读性之外，类型化 **数据集** 还允许 Visual Studio .net 代码编辑器在你键入时自动完成行。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="8c1b0-110">此外，强类型化 **数据集** 还可在编译时访问值作为正确的类型。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="8c1b0-111">使用强类型化 **数据集**时，将在编译代码时（而不是在运行时）捕获类型不匹配错误。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c1b0-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="8c1b0-112">In This Section</span></span>  

 [<span data-ttu-id="8c1b0-113">生成强类型化数据集</span><span class="sxs-lookup"><span data-stu-id="8c1b0-113">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="8c1b0-114">介绍如何创建和使用强类型化 **数据集**。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="8c1b0-115">为类型化的数据集进行批注</span><span class="sxs-lookup"><span data-stu-id="8c1b0-115">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="8c1b0-116">介绍如何批注用于生成强类型化 **数据集** (XSD) 架构的 XML 架构定义语言，以便在不更改基础架构的情况下为 **DataSet** 元素指定友好名称。</span><span class="sxs-lookup"><span data-stu-id="8c1b0-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1b0-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="8c1b0-117">See also</span></span>

- [<span data-ttu-id="8c1b0-118">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="8c1b0-118">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8c1b0-119">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="8c1b0-119">ADO.NET Overview</span></span>](../ado-net-overview.md)
