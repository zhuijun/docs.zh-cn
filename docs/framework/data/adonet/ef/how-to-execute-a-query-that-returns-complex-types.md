---
title: 如何：执行返回复杂类型的查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: e5358e3a1295b180356ed6c127111313b44de277
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198478"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="d95d6-102">如何：执行返回复杂类型的查询</span><span class="sxs-lookup"><span data-stu-id="d95d6-102">How to: Execute a Query that Returns Complex Types</span></span>

<span data-ttu-id="d95d6-103">本主题演示如何执行返回包含复杂类型属性的实体类型对象的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="d95d6-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d95d6-104">运行本示例中的代码</span><span class="sxs-lookup"><span data-stu-id="d95d6-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="d95d6-105">将 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 添加到项目中，并将项目配置为使用实体框架。</span><span class="sxs-lookup"><span data-stu-id="d95d6-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="d95d6-106">有关详细信息，请参阅 [如何：使用实体数据模型向导](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d95d6-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d95d6-107">在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：</span><span class="sxs-lookup"><span data-stu-id="d95d6-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="d95d6-108">双击 .edmx 文件可在 Entity Designer 的 " [模型浏览器" 窗口](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) 中显示该模型。</span><span class="sxs-lookup"><span data-stu-id="d95d6-108">Double click the .edmx file to display the model in the [Model Browser window](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="d95d6-109">在 Entity Designer 图面上，选择 `Email` `Phone` 实体类型的和属性 `Contact` ，然后右键单击并选择 " **重构为新的复杂类型**"。</span><span class="sxs-lookup"><span data-stu-id="d95d6-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="d95d6-110">具有选定和属性的新复杂 `Email` 类型 `Phone` 将添加到 **模型浏览器**。</span><span class="sxs-lookup"><span data-stu-id="d95d6-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="d95d6-111">为复杂类型提供了一个默认名称： `EmailPhone` 在 " **属性** " 窗口中将该类型重命名为。</span><span class="sxs-lookup"><span data-stu-id="d95d6-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="d95d6-112">此外，新的 `ComplexProperty` 属性将添加到 `Contact` 实体类型。</span><span class="sxs-lookup"><span data-stu-id="d95d6-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="d95d6-113">将该属性重命名为 `EmailPhoneComplexType.`。</span><span class="sxs-lookup"><span data-stu-id="d95d6-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="d95d6-114">有关使用实体数据模型向导创建和修改复杂类型的信息，请参阅 [如何：将现有属性重构为复杂类型属性](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) 和 [如何：创建和修改复杂类型](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d95d6-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d95d6-115">示例</span><span class="sxs-lookup"><span data-stu-id="d95d6-115">Example</span></span>  

 <span data-ttu-id="d95d6-116">下面的示例执行一个查询，该查询返回对象的集合 `Contact` 并显示对象的两个属性 `Contact` ： `ContactID` 和 `EmailPhoneComplexType` 复杂类型的值。</span><span class="sxs-lookup"><span data-stu-id="d95d6-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
