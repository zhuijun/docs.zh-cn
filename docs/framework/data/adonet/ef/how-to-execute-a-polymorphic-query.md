---
title: 如何：执行多态查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: ad6fd7bf6a23f4cd1591a17b25042fd76ff1d08d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545332"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="e8e90-102">如何：执行多态查询</span><span class="sxs-lookup"><span data-stu-id="e8e90-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="e8e90-103">本主题说明如何 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 使用 [OFTYPE](./language-reference/oftype-entity-sql.md) 运算符执行多态查询。</span><span class="sxs-lookup"><span data-stu-id="e8e90-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="e8e90-104">运行本示例中的代码</span><span class="sxs-lookup"><span data-stu-id="e8e90-104">To run the code in this example</span></span>

1. <span data-ttu-id="e8e90-105">将 [School 模型](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) 添加到项目中，并将项目配置为使用实体框架。</span><span class="sxs-lookup"><span data-stu-id="e8e90-105">Add the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="e8e90-106">有关详细信息，请参阅 [如何：使用实体数据模型向导](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e8e90-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="e8e90-107">在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：</span><span class="sxs-lookup"><span data-stu-id="e8e90-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="e8e90-108">按照 [演练：映射继承-每个层次结构一个表](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))中的步骤修改概念模型，使其具有每个层次结构一个表继承。</span><span class="sxs-lookup"><span data-stu-id="e8e90-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="e8e90-109">示例</span><span class="sxs-lookup"><span data-stu-id="e8e90-109">Example</span></span>

<span data-ttu-id="e8e90-110">下面的示例使用 OFTYPE 运算符从 `OnsiteCourses` 的集合中获取和显示仅包含 `Courses` 的集合。</span><span class="sxs-lookup"><span data-stu-id="e8e90-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="e8e90-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="e8e90-111">See also</span></span>

- [<span data-ttu-id="e8e90-112">用于实体框架的 EntityClient 提供程序</span><span class="sxs-lookup"><span data-stu-id="e8e90-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="e8e90-113">Entity SQL 语言</span><span class="sxs-lookup"><span data-stu-id="e8e90-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
