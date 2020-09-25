---
title: 如何：执行返回 PrimitiveType 结果的查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: 3f1d589a37eca0254ecd3da96cd5731087c5027a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198374"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a><span data-ttu-id="f1cc4-102">如何：执行返回 PrimitiveType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="f1cc4-102">How to: Execute a Query that Returns PrimitiveType Results</span></span>

<span data-ttu-id="f1cc4-103">本主题演示如何使用 <xref:System.Data.EntityClient.EntityCommand> 针对概念模型执行命令，以及如何使用 <xref:System.Data.Metadata.Edm.PrimitiveType> 检索 <xref:System.Data.EntityClient.EntityDataReader> 结果。</span><span class="sxs-lookup"><span data-stu-id="f1cc4-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand>, and how to retrieve the <xref:System.Data.Metadata.Edm.PrimitiveType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="f1cc4-104">运行本示例中的代码</span><span class="sxs-lookup"><span data-stu-id="f1cc4-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="f1cc4-105">将 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 添加到项目中，并将项目配置为使用实体框架。</span><span class="sxs-lookup"><span data-stu-id="f1cc4-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="f1cc4-106">有关详细信息，请参阅 [如何：使用实体数据模型向导](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f1cc4-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f1cc4-107">在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：</span><span class="sxs-lookup"><span data-stu-id="f1cc4-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="f1cc4-108">示例</span><span class="sxs-lookup"><span data-stu-id="f1cc4-108">Example</span></span>  

 <span data-ttu-id="f1cc4-109">本示例执行返回 <xref:System.Data.Metadata.Edm.PrimitiveType> 结果的查询。</span><span class="sxs-lookup"><span data-stu-id="f1cc4-109">This example executes a query that returns a <xref:System.Data.Metadata.Edm.PrimitiveType> result.</span></span> <span data-ttu-id="f1cc4-110">如果将以下查询作为自变量传递给 `ExecutePrimitiveTypeQuery` 函数，则该函数将显示所有 `Products` 的平均定价：</span><span class="sxs-lookup"><span data-stu-id="f1cc4-110">If you pass the following query as an argument to the `ExecutePrimitiveTypeQuery` function, the function displays the average list price of all `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 <span data-ttu-id="f1cc4-111">如果传递参数化查询（如下面的查询），请将 <xref:System.Data.EntityClient.EntityParameter> 对象添加到 <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> 对象的 <xref:System.Data.EntityClient.EntityCommand> 属性。</span><span class="sxs-lookup"><span data-stu-id="f1cc4-111">If you pass a parameterized query, like the following, <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a><span data-ttu-id="f1cc4-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="f1cc4-112">See also</span></span>

- [<span data-ttu-id="f1cc4-113">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="f1cc4-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="f1cc4-114">用于实体框架的 EntityClient 提供程序</span><span class="sxs-lookup"><span data-stu-id="f1cc4-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
