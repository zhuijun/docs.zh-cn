---
title: XML 架构定义工具和 XML 序列化
description: XML 架构定义工具为 XSD 架构生成 C# 或 Visual Basic 类文件，并从库或可执行文件生成 XML 架构。
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 6451f3b5f6e8ec2c1454e5cf7ffb95a96b620214
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554978"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="34993-103">XML 架构定义工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="34993-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="34993-104">XML 架构定义工具（[XML 架构定义工具 (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)）是作为 Windows&reg; 软件开发工具包 (SDK) 的一部分随 .NET Framework 工具一起安装的。</span><span class="sxs-lookup"><span data-stu-id="34993-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="34993-105">该工具主要有下面两个用途：</span><span class="sxs-lookup"><span data-stu-id="34993-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="34993-106">生成 C# 或 Visual Basic 类文件，而这些文件符合特定的 XML 架构定义语言 (XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="34993-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="34993-107">该工具将 XML 架构用作参数，并输出一个包含若干类的文件，在使用 <xref:System.Xml.Serialization.XmlSerializer> 进行序列化时，这些类符合这种架构。</span><span class="sxs-lookup"><span data-stu-id="34993-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="34993-108">有关如何使用该工具生成符合特定架构的类的信息，请参阅[如何：使用 XML 架构定义工具生成类和 XML 架构文档](xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="34993-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="34993-109">通过 .dll 或 .exe 文件生成 XML 架构文档。</span><span class="sxs-lookup"><span data-stu-id="34993-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="34993-110">若要查看已经创建或已使用特性进行修改的一组文件的架构，可以将 DLL 或 EXE 作为参数传递到该工具，以便生成 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="34993-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="34993-111">有关如何使用该工具从一组类生成 XML 架构文档的信息，请参阅[如何：使用 XML 架构定义工具生成类和 XML 架构文档](xml-schema-def-tool-gen.md)。</span><span class="sxs-lookup"><span data-stu-id="34993-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="34993-112">有关使用此工具的详细信息，请参阅 [XML 架构定义工具 (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="34993-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34993-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="34993-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="34993-114">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="34993-114">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="34993-115">XML 架构定义工具 (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="34993-115">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="34993-116">如何：序列化对象</span><span class="sxs-lookup"><span data-stu-id="34993-116">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="34993-117">如何：反序列化对象</span><span class="sxs-lookup"><span data-stu-id="34993-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="34993-118">如何：使用 XML 架构定义工具生成类和 XML 架构文档</span><span class="sxs-lookup"><span data-stu-id="34993-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](xml-schema-def-tool-gen.md)
- <span data-ttu-id="34993-119">[XML 架构绑定支持](/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="34993-119">[XML Schema Binding Support](/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
