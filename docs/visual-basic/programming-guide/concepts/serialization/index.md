---
title: 序列化
ms.date: 07/20/2015
ms.assetid: 67379a76-5465-4af8-a781-0b0b25a62d9a
ms.openlocfilehash: 98400c9e7ed9e26a9dc6ca548988c3691bfecdc2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086499"
---
# <a name="serialization-visual-basic"></a><span data-ttu-id="a5221-102">序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5221-102">Serialization (Visual Basic)</span></span>

<span data-ttu-id="a5221-103">序列化是指将对象转换成字节流，从而存储对象或将对象传输到内存、数据库或文件的过程。</span><span class="sxs-lookup"><span data-stu-id="a5221-103">Serialization is the process of converting an object into a stream of bytes in order to store the object or transmit it to memory, a database, or a file.</span></span> <span data-ttu-id="a5221-104">它的主要用途是保存对象的状态，以便能够在需要时重新创建对象。</span><span class="sxs-lookup"><span data-stu-id="a5221-104">Its main purpose is to save the state of an object in order to be able to recreate it when needed.</span></span> <span data-ttu-id="a5221-105">反向过程称为“反序列化”。</span><span class="sxs-lookup"><span data-stu-id="a5221-105">The reverse process is called deserialization.</span></span>  
  
## <a name="how-serialization-works"></a><span data-ttu-id="a5221-106">序列化的工作原理</span><span class="sxs-lookup"><span data-stu-id="a5221-106">How Serialization Works</span></span>  

 <span data-ttu-id="a5221-107">下图展示了序列化的整个过程。</span><span class="sxs-lookup"><span data-stu-id="a5221-107">This illustration shows the overall process of serialization.</span></span>  
  
![图：序列化](./media/index/serialization-process.gif)
  
 <span data-ttu-id="a5221-109">对象被序列化成流，其中不仅包含数据，还包含对象类型的相关信息，如版本、区域性和程序集名称。</span><span class="sxs-lookup"><span data-stu-id="a5221-109">The object is serialized to a stream, which carries not just the data, but information about the object's type, such as its version, culture, and assembly name.</span></span> <span data-ttu-id="a5221-110">可以将此流中的内容存储在数据库、文件或内存中。</span><span class="sxs-lookup"><span data-stu-id="a5221-110">From that stream, it can be stored in a database, a file, or memory.</span></span>  
  
### <a name="uses-for-serialization"></a><span data-ttu-id="a5221-111">序列化的用途</span><span class="sxs-lookup"><span data-stu-id="a5221-111">Uses for Serialization</span></span>  

 <span data-ttu-id="a5221-112">借助序列化，开发者可以保存对象的状态，并能在需要时重新创建对象，同时还能存储对象和交换数据。</span><span class="sxs-lookup"><span data-stu-id="a5221-112">Serialization allows the developer to save the state of an object and recreate it as needed, providing storage of objects as well as data exchange.</span></span> <span data-ttu-id="a5221-113">通过序列化，开发者可以执行如下操作：通过 Web 服务将对象发送到远程应用程序、在域之间传递对象、以 XML 字符串的形式传递对象通过防火墙、跨应用程序维护安全性或用户专属信息。</span><span class="sxs-lookup"><span data-stu-id="a5221-113">Through serialization, a developer can perform actions like sending the object to a remote application by means of a Web Service, passing an object from one domain to another, passing an object through a firewall as an XML string, or maintaining security or user-specific information across applications.</span></span>  
  
### <a name="making-an-object-serializable"></a><span data-ttu-id="a5221-114">让对象可序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-114">Making an Object Serializable</span></span>  

 <span data-ttu-id="a5221-115">若要序列化对象，需要具有要序列化的对象、包含已序列化对象的一个流，以及一个 <xref:System.Runtime.Serialization.Formatter>。</span><span class="sxs-lookup"><span data-stu-id="a5221-115">To serialize an object, you need the object to be serialized, a stream to contain the serialized object, and a <xref:System.Runtime.Serialization.Formatter>.</span></span> <span data-ttu-id="a5221-116"><xref:System.Runtime.Serialization> 包含序列化和反序列化对象所必需的类。</span><span class="sxs-lookup"><span data-stu-id="a5221-116"><xref:System.Runtime.Serialization> contains the classes necessary for serializing and deserializing objects.</span></span>  
  
 <span data-ttu-id="a5221-117">将 <xref:System.SerializableAttribute> 特性应用于某个类型，以指示此类型的实例可以被序列化。</span><span class="sxs-lookup"><span data-stu-id="a5221-117">Apply the <xref:System.SerializableAttribute> attribute to a type to indicate that instances of this type can be serialized.</span></span> <span data-ttu-id="a5221-118">如果尝试对没有 <xref:System.SerializableAttribute> 特性的类型进行序列化，则会引发 <xref:System.Runtime.Serialization.SerializationException> 异常。</span><span class="sxs-lookup"><span data-stu-id="a5221-118">A <xref:System.Runtime.Serialization.SerializationException> exception is thrown if you attempt to serialize but the type does not have the <xref:System.SerializableAttribute> attribute.</span></span>  
  
 <span data-ttu-id="a5221-119">如果想让类中的某个字段不可序列化，请应用 <xref:System.NonSerializedAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="a5221-119">If you do not want a field within your class to be serializable, apply the <xref:System.NonSerializedAttribute> attribute.</span></span> <span data-ttu-id="a5221-120">如果可序列化的类型中的一个字段包含指针、句柄或特定环境专用的其他一些数据结构，且不能在其他环境中有意义地重构，不妨让其不可序列化。</span><span class="sxs-lookup"><span data-stu-id="a5221-120">If a field of a serializable type contains a pointer, a handle, or some other data structure that is specific to a particular environment, and the field cannot be meaningfully reconstituted in a different environment, then you may want to make it nonserializable.</span></span>  
  
 <span data-ttu-id="a5221-121">如果已序列化的类引用被标记为 <xref:System.SerializableAttribute> 的其他类的对象，那么这些对象也会被序列化。</span><span class="sxs-lookup"><span data-stu-id="a5221-121">If a serialized class contains references to objects of other classes that are marked <xref:System.SerializableAttribute>, those objects will also be serialized.</span></span>  
  
## <a name="binary-and-xml-serialization"></a><span data-ttu-id="a5221-122">二进制和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-122">Binary and XML Serialization</span></span>  

 <span data-ttu-id="a5221-123">二进制或 XML 序列化均可使用。</span><span class="sxs-lookup"><span data-stu-id="a5221-123">Either binary or XML serialization can be used.</span></span> <span data-ttu-id="a5221-124">在二进制序列化中，所有成员（包括只读成员）都会被序列化，且性能也会有所提升。</span><span class="sxs-lookup"><span data-stu-id="a5221-124">In binary serialization, all members, even those that are read-only, are serialized, and performance is enhanced.</span></span> <span data-ttu-id="a5221-125">XML 序列化可提高代码可读性，以及对象共享和使用的灵活性，从而实现互操作性。</span><span class="sxs-lookup"><span data-stu-id="a5221-125">XML serialization provides more readable code, as well as greater flexibility of object sharing and usage for interoperability purposes.</span></span>  
  
### <a name="binary-serialization"></a><span data-ttu-id="a5221-126">二进制序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-126">Binary Serialization</span></span>  

 <span data-ttu-id="a5221-127">二进制序列化使用二进制编码来生成精简的序列化以供使用，如基于存储或套接字的网络流。</span><span class="sxs-lookup"><span data-stu-id="a5221-127">Binary serialization uses binary encoding to produce compact serialization for uses such as storage or socket-based network streams.</span></span>  
  
### <a name="xml-serialization"></a><span data-ttu-id="a5221-128">XML 序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-128">XML Serialization</span></span>  

 <span data-ttu-id="a5221-129">XML 序列化将对象的公共字段和属性或方法的参数和返回值序列化成符合特定 XML 架构定义语言 (XSD) 文档要求的 XML 流。</span><span class="sxs-lookup"><span data-stu-id="a5221-129">XML serialization serializes the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="a5221-130">XML 序列化生成已转换成 XML 的强类型类，其中包含公共属性和字段。</span><span class="sxs-lookup"><span data-stu-id="a5221-130">XML serialization results in strongly typed classes with public properties and fields that are converted to XML.</span></span> <span data-ttu-id="a5221-131"><xref:System.Xml.Serialization> 包含序列化和反序列化 XML 所必需的类。</span><span class="sxs-lookup"><span data-stu-id="a5221-131"><xref:System.Xml.Serialization> contains the classes necessary for serializing and deserializing XML.</span></span>  
  
 <span data-ttu-id="a5221-132">可以将特性应用于类和类成员，从而控制 <xref:System.Xml.Serialization.XmlSerializer> 如何序列化或反序列化类的实例。</span><span class="sxs-lookup"><span data-stu-id="a5221-132">You can apply attributes to classes and class members in order to control the way the <xref:System.Xml.Serialization.XmlSerializer> serializes or deserializes an instance of the class.</span></span>  
  
## <a name="basic-and-custom-serialization"></a><span data-ttu-id="a5221-133">基本和自定义序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-133">Basic and Custom Serialization</span></span>  

 <span data-ttu-id="a5221-134">序列化有两种执行方式：基本和自定义序列化。</span><span class="sxs-lookup"><span data-stu-id="a5221-134">Serialization can be performed in two ways, basic and custom.</span></span> <span data-ttu-id="a5221-135">基本序列化使用 .NET Framework 自动序列化对象。</span><span class="sxs-lookup"><span data-stu-id="a5221-135">Basic serialization uses the .NET Framework to automatically serialize the object.</span></span>  
  
### <a name="basic-serialization"></a><span data-ttu-id="a5221-136">基本序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-136">Basic Serialization</span></span>  

 <span data-ttu-id="a5221-137">基本序列化的唯一要求是对象必须已应用 <xref:System.SerializableAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="a5221-137">The only requirement in basic serialization is that the object has the <xref:System.SerializableAttribute> attribute applied.</span></span> <span data-ttu-id="a5221-138"><xref:System.NonSerializedAttribute> 可用于防止特定字段被序列化。</span><span class="sxs-lookup"><span data-stu-id="a5221-138">The <xref:System.NonSerializedAttribute> can be used to keep specific fields from being serialized.</span></span>  
  
 <span data-ttu-id="a5221-139">使用基本序列化时，对象的版本控制可能会导致问题出现，在这种情况下，最好使用自定义序列化。</span><span class="sxs-lookup"><span data-stu-id="a5221-139">When you use basic serialization, the versioning of objects may create problems, in which case custom serialization may be preferable.</span></span> <span data-ttu-id="a5221-140">基本序列化是最简单的序列化执行方式，但无法提供太多的进程控制。</span><span class="sxs-lookup"><span data-stu-id="a5221-140">Basic serialization is the easiest way to perform serialization, but it does not provide much control over the process.</span></span>  
  
### <a name="custom-serialization"></a><span data-ttu-id="a5221-141">自定义序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-141">Custom Serialization</span></span>  

 <span data-ttu-id="a5221-142">在自定义序列化中，可以精确指定要序列化的对象以及具体执行方式。</span><span class="sxs-lookup"><span data-stu-id="a5221-142">In custom serialization, you can specify exactly which objects will be serialized and how it will be done.</span></span> <span data-ttu-id="a5221-143">类必须被标记为 <xref:System.SerializableAttribute>，并实现 <xref:System.Runtime.Serialization.ISerializable> 接口。</span><span class="sxs-lookup"><span data-stu-id="a5221-143">The class must be marked <xref:System.SerializableAttribute> and implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="a5221-144">如果还想按自定义方式反序列化对象，必须使用自定义构造函数。</span><span class="sxs-lookup"><span data-stu-id="a5221-144">If you want your object to be deserialized in a custom manner as well, you must use a custom constructor.</span></span>  
  
## <a name="designer-serialization"></a><span data-ttu-id="a5221-145">设计器序列化</span><span class="sxs-lookup"><span data-stu-id="a5221-145">Designer Serialization</span></span>  

 <span data-ttu-id="a5221-146">设计器序列化是一种特殊形式的序列化，涉及通常与开发工具相关联的对象暂留。</span><span class="sxs-lookup"><span data-stu-id="a5221-146">Designer serialization is a special form of serialization that involves the kind of object persistence usually associated with development tools.</span></span> <span data-ttu-id="a5221-147">设计器序列化是指将对象图转换成源文件以供日后用于恢复对象图的过程。</span><span class="sxs-lookup"><span data-stu-id="a5221-147">Designer serialization is the process of converting an object graph into a source file that can later be used to recover the object graph.</span></span> <span data-ttu-id="a5221-148">源文件可以包含代码、标记或 SQL 表信息。</span><span class="sxs-lookup"><span data-stu-id="a5221-148">A source file can contain code, markup, or even SQL table information.</span></span>  
  
## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a><span data-ttu-id="a5221-149">相关主题和示例</span><span class="sxs-lookup"><span data-stu-id="a5221-149">Related Topics and Examples</span></span>  

 [<span data-ttu-id="a5221-150">演练：在 Visual Studio 中暂留对象 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5221-150">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>](walkthrough-persisting-an-object-in-visual-studio.md)  
 <span data-ttu-id="a5221-151">展示了如何使用序列化在实例之间暂留对象数据，以便可以存储值并在下次实例化对象时检索值。</span><span class="sxs-lookup"><span data-stu-id="a5221-151">Demonstrates how serialization can be used to persist an object's data between instances, allowing you to store values and retrieve them the next time the object is instantiated.</span></span>  
  
 [<span data-ttu-id="a5221-152">如何：读取 XML 文件中的对象数据 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5221-152">How to: Read Object Data from an XML File (Visual Basic)</span></span>](how-to-read-object-data-from-an-xml-file.md)  
 <span data-ttu-id="a5221-153">介绍如何使用 <xref:System.Xml.Serialization.XmlSerializer> 类读取之前写入 XML 文件的对象数据。</span><span class="sxs-lookup"><span data-stu-id="a5221-153">Shows how to read object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
 [<span data-ttu-id="a5221-154">如何：将对象数据写入 XML 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5221-154">How to: Write Object Data to an XML File (Visual Basic)</span></span>](how-to-write-object-data-to-an-xml-file.md)  
 <span data-ttu-id="a5221-155">介绍如何使用 <xref:System.Xml.Serialization.XmlSerializer> 类从某个类将对象写入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a5221-155">Shows how to write the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>
