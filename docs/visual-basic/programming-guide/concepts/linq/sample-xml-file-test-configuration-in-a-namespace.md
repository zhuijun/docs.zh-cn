---
title: 示例 XML 文件： Namespace3 中的测试配置
ms.date: 07/20/2015
ms.assetid: aff02614-30ee-45e1-bc0f-d64b193d20b8
ms.openlocfilehash: 6727a83e1373cd2d058bce2210993419effb1190
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360857"
---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="3452b-102">示例 XML 文件：命名空间中的测试配置</span><span class="sxs-lookup"><span data-stu-id="3452b-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="3452b-103">下面的 XML 文件用在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文档的很多示例中。</span><span class="sxs-lookup"><span data-stu-id="3452b-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="3452b-104">这是一个测试配置文件。</span><span class="sxs-lookup"><span data-stu-id="3452b-104">This is a test configuration file.</span></span> <span data-ttu-id="3452b-105">该 XML 在某个命名空间中。</span><span class="sxs-lookup"><span data-stu-id="3452b-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="3452b-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="3452b-106">TestConfigInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests xmlns="http://www.adatum.com">  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3452b-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3452b-107">See also</span></span>

- [<span data-ttu-id="3452b-108">示例 XML 文档 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3452b-108">Sample XML Documents (LINQ to XML)</span></span>](sample-xml-documents-linq-to-xml.md)
