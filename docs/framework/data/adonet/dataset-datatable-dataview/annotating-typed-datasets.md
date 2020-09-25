---
title: 为类型化的数据集进行批注
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 79d3913827d5df6f0ac4e77bfdb8f37b553a86d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203743"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="40778-102">为类型化的数据集进行批注</span><span class="sxs-lookup"><span data-stu-id="40778-102">Annotating Typed DataSets</span></span>

<span data-ttu-id="40778-103">批注使您能够在不修改基础架构的情况下修改类型化 <xref:System.Data.DataSet> 中元素的名称。</span><span class="sxs-lookup"><span data-stu-id="40778-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="40778-104">修改基础架构中元素的名称将导致类型化 **数据集** 引用数据源中不存在的对象，并丢失对数据源中存在的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="40778-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="40778-105">使用批注，你可以使用更有意义的名称来自定义类型化 **数据集中** 的对象的名称，从而使代码更易于阅读，并且你的类型化 **数据集** 更易于供客户端使用，同时保持基础架构不变。</span><span class="sxs-lookup"><span data-stu-id="40778-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="40778-106">例如， **Northwind**数据库的**Customers**表的以下 Schema 元素会导致**DataRow**对象名称**CustomersRow**和 <xref:System.Data.DataRowCollection> 命名**客户**。</span><span class="sxs-lookup"><span data-stu-id="40778-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="40778-107">客户端代码中**客户**端代码的**DataRowCollection**名称是有意义的，但**DataRow**名称**CustomersRow**会产生误导，因为它是单个对象。</span><span class="sxs-lookup"><span data-stu-id="40778-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="40778-108">此外，在常见情况下，对象会被称为没有 **行** 标识符，而只是将其称为 **Customer** 对象。</span><span class="sxs-lookup"><span data-stu-id="40778-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="40778-109">解决方法是为该架构添加注释并标识 **DataRow** 和 **DataRowCollection** 对象的新名称。</span><span class="sxs-lookup"><span data-stu-id="40778-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="40778-110">下面是上一架构的批注版本。</span><span class="sxs-lookup"><span data-stu-id="40778-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="40778-111">将 **typedName** 值指定为 **Customer** 将导致 **DataRow** 对象名称为 **customer**。</span><span class="sxs-lookup"><span data-stu-id="40778-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="40778-112">指定**客户**的**typedPlural**值将保留**客户**的**DataRowCollection**名称。</span><span class="sxs-lookup"><span data-stu-id="40778-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="40778-113">下表显示可用的批注。</span><span class="sxs-lookup"><span data-stu-id="40778-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="40778-114">Annotation</span><span class="sxs-lookup"><span data-stu-id="40778-114">Annotation</span></span>|<span data-ttu-id="40778-115">描述</span><span class="sxs-lookup"><span data-stu-id="40778-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="40778-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="40778-116">**typedName**</span></span>|<span data-ttu-id="40778-117">对象的名称。</span><span class="sxs-lookup"><span data-stu-id="40778-117">Name of the object.</span></span>|  
|<span data-ttu-id="40778-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="40778-118">**typedPlural**</span></span>|<span data-ttu-id="40778-119">对象集合的名称。</span><span class="sxs-lookup"><span data-stu-id="40778-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="40778-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="40778-120">**typedParent**</span></span>|<span data-ttu-id="40778-121">对象在父关系中被引用时的名称。</span><span class="sxs-lookup"><span data-stu-id="40778-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="40778-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="40778-122">**typedChildren**</span></span>|<span data-ttu-id="40778-123">用于从子关系中返回对象的方法的名称。</span><span class="sxs-lookup"><span data-stu-id="40778-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="40778-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="40778-124">**nullValue**</span></span>|<span data-ttu-id="40778-125">如果基础值为 **DBNull**，则值为。</span><span class="sxs-lookup"><span data-stu-id="40778-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="40778-126">请参阅下表了解 **nullValue** 批注。</span><span class="sxs-lookup"><span data-stu-id="40778-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="40778-127">默认值为 **_throw**。</span><span class="sxs-lookup"><span data-stu-id="40778-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="40778-128">下表显示了可为 **nullValue** 批注指定的值。</span><span class="sxs-lookup"><span data-stu-id="40778-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="40778-129">nullValue 值</span><span class="sxs-lookup"><span data-stu-id="40778-129">nullValue Value</span></span>|<span data-ttu-id="40778-130">描述</span><span class="sxs-lookup"><span data-stu-id="40778-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="40778-131">*替换值*</span><span class="sxs-lookup"><span data-stu-id="40778-131">*Replacement Value*</span></span>|<span data-ttu-id="40778-132">指定要返回的值。</span><span class="sxs-lookup"><span data-stu-id="40778-132">Specify a value to be returned.</span></span> <span data-ttu-id="40778-133">所返回的值必须匹配该元素的类型。</span><span class="sxs-lookup"><span data-stu-id="40778-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="40778-134">例如，使用 `nullValue="0"` 可为空整数字段返回 0。</span><span class="sxs-lookup"><span data-stu-id="40778-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="40778-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="40778-135">**_throw**</span></span>|<span data-ttu-id="40778-136">引发异常。</span><span class="sxs-lookup"><span data-stu-id="40778-136">Throw an exception.</span></span> <span data-ttu-id="40778-137">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="40778-137">This is the default.</span></span>|  
|<span data-ttu-id="40778-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="40778-138">**_null**</span></span>|<span data-ttu-id="40778-139">如果遇到基元类型，则返回空引用或引发异常。</span><span class="sxs-lookup"><span data-stu-id="40778-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="40778-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="40778-140">**_empty**</span></span>|<span data-ttu-id="40778-141">对于字符串，返回 **String。** 如果为空，则返回从空构造函数创建的对象。</span><span class="sxs-lookup"><span data-stu-id="40778-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="40778-142">如果遇到基元类型，则引发异常。</span><span class="sxs-lookup"><span data-stu-id="40778-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="40778-143">下表显示了类型化 **数据集中** 的对象的默认值和可用的批注。</span><span class="sxs-lookup"><span data-stu-id="40778-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="40778-144">对象/方法/事件</span><span class="sxs-lookup"><span data-stu-id="40778-144">Object/Method/Event</span></span>|<span data-ttu-id="40778-145">默认</span><span class="sxs-lookup"><span data-stu-id="40778-145">Default</span></span>|<span data-ttu-id="40778-146">Annotation</span><span class="sxs-lookup"><span data-stu-id="40778-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="40778-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="40778-147">**DataTable**</span></span>|<span data-ttu-id="40778-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="40778-148">TableNameDataTable</span></span>|<span data-ttu-id="40778-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="40778-149">typedPlural</span></span>|  
|<span data-ttu-id="40778-150">**DataTable** 方法</span><span class="sxs-lookup"><span data-stu-id="40778-150">**DataTable** Methods</span></span>|<span data-ttu-id="40778-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="40778-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="40778-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="40778-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="40778-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="40778-153">DeleteTableNameRow</span></span>|<span data-ttu-id="40778-154">typedName</span><span class="sxs-lookup"><span data-stu-id="40778-154">typedName</span></span>|  
|<span data-ttu-id="40778-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="40778-155">**DataRowCollection**</span></span>|<span data-ttu-id="40778-156">TableName</span><span class="sxs-lookup"><span data-stu-id="40778-156">TableName</span></span>|<span data-ttu-id="40778-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="40778-157">typedPlural</span></span>|  
|<span data-ttu-id="40778-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="40778-158">**DataRow**</span></span>|<span data-ttu-id="40778-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="40778-159">TableNameRow</span></span>|<span data-ttu-id="40778-160">typedName</span><span class="sxs-lookup"><span data-stu-id="40778-160">typedName</span></span>|  
|<span data-ttu-id="40778-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="40778-161">**DataColumn**</span></span>|<span data-ttu-id="40778-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="40778-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="40778-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="40778-163">DataRow.ColumnName</span></span>|<span data-ttu-id="40778-164">typedName</span><span class="sxs-lookup"><span data-stu-id="40778-164">typedName</span></span>|  
|<span data-ttu-id="40778-165">**属性**</span><span class="sxs-lookup"><span data-stu-id="40778-165">**Property**</span></span>|<span data-ttu-id="40778-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="40778-166">PropertyName</span></span>|<span data-ttu-id="40778-167">typedName</span><span class="sxs-lookup"><span data-stu-id="40778-167">typedName</span></span>|  
|<span data-ttu-id="40778-168">**子** 者</span><span class="sxs-lookup"><span data-stu-id="40778-168">**Child** Accessor</span></span>|<span data-ttu-id="40778-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="40778-169">GetChildTableNameRows</span></span>|<span data-ttu-id="40778-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="40778-170">typedChildren</span></span>|  
|<span data-ttu-id="40778-171">**父项** 者</span><span class="sxs-lookup"><span data-stu-id="40778-171">**Parent** Accessor</span></span>|<span data-ttu-id="40778-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="40778-172">TableNameRow</span></span>|<span data-ttu-id="40778-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="40778-173">typedParent</span></span>|  
|<span data-ttu-id="40778-174">**数据集** 事件</span><span class="sxs-lookup"><span data-stu-id="40778-174">**DataSet** Events</span></span>|<span data-ttu-id="40778-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="40778-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="40778-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="40778-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="40778-177">typedName</span><span class="sxs-lookup"><span data-stu-id="40778-177">typedName</span></span>|  
  
 <span data-ttu-id="40778-178">若要使用类型化 **数据集** 批注，您必须在 XML 架构定义语言中包含以下 (XSD) 架构的 **xmlns** 引用。</span><span class="sxs-lookup"><span data-stu-id="40778-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="40778-179">若要从数据库表创建 xsd，请参阅 <xref:System.Data.DataSet.WriteXmlSchema%2A> 或 [使用 Visual Studio 中的数据集](/visualstudio/data-tools/dataset-tools-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="40778-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="40778-180">下面是一个示例批注的架构，它公开**Northwind**数据库的**Customers**表，其中包含与**Orders**表的关系。</span><span class="sxs-lookup"><span data-stu-id="40778-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="40778-181">下面的代码示例使用从示例架构创建的强类型化 **数据集** 。</span><span class="sxs-lookup"><span data-stu-id="40778-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="40778-182">它使用一个 <xref:System.Data.SqlClient.SqlDataAdapter> 填充 **Customers** 表，另一个用于 <xref:System.Data.SqlClient.SqlDataAdapter> 填充 **Orders** 表。</span><span class="sxs-lookup"><span data-stu-id="40778-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="40778-183">强类型化 **数据集** 定义 **datarelation**。</span><span class="sxs-lookup"><span data-stu-id="40778-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="40778-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="40778-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="40778-185">类型化数据集</span><span class="sxs-lookup"><span data-stu-id="40778-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="40778-186">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="40778-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="40778-187">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="40778-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
