---
title: 创建数据表
description: 了解如何在 ADO.NET 中创建一个 DataTable，它代表一个内存中关系数据表，以独立方式或其他 .NET Framework 对象使用。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 75c9bcf0e0b6180030825b4d1e7dd9e1f9686712
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198634"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="99782-103">创建数据表</span><span class="sxs-lookup"><span data-stu-id="99782-103">Creating a DataTable</span></span>

<span data-ttu-id="99782-104"><xref:System.Data.DataTable> 表示一个内存内关系数据的表，可以独立创建和使用，也可以由其他 .NET Framework 对象使用，最常见的情况是作为 <xref:System.Data.DataSet> 的成员使用。</span><span class="sxs-lookup"><span data-stu-id="99782-104">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="99782-105">您可以使用相应的**datatable**构造函数创建**datatable**对象。</span><span class="sxs-lookup"><span data-stu-id="99782-105">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="99782-106">您可以通过使用**add**方法将其添加到**DataTable**对象的**Tables**集合中，将其添加到**数据集**。</span><span class="sxs-lookup"><span data-stu-id="99782-106">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="99782-107">你还可以使用**DataAdapter**对象的**Fill**或**FillSchema**方法，或使用**dataset**的**ReadXml**、 **READXMLSCHEMA**或**InferXmlSchema**方法从预**定义的或**推断的 XML 架构中创建**DataTable**对象。</span><span class="sxs-lookup"><span data-stu-id="99782-107">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="99782-108">请注意，将**DataTable**添加为一个**数据集**的**tables**集合的成员后，不能将其添加到任何其他**数据集**的表的集合中。</span><span class="sxs-lookup"><span data-stu-id="99782-108">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="99782-109">当你首次创建 **DataTable**时，它没有架构 (即结构) 。</span><span class="sxs-lookup"><span data-stu-id="99782-109">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="99782-110">若要定义表的架构，必须创建对象并将其添加 <xref:System.Data.DataColumn> 到表的 **Columns** 集合中。</span><span class="sxs-lookup"><span data-stu-id="99782-110">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="99782-111">您还可以为表定义主键列，并创建 **约束** 对象并将其添加到表的 **约束** 集合。</span><span class="sxs-lookup"><span data-stu-id="99782-111">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="99782-112">为 **DataTable**定义了架构之后，可以通过将 **DataRow** 对象添加到表的 **rows** 集合中来向表中添加数据行。</span><span class="sxs-lookup"><span data-stu-id="99782-112">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="99782-113">创建 DataTable 时，不需要提供属性的值 <xref:System.Data.DataTable.TableName%2A> ; 您可以在其他**DataTable**时间指定该属性，也可以将其留空。</span><span class="sxs-lookup"><span data-stu-id="99782-113">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="99782-114">但是，当您将没有 **TableName** 值的表添加到 **数据集**时，将为该表给定增量默认名称表*N*，并以 "table" 作为 Table0。</span><span class="sxs-lookup"><span data-stu-id="99782-114">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99782-115">当你提供**TableName**值时，我们建议你避免使用 "Table*N*" 命名约定，因为所提供的名称可能与**数据集中**的现有默认表名称冲突。</span><span class="sxs-lookup"><span data-stu-id="99782-115">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="99782-116">如果提供的名称已经存在，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="99782-116">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="99782-117">下面的示例创建 **DataTable** 对象的一个实例，并为其分配名称 "Customers"。</span><span class="sxs-lookup"><span data-stu-id="99782-117">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="99782-118">下面的示例通过将 DataTable 添加到**DataSet**的**Tables**集合来创建**DataTable**的实例。</span><span class="sxs-lookup"><span data-stu-id="99782-118">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="99782-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="99782-119">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="99782-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="99782-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="99782-121">从 DataAdapter 填充数据集</span><span class="sxs-lookup"><span data-stu-id="99782-121">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="99782-122">从 XML 加载数据集</span><span class="sxs-lookup"><span data-stu-id="99782-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="99782-123">从 XML 加载数据集架构信息</span><span class="sxs-lookup"><span data-stu-id="99782-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="99782-124">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="99782-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
