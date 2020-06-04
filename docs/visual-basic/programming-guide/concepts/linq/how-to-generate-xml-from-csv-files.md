---
title: 如何：从 CSV 文件生成 XML
ms.date: 07/20/2015
ms.assetid: fe4dbc87-7b0d-40bf-88c3-5d706ee89a4d
ms.openlocfilehash: 647cab02c730f18629c669c3526520b2a98a86d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396605"
---
# <a name="how-to-generate-xml-from-csv-files-visual-basic"></a><span data-ttu-id="2959c-102">如何：从 CSV 文件生成 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2959c-102">How to: Generate XML from CSV Files (Visual Basic)</span></span>
<span data-ttu-id="2959c-103">本示例演示如何使用语言集成查询 (LINQ) 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 从逗号分隔值 (CSV) 文件生成 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="2959c-103">This example shows how to use Language-Integrated Query (LINQ) and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to generate an XML file from a comma-separated value (CSV) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2959c-104">示例</span><span class="sxs-lookup"><span data-stu-id="2959c-104">Example</span></span>  
 <span data-ttu-id="2959c-105">下面的代码对字符串数组执行 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="2959c-105">The following code performs a LINQ query on an array of strings.</span></span>  
  
```vb  
      ' Create the text file.  
Dim csvString As String = "GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA" & vbCrLf & _  
    "HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA" & vbCrLf & _  
    "LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA" & vbCrLf & _  
    "LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA"  
File.WriteAllText("cust.csv", csvString)  
  
' Read into an array of strings.  
Dim source As String() = File.ReadAllLines("cust.csv")  
Dim cust As XElement = _  
    <Root>  
        <%= From strs In source _  
            Let fields = Split(strs, ",") _  
            Select _  
            <Customer CustomerID=<%= fields(0) %>>  
                <CompanyName><%= fields(1) %></CompanyName>  
                <ContactName><%= fields(2) %></ContactName>  
                <ContactTitle><%= fields(3) %></ContactTitle>  
                <Phone><%= fields(4) %></Phone>  
                <FullAddress>  
                    <Address><%= fields(5) %></Address>  
                    <City><%= fields(6) %></City>  
                    <Region><%= fields(7) %></Region>  
                    <PostalCode><%= fields(8) %></PostalCode>  
                    <Country><%= fields(9) %></Country>  
                </FullAddress>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(cust)  
```  
  
 <span data-ttu-id="2959c-106">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="2959c-106">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="LAZYK">  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(509) 555-7969</Phone>  
    <FullAddress>  
      <Address>12 Orchestra Terrace</Address>  
      <City>Walla Walla</City>  
      <Region>WA</Region>  
      <PostalCode>99362</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="LETSS">  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <ContactTitle>Owner</ContactTitle>  
    <Phone>(415) 555-5938</Phone>  
    <FullAddress>  
      <Address>87 Polk St. Suite 5</Address>  
      <City>San Francisco</City>  
      <Region>CA</Region>  
      <PostalCode>94117</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2959c-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2959c-107">See also</span></span>

- [<span data-ttu-id="2959c-108">投影和转换（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2959c-108">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
