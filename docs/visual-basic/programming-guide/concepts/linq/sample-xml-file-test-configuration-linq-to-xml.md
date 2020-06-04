---
title: 示例 XML 文件：测试配置 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 2e0e19f2-83e4-42ad-958a-6b3e34c9bf17
ms.openlocfilehash: b971044ad28763858f40d36e454c08762598a435
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360847"
---
# <a name="sample-xml-file-test-configuration-linq-to-xml"></a><span data-ttu-id="f902c-102">示例 XML 文件：测试配置 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f902c-102">Sample XML File: Test Configuration (LINQ to XML)</span></span>
<span data-ttu-id="f902c-103">下面的 XML 文件用在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文档的很多示例中。</span><span class="sxs-lookup"><span data-stu-id="f902c-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="f902c-104">这是一个测试配置文件。</span><span class="sxs-lookup"><span data-stu-id="f902c-104">This is a test configuration file.</span></span>  
  
## <a name="testconfigxml"></a><span data-ttu-id="f902c-105">TestConfig.xml</span><span class="sxs-lookup"><span data-stu-id="f902c-105">TestConfig.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests>  
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
  
## <a name="see-also"></a><span data-ttu-id="f902c-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f902c-106">See also</span></span>

- [<span data-ttu-id="f902c-107">示例 XML 文档 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f902c-107">Sample XML Documents (LINQ to XML)</span></span>](sample-xml-documents-linq-to-xml.md)
