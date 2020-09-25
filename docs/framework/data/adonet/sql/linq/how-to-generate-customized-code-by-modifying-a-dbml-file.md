---
title: 如何：通过修改 DBML 文件生成自定义代码
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: ab49f76a0d5e7338a93e21ae9a8d1d9d74a21e82
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173433"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="762d4-102">如何：通过修改 DBML 文件生成自定义代码</span><span class="sxs-lookup"><span data-stu-id="762d4-102">How to: Generate Customized Code by Modifying a DBML File</span></span>

<span data-ttu-id="762d4-103">您可以 ( .dbml) 元数据文件生成 Visual Basic 或 c # 源代码。</span><span class="sxs-lookup"><span data-stu-id="762d4-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="762d4-104">此方法提供了一个在生成应用程序映射代码前自定义默认 .dbml 文件的机会。</span><span class="sxs-lookup"><span data-stu-id="762d4-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="762d4-105">这是一项高级功能。</span><span class="sxs-lookup"><span data-stu-id="762d4-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="762d4-106">此过程中的步骤如下：</span><span class="sxs-lookup"><span data-stu-id="762d4-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="762d4-107">生成 .dbml 文件。</span><span class="sxs-lookup"><span data-stu-id="762d4-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="762d4-108">使用编辑器修改此 .dbml 文件。</span><span class="sxs-lookup"><span data-stu-id="762d4-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="762d4-109">请注意，此 .dbml 文件必须通过 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml 文件的架构定义 (.xsd) 文件的验证。</span><span class="sxs-lookup"><span data-stu-id="762d4-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="762d4-110">有关详细信息，请参阅 [LINQ to SQL 中的代码生成](code-generation-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="762d4-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="762d4-111">生成 Visual Basic 或 c # 源代码。</span><span class="sxs-lookup"><span data-stu-id="762d4-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="762d4-112">下面的示例使用 SQLMetal 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="762d4-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="762d4-113">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="762d4-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="762d4-114">示例</span><span class="sxs-lookup"><span data-stu-id="762d4-114">Example</span></span>  

 <span data-ttu-id="762d4-115">下面的代码从 Northwind 示例数据库生成 .dbml 文件。</span><span class="sxs-lookup"><span data-stu-id="762d4-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="762d4-116">您可以使用数据库的名称或 .mdf 文件的名称作为数据库元数据的源。</span><span class="sxs-lookup"><span data-stu-id="762d4-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="762d4-117">示例</span><span class="sxs-lookup"><span data-stu-id="762d4-117">Example</span></span>  

 <span data-ttu-id="762d4-118">下面的代码从 .dbml 文件生成 Visual Basic 或 c # 源代码文件。</span><span class="sxs-lookup"><span data-stu-id="762d4-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="762d4-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="762d4-119">See also</span></span>

- [<span data-ttu-id="762d4-120">LINQ to SQL 中的代码生成</span><span class="sxs-lookup"><span data-stu-id="762d4-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="762d4-121">SqlMetal.exe（代码生成工具）</span><span class="sxs-lookup"><span data-stu-id="762d4-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="762d4-122">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="762d4-122">Creating the Object Model</span></span>](creating-the-object-model.md)
