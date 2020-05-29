---
title: 如何使用 XmlSerializer 反序列化对象
description: 了解如何反序列化对象。 传输格式决定着是创建流还是文件对象。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e08ae0d77539219223650fd3bcbd1bcee4df2739
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379114"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="be2f0-104">如何使用 XmlSerializer 反序列化对象</span><span class="sxs-lookup"><span data-stu-id="be2f0-104">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="be2f0-105">当您反序列化对象时，传输格式确定您将创建流还是文件对象。</span><span class="sxs-lookup"><span data-stu-id="be2f0-105">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="be2f0-106">确定了传输格式之后，就可以根据需要调用 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 或 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="be2f0-106">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="be2f0-107">反序列化对象</span><span class="sxs-lookup"><span data-stu-id="be2f0-107">To deserialize an object</span></span>

1. <span data-ttu-id="be2f0-108">使用要反序列化的对象的类型构造 <xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="be2f0-108">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="be2f0-109">调用 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法以生成该对象的副本。</span><span class="sxs-lookup"><span data-stu-id="be2f0-109">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="be2f0-110">在反序列化时，必须将返回的对象强制转换为原始对象的类型，如以下示例所示，该示例从文件反序列化该对象（尽管也可以从流反序列化该对象）。</span><span class="sxs-lookup"><span data-stu-id="be2f0-110">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a><span data-ttu-id="be2f0-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="be2f0-111">See also</span></span>

- [<span data-ttu-id="be2f0-112">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="be2f0-112">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="be2f0-113">如何：序列化对象</span><span class="sxs-lookup"><span data-stu-id="be2f0-113">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
