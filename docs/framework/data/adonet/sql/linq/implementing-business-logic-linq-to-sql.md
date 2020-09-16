---
title: 实现业务逻辑 (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: a8be0bd542c76e732d47c19f1d3b578884e2b5ff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558922"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="6d277-102">实现业务逻辑 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="6d277-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="6d277-103">本主题中的术语“业务逻辑”指的是在对数据库数据进行插入、更新或删除操作之前，应用于数据的任何自定义规则或验证测试。</span><span class="sxs-lookup"><span data-stu-id="6d277-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="6d277-104">业务逻辑有时也称为“业务规则”或“域逻辑”。</span><span class="sxs-lookup"><span data-stu-id="6d277-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="6d277-105">在 n 层应用程序中，业务逻辑通常设计为逻辑层，因此可以独立于表示层或数据访问层进行修改。</span><span class="sxs-lookup"><span data-stu-id="6d277-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="6d277-106">在对数据库数据进行任何更新、插入或删除操作前后，数据访问层可以调用业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="6d277-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="6d277-107">业务逻辑可以和架构验证一样简单，以确保字段类型与表列类型兼容。</span><span class="sxs-lookup"><span data-stu-id="6d277-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="6d277-108">它也可以包含一组以任意复杂方式进行交互的对象。</span><span class="sxs-lookup"><span data-stu-id="6d277-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="6d277-109">这些规则可以作为数据库上的存储过程或内存中的对象来实现。</span><span class="sxs-lookup"><span data-stu-id="6d277-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="6d277-110">无论通过何种方式实现业务逻辑，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 都允许您使用分部类和分部方法，将业务逻辑与数据访问代码分开。</span><span class="sxs-lookup"><span data-stu-id="6d277-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="6d277-111">LINQ to SQL 如何调用业务逻辑</span><span class="sxs-lookup"><span data-stu-id="6d277-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="6d277-112">当你在设计时（手动或通过使用对象关系设计器或 SQLMetal）生成实体类时，它将定义为一个分部类。</span><span class="sxs-lookup"><span data-stu-id="6d277-112">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="6d277-113">这意味着，在单独的代码文件中，可以定义包含自定义业务逻辑的另一部分实体类。</span><span class="sxs-lookup"><span data-stu-id="6d277-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="6d277-114">在编译时，这两个部分将合并成一个类。</span><span class="sxs-lookup"><span data-stu-id="6d277-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="6d277-115">但是，如果必须通过使用对象关系设计器或 SQLMetal 来重新生成实体类，则可以这样做，并且不会修改类的一部分。</span><span class="sxs-lookup"><span data-stu-id="6d277-115">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="6d277-116">定义实体和 <xref:System.Data.Linq.DataContext> 的分部类包含分部方法。</span><span class="sxs-lookup"><span data-stu-id="6d277-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="6d277-117">这些是扩展性点，可以在进行任何更新、插入或删除前后用于对实体或实体属性应用业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="6d277-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="6d277-118">分部方法可以视为编译时事件。</span><span class="sxs-lookup"><span data-stu-id="6d277-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="6d277-119">代码生成器定义方法签名，并在 get 和 set 属性访问器、`DataContext` 构造函数中调用这些方法，有些情况下还在调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时在后台调用方法。</span><span class="sxs-lookup"><span data-stu-id="6d277-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="6d277-120">但是，如果未实现特殊的分部方法，那么在编译时将移除对该分部方法的所有引用和定义。</span><span class="sxs-lookup"><span data-stu-id="6d277-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="6d277-121">在你在单独的代码文件中编写的实现定义中，可以执行所需的任何自定义逻辑。</span><span class="sxs-lookup"><span data-stu-id="6d277-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="6d277-122">可以将分部类本身用作域层，也可以从分部方法的实现定义，将分部类调入单独对象或多个对象。</span><span class="sxs-lookup"><span data-stu-id="6d277-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="6d277-123">无论采用何种方式，业务逻辑都将与数据访问代码和表示层代码完全分开。</span><span class="sxs-lookup"><span data-stu-id="6d277-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="6d277-124">详细了解扩展性点</span><span class="sxs-lookup"><span data-stu-id="6d277-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="6d277-125">下面的示例演示了由对象关系设计器为类生成的代码的一部分 `DataContext` ，其中包含两个表： `Customers` 和 `Orders` 。</span><span class="sxs-lookup"><span data-stu-id="6d277-125">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="6d277-126">注意为该类的每个表都定义了插入、更新和删除方法。</span><span class="sxs-lookup"><span data-stu-id="6d277-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 <span data-ttu-id="6d277-127">如果在分部类中实现插入、更新和删除方法，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 运行时将在调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时调用这些方法，而不是自己的默认方法。</span><span class="sxs-lookup"><span data-stu-id="6d277-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="6d277-128">这使您能够重写创建/读取/更新/删除操作的默认行为。</span><span class="sxs-lookup"><span data-stu-id="6d277-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="6d277-129">有关详细信息，请参阅 [演练：自定义实体类的插入、更新和删除行为](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)。</span><span class="sxs-lookup"><span data-stu-id="6d277-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="6d277-130">`OnCreated` 方法在类构造函数中调用。</span><span class="sxs-lookup"><span data-stu-id="6d277-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 <span data-ttu-id="6d277-131">此实体类有三个方法，当创建、加载和验证实体时（调用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 时），`SubmitChanges` 运行时会调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="6d277-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="6d277-132">此实体类还为每个属性提供两个分部方法，一个在设置属性前调用，另一个在设置属性后调用。</span><span class="sxs-lookup"><span data-stu-id="6d277-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="6d277-133">下面的代码示例显示为 `Customer` 类生成的一些方法：</span><span class="sxs-lookup"><span data-stu-id="6d277-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 <span data-ttu-id="6d277-134">在属性 set 访问器中调用这些方法，如下面的 `CustomerID` 属性示例中所示。</span><span class="sxs-lookup"><span data-stu-id="6d277-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 <span data-ttu-id="6d277-135">在类的自定义部分，编写方法的实现定义。</span><span class="sxs-lookup"><span data-stu-id="6d277-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="6d277-136">在 Visual Studio 中，键入后 `partial` 将在类的其他部分中看到方法定义的 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="6d277-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 <span data-ttu-id="6d277-137">有关如何使用分部方法向应用程序添加业务逻辑的更多信息，请参见下列主题：</span><span class="sxs-lookup"><span data-stu-id="6d277-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="6d277-138">如何：向实体类添加验证</span><span class="sxs-lookup"><span data-stu-id="6d277-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="6d277-139">演练：自定义实体类的插入、更新和删除行为</span><span class="sxs-lookup"><span data-stu-id="6d277-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="6d277-140">[演练：向实体类添加验证](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6d277-140">[Walkthrough: Adding Validation to Entity Classes](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d277-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="6d277-141">See also</span></span>

- [<span data-ttu-id="6d277-142">分部类和方法</span><span class="sxs-lookup"><span data-stu-id="6d277-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="6d277-143">分部方法</span><span class="sxs-lookup"><span data-stu-id="6d277-143">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="6d277-144">Visual Studio 中的 LINQ to SQL 工具</span><span class="sxs-lookup"><span data-stu-id="6d277-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="6d277-145">SqlMetal.exe（代码生成工具）</span><span class="sxs-lookup"><span data-stu-id="6d277-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
