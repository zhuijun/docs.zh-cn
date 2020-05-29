---
title: XML 和 SOAP 序列化
description: 本概述讨论了 XML 序列化，其可用于将对象序列化为符合 SOAP 规范的 XML 流。
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 6b7d6f59694a28207758fa7772781eed073917e4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379544"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="5902d-103">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="5902d-103">XML and SOAP serialization</span></span>

<span data-ttu-id="5902d-104">XML 序列化将对象的公共字段和属性以及方法的参数和返回值转换（序列化）为符合特定 XML 架构定义语言 (XSD) 文档的 XML 流。</span><span class="sxs-lookup"><span data-stu-id="5902d-104">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="5902d-105">XML 序列化会生成强类型类，同时将公共属性和字段转换为序列格式（在此情况下为 XML），以便存储或传输。</span><span class="sxs-lookup"><span data-stu-id="5902d-105">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="5902d-106">由于 XML 是开放式的标准，因此可以根据需要由任何应用程序处理 XML 流，而与平台无关。</span><span class="sxs-lookup"><span data-stu-id="5902d-106">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="5902d-107">例如，用 ASP.NET 创建的 XML Web services 使用 <xref:System.Xml.Serialization.XmlSerializer> 类来创建 XML 流，这些流在整个 Internet 中或在 Intranet 上的 XML Web services 应用程序之间传递数据。</span><span class="sxs-lookup"><span data-stu-id="5902d-107">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="5902d-108">相反，反序列化采用这样一个 XML 流并重新构造对象。</span><span class="sxs-lookup"><span data-stu-id="5902d-108">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="5902d-109">XML 序列化还可用于将对象序列化为符合 SOAP 规范的 XML 流。</span><span class="sxs-lookup"><span data-stu-id="5902d-109">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="5902d-110">SOAP 是一种基于 XML 的协议，它是专门为使用 XML 来传输过程调用而设计的。</span><span class="sxs-lookup"><span data-stu-id="5902d-110">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="5902d-111">若要序列化或反序列化对象，请使用 <xref:System.Xml.Serialization.XmlSerializer> 类。</span><span class="sxs-lookup"><span data-stu-id="5902d-111">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="5902d-112">要创建待序列化的类，请使用 XML 架构定义工具。</span><span class="sxs-lookup"><span data-stu-id="5902d-112">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="5902d-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="5902d-113">See also</span></span>

- [<span data-ttu-id="5902d-114">二进制序列化</span><span class="sxs-lookup"><span data-stu-id="5902d-114">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="5902d-115">[使用 ASP.NET 创建的 XML Web service 以及 XML Web Service 客户端](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5902d-115">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
