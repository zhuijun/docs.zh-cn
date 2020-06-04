---
title: 如何：控制投影的类型
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 6b809188f68805afcca960bd809e079d997e79c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357252"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="7e097-102">如何：控制投影的类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7e097-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="7e097-103">投影是一个过程，这一过程包括：获取一组数据，筛选这些数据，更改数据形状，甚至更改数据的类型。</span><span class="sxs-lookup"><span data-stu-id="7e097-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="7e097-104">大多数查询表达式都可执行投影。</span><span class="sxs-lookup"><span data-stu-id="7e097-104">Most query expressions perform projections.</span></span> <span data-ttu-id="7e097-105">本节中介绍的大多数查询表达式的计算结果都是 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，不过，可以控制投影的类型从而创建其他类型的集合。</span><span class="sxs-lookup"><span data-stu-id="7e097-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="7e097-106">本主题演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="7e097-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e097-107">示例</span><span class="sxs-lookup"><span data-stu-id="7e097-107">Example</span></span>  
 <span data-ttu-id="7e097-108">下面的示例定义一个新类型 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="7e097-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="7e097-109">然后，查询表达式在 `Customer` 子句中实例化新的 `Select` 对象。</span><span class="sxs-lookup"><span data-stu-id="7e097-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="7e097-110">这样，查询表达式的类型就是 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="7e097-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="7e097-111">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="7e097-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 <span data-ttu-id="7e097-112">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="7e097-112">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e097-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e097-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="7e097-114">投影和转换（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7e097-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
