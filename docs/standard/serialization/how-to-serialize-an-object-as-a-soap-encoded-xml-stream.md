---
title: 如何：将对象序列化为 SOAP 编码的 XML 流
description: 了解如何将对象序列化为 SOAP 编码的 XML 流。 XmlSerializer 类可用于序列化类和生成编码的 SOAP 消息。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: 1d38c4e334439ef41b4d4429e52cff04c6463573
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "84291560"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="dcc41-104">如何：将对象序列化为 SOAP 编码的 XML 流</span><span class="sxs-lookup"><span data-stu-id="dcc41-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="dcc41-105">由于 SOAP 消息是使用 XML 生成的，因此 <xref:System.Xml.Serialization.XmlSerializer> 类可用于序列化类和生成编码的 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="dcc41-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="dcc41-106">生成的 XML 符合[万维网联合会文档“简单对象访问协议 (SOAP) 1.1”的第 5 节](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)。</span><span class="sxs-lookup"><span data-stu-id="dcc41-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="dcc41-107">如果您要创建通过 SOAP 消息进行通信的 XML Web services，则可以将一组特殊的 SOAP 属性应用于类和类的成员来自定义 XML 流。</span><span class="sxs-lookup"><span data-stu-id="dcc41-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="dcc41-108">有关属性列表，请参阅[控制编码的 SOAP 序列化的特性](attributes-that-control-encoded-soap-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc41-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="dcc41-109">将对象序列化为 SOAP 编码的 XML 流</span><span class="sxs-lookup"><span data-stu-id="dcc41-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="dcc41-110">使用 [XML 架构定义工具 (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md) 创建类。</span><span class="sxs-lookup"><span data-stu-id="dcc41-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="dcc41-111">应用在 `System.Xml.Serialization` 中找到的一个或多个特殊属性。</span><span class="sxs-lookup"><span data-stu-id="dcc41-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="dcc41-112">请参见“用来控制编码的 SOAP 序列化的属性”中的列表。</span><span class="sxs-lookup"><span data-stu-id="dcc41-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="dcc41-113">通过创建新的 `XmlTypeMapping`，然后用已序列化类的类型调用 `SoapReflectionImporter` 方法，来创建 `ImportTypeMapping`。</span><span class="sxs-lookup"><span data-stu-id="dcc41-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="dcc41-114">以下代码示例调用 `SoapReflectionImporter` 类的 `ImportTypeMapping` 方法来创建 `XmlTypeMapping`。</span><span class="sxs-lookup"><span data-stu-id="dcc41-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4. <span data-ttu-id="dcc41-115">通过将 `XmlSerializer` 传递给 `XmlTypeMapping` 构造函数，来创建 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dcc41-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="dcc41-116">调用 `Serialize` 或 `Deserialize` 方法。</span><span class="sxs-lookup"><span data-stu-id="dcc41-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcc41-117">示例</span><span class="sxs-lookup"><span data-stu-id="dcc41-117">Example</span></span>  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcc41-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="dcc41-118">See also</span></span>

- [<span data-ttu-id="dcc41-119">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="dcc41-119">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="dcc41-120">用来控制编码的 SOAP 序列化的属性</span><span class="sxs-lookup"><span data-stu-id="dcc41-120">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="dcc41-121">使用 XML Web services 进行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="dcc41-121">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="dcc41-122">如何：序列化对象</span><span class="sxs-lookup"><span data-stu-id="dcc41-122">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="dcc41-123">如何：反序列化对象</span><span class="sxs-lookup"><span data-stu-id="dcc41-123">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="dcc41-124">如何：替代编码的 SOAP XML 序列化</span><span class="sxs-lookup"><span data-stu-id="dcc41-124">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
