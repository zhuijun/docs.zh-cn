---
title: 如何：显示生成的 SQL
description: 了解如何使用 Log 属性查看为查询生成的 SQL 代码，以帮助了解 LINQ to SQL 功能和调试。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 81f6b9603cc7f8b7863f787272ce6a1af920fa75
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169474"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="77dcc-103">如何：显示生成的 SQL</span><span class="sxs-lookup"><span data-stu-id="77dcc-103">How to: Display Generated SQL</span></span>

<span data-ttu-id="77dcc-104">您可以通过使用 <xref:System.Data.Linq.DataContext.Log%2A> 属性查看为查询生成的 SQL 代码和更改处理方式。</span><span class="sxs-lookup"><span data-stu-id="77dcc-104">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="77dcc-105">此方法对了解 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 功能和调试特定的问题可能很有用。</span><span class="sxs-lookup"><span data-stu-id="77dcc-105">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77dcc-106">示例</span><span class="sxs-lookup"><span data-stu-id="77dcc-106">Example</span></span>  

 <span data-ttu-id="77dcc-107">下面的示例使用 <xref:System.Data.Linq.DataContext.Log%2A> 属性在 SQL 代码执行前在控制台窗口中显示此代码。</span><span class="sxs-lookup"><span data-stu-id="77dcc-107">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="77dcc-108">您可以将此属性与查询、插入、更新和删除命令一起使用。</span><span class="sxs-lookup"><span data-stu-id="77dcc-108">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="77dcc-109">控制台窗口中的行是执行下面的 Visual Basic 或 c # 代码时看到的内容。</span><span class="sxs-lookup"><span data-stu-id="77dcc-109">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```console  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```console  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="77dcc-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="77dcc-110">See also</span></span>

- [<span data-ttu-id="77dcc-111">调试支持</span><span class="sxs-lookup"><span data-stu-id="77dcc-111">Debugging Support</span></span>](debugging-support.md)
