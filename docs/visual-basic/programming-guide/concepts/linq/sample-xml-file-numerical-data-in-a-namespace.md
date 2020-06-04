---
title: 示例 XML 文件：命名空间中的数值数据
ms.date: 07/20/2015
ms.assetid: f01cc0a1-fb55-4b42-8380-16f4be47d6f4
ms.openlocfilehash: 37e9cdcdd3a1d570f9602ddf72f770def9f4b283
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360938"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a>示例 XML 文件：命名空间中的数值数据
下面的 XML 文件用在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文档的很多示例中。 此文件包含数值数据，用于求和、求平均值和分组。 该 XML 在某个命名空间中。  
  
## <a name="data"></a>data  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
  
## <a name="see-also"></a>另请参阅

- [示例 XML 文档 (LINQ to XML)](sample-xml-documents-linq-to-xml.md)
