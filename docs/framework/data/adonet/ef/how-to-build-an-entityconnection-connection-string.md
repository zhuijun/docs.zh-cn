---
title: 如何：生成 EntityConnection 连接字符串
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: 86ba3956797ff603dd944bfc8df1990df8f23001
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556429"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="289c9-102">如何：生成 EntityConnection 连接字符串</span><span class="sxs-lookup"><span data-stu-id="289c9-102">How to: Build an EntityConnection Connection String</span></span>
<span data-ttu-id="289c9-103">本主题提供有关如何生成 <xref:System.Data.EntityClient.EntityConnection> 的示例。</span><span class="sxs-lookup"><span data-stu-id="289c9-103">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="289c9-104">运行本示例中的代码</span><span class="sxs-lookup"><span data-stu-id="289c9-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="289c9-105">将 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 添加到项目中，并将项目配置为使用实体框架。</span><span class="sxs-lookup"><span data-stu-id="289c9-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="289c9-106">有关详细信息，请参阅 [如何：使用实体数据模型向导](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="289c9-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="289c9-107">在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：</span><span class="sxs-lookup"><span data-stu-id="289c9-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="289c9-108">示例</span><span class="sxs-lookup"><span data-stu-id="289c9-108">Example</span></span>  
 <span data-ttu-id="289c9-109">以下示例初始化基础提供程序的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>，然后初始化 <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> 对象并将此对象传递给 <xref:System.Data.EntityClient.EntityConnection> 的构造函数。</span><span class="sxs-lookup"><span data-stu-id="289c9-109">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="289c9-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="289c9-110">See also</span></span>

- <span data-ttu-id="289c9-111">[如何：将 EntityConnection 与对象上下文结合使用](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="289c9-111">[How to: Use EntityConnection with an Object Context](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span></span>
- [<span data-ttu-id="289c9-112">用于实体框架的 EntityClient 提供程序</span><span class="sxs-lookup"><span data-stu-id="289c9-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
