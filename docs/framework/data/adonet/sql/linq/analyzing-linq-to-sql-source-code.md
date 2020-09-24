---
title: 分析 LINQ to SQL 源代码
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: e39b1686269442044beb73bb7e572738832bec27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164579"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="c21c4-102">分析 LINQ to SQL 源代码</span><span class="sxs-lookup"><span data-stu-id="c21c4-102">Analyzing LINQ to SQL Source Code</span></span>

<span data-ttu-id="c21c4-103">通过按以下步骤操作，你可以用 Northwind 示例数据库生成 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 源代码。</span><span class="sxs-lookup"><span data-stu-id="c21c4-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="c21c4-104">您可以将对象模型的元素与数据库的元素作一个比较，以便更好地了解不同项的映射方式。</span><span class="sxs-lookup"><span data-stu-id="c21c4-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c21c4-105">使用 Visual Studio 的开发人员可以使用 O/R 设计器来生成此代码。</span><span class="sxs-lookup"><span data-stu-id="c21c4-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="c21c4-106">如果您的开发计算机上还没有 Northwind 示例数据库，您可以免费下载它。</span><span class="sxs-lookup"><span data-stu-id="c21c4-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="c21c4-107">有关详细信息，请参阅 [下载示例数据库](downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="c21c4-107">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="c21c4-108">使用 SqlMetal 命令行工具生成 Visual Basic 或 C# 源文件。</span><span class="sxs-lookup"><span data-stu-id="c21c4-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="c21c4-109">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="c21c4-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="c21c4-110">通过在命令提示符处键入以下命令，您可以生成包含存储过程和函数的 Visual Basic 和 C# 源文件。</span><span class="sxs-lookup"><span data-stu-id="c21c4-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="c21c4-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c21c4-111">See also</span></span>

- [<span data-ttu-id="c21c4-112">引用</span><span class="sxs-lookup"><span data-stu-id="c21c4-112">Reference</span></span>](reference.md)
- [<span data-ttu-id="c21c4-113">背景信息</span><span class="sxs-lookup"><span data-stu-id="c21c4-113">Background Information</span></span>](background-information.md)
