---
title: 如何：在 Visual Basic 或 C# 中生成对象模型
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: e2491cf18be556cb26f084a178b7bf09448c6904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546609"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="327e2-102">如何：在 Visual Basic 或 C 中生成对象模型\#</span><span class="sxs-lookup"><span data-stu-id="327e2-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="327e2-103">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，采用您自己的编程语言的对象模型映射到关系数据库。</span><span class="sxs-lookup"><span data-stu-id="327e2-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="327e2-104">有两个工具可用于根据现有数据库的元数据自动生成 Visual Basic 或 c # 模型。</span><span class="sxs-lookup"><span data-stu-id="327e2-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="327e2-105">如果使用的是 Visual Studio，则可以使用对象关系设计器来生成对象模型。</span><span class="sxs-lookup"><span data-stu-id="327e2-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="327e2-106">O/R 设计器提供丰富的用户界面来帮助您生成 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 对象模型。</span><span class="sxs-lookup"><span data-stu-id="327e2-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="327e2-107">有关详细信息，请参阅 [Visual Studio 中的 Linq TO SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。</span><span class="sxs-lookup"><span data-stu-id="327e2-107">For more information see, [Linq to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="327e2-108">SQLMetal 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="327e2-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="327e2-109">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="327e2-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="327e2-110">如果您没有现有数据库且希望利用对象模型创建一个，则可以使用代码编辑器和 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 来创建对象模型。</span><span class="sxs-lookup"><span data-stu-id="327e2-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="327e2-111">有关详细信息，请参阅 [如何：动态创建数据库](how-to-dynamically-create-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="327e2-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="327e2-112">O/R 设计器的文档提供了有关如何使用 O/R 设计器生成 Visual Basic 或 c # 对象模型的示例。</span><span class="sxs-lookup"><span data-stu-id="327e2-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="327e2-113">以下信息提供了有关如何使用 SQLMetal 命令行工具的示例。</span><span class="sxs-lookup"><span data-stu-id="327e2-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="327e2-114">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="327e2-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="327e2-115">示例</span><span class="sxs-lookup"><span data-stu-id="327e2-115">Example</span></span>  
 <span data-ttu-id="327e2-116">下面的示例中所示的 SQLMetal 命令行产生 Visual Basic 代码，作为 Northwind 示例数据库的基于属性的对象模型。</span><span class="sxs-lookup"><span data-stu-id="327e2-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="327e2-117">还呈现了存储过程和函数。</span><span class="sxs-lookup"><span data-stu-id="327e2-117">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="327e2-118">示例</span><span class="sxs-lookup"><span data-stu-id="327e2-118">Example</span></span>  
 <span data-ttu-id="327e2-119">下面的示例中显示的 SQLMetal 命令行会生成 C# 代码作为 Northwind 示例数据库的基于属性的对象模型。</span><span class="sxs-lookup"><span data-stu-id="327e2-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="327e2-120">还呈现了存储过程和函数，并自动将表名变为复数形式。</span><span class="sxs-lookup"><span data-stu-id="327e2-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="327e2-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="327e2-121">See also</span></span>

- [<span data-ttu-id="327e2-122">编程指南</span><span class="sxs-lookup"><span data-stu-id="327e2-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="327e2-123">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="327e2-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="327e2-124">通过演练学习</span><span class="sxs-lookup"><span data-stu-id="327e2-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="327e2-125">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="327e2-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="327e2-126">基于特性的映射</span><span class="sxs-lookup"><span data-stu-id="327e2-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="327e2-127">SqlMetal.exe（代码生成工具）</span><span class="sxs-lookup"><span data-stu-id="327e2-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="327e2-128">外部映射</span><span class="sxs-lookup"><span data-stu-id="327e2-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="327e2-129">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="327e2-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="327e2-130">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="327e2-130">Creating the Object Model</span></span>](creating-the-object-model.md)
