---
title: 序列化 (C#)
description: 序列化将对象转换成字节流，以存储对象或将对象传输到内存、数据库或文件。
ms.date: 01/02/2020
ms.openlocfilehash: 29625648b19c97556c107997ef9ecd3f0f971cbf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455745"
---
# <a name="serialization-c"></a><span data-ttu-id="c8fa2-103">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="c8fa2-103">Serialization (C#)</span></span>

<span data-ttu-id="c8fa2-104">序列化是指将对象转换成字节流，从而存储对象或将对象传输到内存、数据库或文件的过程。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-104">Serialization is the process of converting an object into a stream of bytes to store the object or transmit it to memory, a database, or a file.</span></span> <span data-ttu-id="c8fa2-105">它的主要用途是保存对象的状态，以便能够在需要时重新创建对象。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-105">Its main purpose is to save the state of an object in order to be able to recreate it when needed.</span></span> <span data-ttu-id="c8fa2-106">反向过程称为“反序列化”。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-106">The reverse process is called deserialization.</span></span>

## <a name="how-serialization-works"></a><span data-ttu-id="c8fa2-107">序列化的工作原理</span><span class="sxs-lookup"><span data-stu-id="c8fa2-107">How serialization works</span></span>

<span data-ttu-id="c8fa2-108">下图展示了序列化的整个过程：</span><span class="sxs-lookup"><span data-stu-id="c8fa2-108">This illustration shows the overall process of serialization:</span></span>

![图：序列化](./media/index/serialization-process.gif)

<span data-ttu-id="c8fa2-110">将对象序列化为带有数据的流。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-110">The object is serialized to a stream that carries the data.</span></span> <span data-ttu-id="c8fa2-111">该流还可能包含有关对象类型的信息，例如其版本、区域性和程序集名称。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-111">The stream may also have information about the object's type, such as its version, culture, and assembly name.</span></span> <span data-ttu-id="c8fa2-112">可以将此流中的对象存储在数据库、文件或内存中。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-112">From that stream, the object can be stored in a database, a file, or memory.</span></span>

### <a name="uses-for-serialization"></a><span data-ttu-id="c8fa2-113">序列化的用途</span><span class="sxs-lookup"><span data-stu-id="c8fa2-113">Uses for serialization</span></span>

<span data-ttu-id="c8fa2-114">通过序列化，开发人员可以保存对象的状态，并能在需要时重新创建对象，同时还能存储对象和交换数据。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-114">Serialization allows the developer to save the state of an object and re-create it as needed, providing storage of objects as well as data exchange.</span></span> <span data-ttu-id="c8fa2-115">通过序列化，开发人员可以执行如下操作：</span><span class="sxs-lookup"><span data-stu-id="c8fa2-115">Through serialization, a developer can perform actions such as:</span></span>

* <span data-ttu-id="c8fa2-116">使用 Web 服务将对象发送到远程应用程序</span><span class="sxs-lookup"><span data-stu-id="c8fa2-116">Sending the object to a remote application by using a web service</span></span>
* <span data-ttu-id="c8fa2-117">将对象从一个域传递到另一个域</span><span class="sxs-lookup"><span data-stu-id="c8fa2-117">Passing an object from one domain to another</span></span>
* <span data-ttu-id="c8fa2-118">将对象通过防火墙传递为 JSON 或 XML 字符串</span><span class="sxs-lookup"><span data-stu-id="c8fa2-118">Passing an object through a firewall as a JSON or XML string</span></span>
* <span data-ttu-id="c8fa2-119">跨应用程序维护安全或用户特定的信息</span><span class="sxs-lookup"><span data-stu-id="c8fa2-119">Maintaining security or user-specific information across applications</span></span>

## <a name="json-serialization"></a><span data-ttu-id="c8fa2-120">JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="c8fa2-120">JSON serialization</span></span>

<span data-ttu-id="c8fa2-121"><xref:System.Text.Json> 命名空间包含用于 JavaScript 对象表示法 (JSON) 序列化和反序列化的类。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-121">The <xref:System.Text.Json> namespace contains classes for JavaScript Object Notation (JSON) serialization and deserialization.</span></span> <span data-ttu-id="c8fa2-122">JSON 是一种常用于在 Web 上共享数据的开放标准。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-122">JSON is an open standard that is commonly used for sharing data across the web.</span></span>

<span data-ttu-id="c8fa2-123">JSON 序列化将对象的公共属性序列化为符合 [RFC 8259 JSON 规范](https://tools.ietf.org/html/rfc8259)的字符串、字节数组或流。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-123">JSON serialization serializes the public properties of an object into a string, byte array, or stream that conforms to [the RFC 8259 JSON specification](https://tools.ietf.org/html/rfc8259).</span></span> <span data-ttu-id="c8fa2-124">若要控制 <xref:System.Text.Json.JsonSerializer> 对类的实例进行序列化或反序列化的方法，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c8fa2-124">To control the way <xref:System.Text.Json.JsonSerializer> serializes or deserializes an instance of the class:</span></span>

* <span data-ttu-id="c8fa2-125">使用 <xref:System.Text.Json.JsonSerializerOptions> 对象</span><span class="sxs-lookup"><span data-stu-id="c8fa2-125">Use a <xref:System.Text.Json.JsonSerializerOptions> object</span></span>
* <span data-ttu-id="c8fa2-126">将 <xref:System.Text.Json.Serialization> 命名空间中的特性应用于类或属性</span><span class="sxs-lookup"><span data-stu-id="c8fa2-126">Apply attributes from the <xref:System.Text.Json.Serialization> namespace to classes or properties</span></span>
* [<span data-ttu-id="c8fa2-127">实现自定义转换器</span><span class="sxs-lookup"><span data-stu-id="c8fa2-127">Implement custom converters</span></span>](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a><span data-ttu-id="c8fa2-128">二进制和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="c8fa2-128">Binary and XML serialization</span></span>

<span data-ttu-id="c8fa2-129"><xref:System.Runtime.Serialization> 命名空间包含用于对二进制和 XML 进行序列化和反序列化的类。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-129">The <xref:System.Runtime.Serialization> namespace contains classes for binary and XML serialization and deserialization.</span></span>

<span data-ttu-id="c8fa2-130">二进制序列化使用二进制编码来生成精简的序列化以供使用，如基于存储或套接字的网络流。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-130">Binary serialization uses binary encoding to produce compact serialization for uses such as storage or socket-based network streams.</span></span> <span data-ttu-id="c8fa2-131">在二进制序列化中，所有成员（包括只读成员）都会被序列化，且性能也会有所提升。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-131">In binary serialization, all members, even members that are read-only, are serialized, and performance is enhanced.</span></span>

[!INCLUDE [binary-serialization-warning](~/includes/binary-serialization-warning.md)]

<span data-ttu-id="c8fa2-132">XML 序列化将对象的公共字段和属性或方法的参数和返回值序列化成符合特定 XML 架构定义语言 (XSD) 文档要求的 XML 流。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-132">XML serialization serializes the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="c8fa2-133">XML 序列化生成已转换成 XML 的强类型类，其中包含公共属性和字段。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-133">XML serialization results in strongly typed classes with public properties and fields that are converted to XML.</span></span> <span data-ttu-id="c8fa2-134"><xref:System.Xml.Serialization> 包含用于对 XML 进行序列化和反序列化的类。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-134"><xref:System.Xml.Serialization> contains classes for serializing and deserializing XML.</span></span> <span data-ttu-id="c8fa2-135">将特性应用于类和类成员，从而控制 <xref:System.Xml.Serialization.XmlSerializer> 如何序列化或反序列化类的实例。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-135">You apply attributes to classes and class members to control the way the <xref:System.Xml.Serialization.XmlSerializer> serializes or deserializes an instance of the class.</span></span>

### <a name="making-an-object-serializable"></a><span data-ttu-id="c8fa2-136">让对象可序列化</span><span class="sxs-lookup"><span data-stu-id="c8fa2-136">Making an object serializable</span></span>

<span data-ttu-id="c8fa2-137">若要对二进制或 XML 进行序列化，你需要：</span><span class="sxs-lookup"><span data-stu-id="c8fa2-137">For binary or XML serialization, you need:</span></span>

* <span data-ttu-id="c8fa2-138">要序列化的对象</span><span class="sxs-lookup"><span data-stu-id="c8fa2-138">The object to be serialized</span></span>
* <span data-ttu-id="c8fa2-139">包含序列化对象的流</span><span class="sxs-lookup"><span data-stu-id="c8fa2-139">A stream to contain the serialized object</span></span>
* <span data-ttu-id="c8fa2-140">一个 <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> 实例</span><span class="sxs-lookup"><span data-stu-id="c8fa2-140">A <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> instance</span></span>

<span data-ttu-id="c8fa2-141">将 <xref:System.SerializableAttribute> 特性应用于某个类型，以指示可对此类型进行序列化的实例。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-141">Apply the <xref:System.SerializableAttribute> attribute to a type to indicate that instances of the type can be serialized.</span></span> <span data-ttu-id="c8fa2-142">如果尝试对没有 <xref:System.SerializableAttribute> 特性的类型进行序列化，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-142">An  exception is thrown if you attempt to serialize but the type doesn't have the <xref:System.SerializableAttribute> attribute.</span></span>

<span data-ttu-id="c8fa2-143">若要防止对字段进行序列化，请应用 <xref:System.NonSerializedAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-143">To prevent a field from being serialized, apply the <xref:System.NonSerializedAttribute> attribute.</span></span> <span data-ttu-id="c8fa2-144">如果可序列化的类型中的一个字段包含指针、句柄或特定环境专用的其他一些数据结构，且不能在其他环境中有意义地重构，不妨让其不可序列化。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-144">If a field of a serializable type contains a pointer, a handle, or some other data structure that is specific to a particular environment, and the field cannot be meaningfully reconstituted in a different environment, then you may want to make it nonserializable.</span></span>

<span data-ttu-id="c8fa2-145">如果已序列化的类引用被标记为 <xref:System.SerializableAttribute> 的其他类的对象，那么这些对象也会被序列化。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-145">If a serialized class contains references to objects of other classes that are marked <xref:System.SerializableAttribute>, those objects will also be serialized.</span></span>

### <a name="basic-and-custom-serialization"></a><span data-ttu-id="c8fa2-146">基本和自定义序列化</span><span class="sxs-lookup"><span data-stu-id="c8fa2-146">Basic and custom serialization</span></span>

<span data-ttu-id="c8fa2-147">可以使用两种方法对二进制和 XML 进行序列化：基本和自定义。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-147">Binary and XML serialization can be performed in two ways, basic and custom.</span></span>

<span data-ttu-id="c8fa2-148">基本序列化使用 .NET 自动序列化对象。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-148">Basic serialization uses .NET to automatically serialize the object.</span></span> <span data-ttu-id="c8fa2-149">唯一的要求是类应用 <xref:System.SerializableAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-149">The only requirement is that the class has the <xref:System.SerializableAttribute> attribute applied.</span></span> <span data-ttu-id="c8fa2-150"><xref:System.NonSerializedAttribute> 可用于防止特定字段被序列化。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-150">The <xref:System.NonSerializedAttribute> can be used to keep specific fields from being serialized.</span></span>

<span data-ttu-id="c8fa2-151">使用基本序列化时，对象的版本控制可能会产生问题。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-151">When you use basic serialization, the versioning of objects may create problems.</span></span> <span data-ttu-id="c8fa2-152">对于重要的版本控制问题，可以使用自定义序列化。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-152">You would use custom serialization when versioning issues are important.</span></span> <span data-ttu-id="c8fa2-153">基本序列化是最简单的序列化执行方式，但无法提供太多的进程控制。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-153">Basic serialization is the easiest way to perform serialization, but it does not provide much control over the process.</span></span>

<span data-ttu-id="c8fa2-154">在自定义序列化中，可以精确指定要序列化的对象以及具体执行方式。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-154">In custom serialization, you can specify exactly which objects will be serialized and how it will be done.</span></span> <span data-ttu-id="c8fa2-155">类必须被标记为 <xref:System.SerializableAttribute>，并实现 <xref:System.Runtime.Serialization.ISerializable> 接口。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-155">The class must be marked <xref:System.SerializableAttribute> and implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="c8fa2-156">如果还希望按自定义方式反序列化对象，请使用自定义构造函数。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-156">If you want your object to be deserialized in a custom manner as well, use a custom constructor.</span></span>

## <a name="designer-serialization"></a><span data-ttu-id="c8fa2-157">设计器序列化</span><span class="sxs-lookup"><span data-stu-id="c8fa2-157">Designer serialization</span></span>

<span data-ttu-id="c8fa2-158">设计器序列化是一种特殊形式的序列化，涉及与开发工具相关联的对象暂留。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-158">Designer serialization is a special form of serialization that involves the kind of object persistence associated with development tools.</span></span> <span data-ttu-id="c8fa2-159">设计器序列化是指将对象图转换成源文件以供日后用于恢复对象图的过程。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-159">Designer serialization is the process of converting an object graph into a source file that can later be used to recover the object graph.</span></span> <span data-ttu-id="c8fa2-160">源文件可以包含代码、标记或 SQL 表信息。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-160">A source file can contain code, markup, or even SQL table information.</span></span>

## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a><span data-ttu-id="c8fa2-161">相关主题和示例</span><span class="sxs-lookup"><span data-stu-id="c8fa2-161">Related Topics and Examples</span></span>  

<span data-ttu-id="c8fa2-162">[System.Text.Json 概述](../../../../standard/serialization/system-text-json-overview.md) 演示如何获取 `System.Text.Json` 库。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-162">[System.Text.Json overview](../../../../standard/serialization/system-text-json-overview.md) Shows how to get the `System.Text.Json` library.</span></span>

<span data-ttu-id="c8fa2-163">[如何在 .NET 中对 JSON 数据进行序列化和反序列化](../../../../standard/serialization/system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-163">[How to serialize and deserialize JSON in .NET](../../../../standard/serialization/system-text-json-how-to.md).</span></span>
<span data-ttu-id="c8fa2-164">演示如何使用 <xref:System.Text.Json.JsonSerializer> 类在 JSON 之间读取和写入对象数据。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-164">Shows how to read and write object data to and from JSON using the <xref:System.Text.Json.JsonSerializer> class.</span></span>

[<span data-ttu-id="c8fa2-165">演练：在 Visual Basic 中保持对象 (C#)</span><span class="sxs-lookup"><span data-stu-id="c8fa2-165">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>](walkthrough-persisting-an-object-in-visual-studio.md)  
<span data-ttu-id="c8fa2-166">展示了如何使用序列化在实例之间暂留对象数据，以便可以存储值并在下次实例化对象时检索值。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-166">Demonstrates how serialization can be used to persist an object's data between instances, allowing you to store values and retrieve them the next time the object is instantiated.</span></span>

[<span data-ttu-id="c8fa2-167">如何从 XML 文件读取对象数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="c8fa2-167">How to read object data from an XML file (C#)</span></span>](how-to-read-object-data-from-an-xml-file.md)  
<span data-ttu-id="c8fa2-168">介绍如何使用 <xref:System.Xml.Serialization.XmlSerializer> 类读取之前写入 XML 文件的对象数据。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-168">Shows how to read object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>

[<span data-ttu-id="c8fa2-169">如何将对象数据写入 XML 文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="c8fa2-169">How to write object data to an XML file (C#)</span></span>](how-to-write-object-data-to-an-xml-file.md)  
<span data-ttu-id="c8fa2-170">介绍如何使用 <xref:System.Xml.Serialization.XmlSerializer> 类从某个类将对象写入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c8fa2-170">Shows how to write the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>
