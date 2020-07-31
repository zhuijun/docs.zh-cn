---
title: 如何控制投影的类型 (C#)
description: 了解如何使用 C# 中的 LINQ 控制投影的类型，以创建 XElement 的 IEnumerable<T> 以外的类型集合。
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 32b019b5e1574e7160b4dce5fb0322caa3c1ca71
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103337"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="87218-103">如何控制投影的类型 (C#)</span><span class="sxs-lookup"><span data-stu-id="87218-103">How to control the type of a projection (C#)</span></span>
<span data-ttu-id="87218-104">投影是一个过程，这一过程包括：获取一组数据，筛选这些数据，更改数据形状，甚至更改数据的类型。</span><span class="sxs-lookup"><span data-stu-id="87218-104">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="87218-105">大多数查询表达式都可执行投影。</span><span class="sxs-lookup"><span data-stu-id="87218-105">Most query expressions perform projections.</span></span> <span data-ttu-id="87218-106">本节中介绍的大多数查询表达式的计算结果都是 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，不过，可以控制投影的类型从而创建其他类型的集合。</span><span class="sxs-lookup"><span data-stu-id="87218-106">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="87218-107">本主题演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="87218-107">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87218-108">示例</span><span class="sxs-lookup"><span data-stu-id="87218-108">Example</span></span>  
 <span data-ttu-id="87218-109">下面的示例定义一个新类型 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="87218-109">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="87218-110">然后，查询表达式在 `Customer` 子句中实例化新的 `Select` 对象。</span><span class="sxs-lookup"><span data-stu-id="87218-110">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="87218-111">这样，查询表达式的类型就是 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="87218-111">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="87218-112">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) 的架构定义。</span><span class="sxs-lookup"><span data-stu-id="87218-112">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 <span data-ttu-id="87218-113">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="87218-113">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="87218-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87218-114">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
