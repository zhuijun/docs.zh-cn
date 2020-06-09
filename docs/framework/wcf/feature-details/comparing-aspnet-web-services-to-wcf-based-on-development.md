---
title: 从开发的角度比较 ASP.NET Web 服务与 WCF
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: c6e83bb234751dc477776f0fa540ffa8688dc667
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597587"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="fc073-102">从开发的角度比较 ASP.NET Web 服务与 WCF</span><span class="sxs-lookup"><span data-stu-id="fc073-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="fc073-103">Windows Communication Foundation （WCF）具有 ASP.NET 兼容模式选项，可对 WCF 应用程序进行编程和配置（如 ASP.NET Web 服务）并模拟它们的行为。</span><span class="sxs-lookup"><span data-stu-id="fc073-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="fc073-104">以下各节基于使用这两种技术开发应用程序所需的内容，对 ASP.NET Web 服务和 WCF 进行比较。</span><span class="sxs-lookup"><span data-stu-id="fc073-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="fc073-105">数据表示形式</span><span class="sxs-lookup"><span data-stu-id="fc073-105">Data Representation</span></span>

<span data-ttu-id="fc073-106">一般情况下，使用 ASP.NET 开发 Web 服务首先要定义服务要使用的任意复杂数据类型。</span><span class="sxs-lookup"><span data-stu-id="fc073-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="fc073-107">ASP.NET 依赖于 <xref:System.Xml.Serialization.XmlSerializer> 将由 .NET Framework 类型表示的数据转换为 XML，以便与服务进行相互传输并将以 XML 形式接收的数据转换为 .NET Framework 对象。</span><span class="sxs-lookup"><span data-stu-id="fc073-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="fc073-108">定义 ASP.NET 服务要使用的复杂数据类型需要使用 .NET Framework 类的定义，这些类可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化为 XML 或从 XML 进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="fc073-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="fc073-109">这些类可以手动编写，或者使用命令行 XML 架构/数据类型支持实用工具 xsd.exe 从 XML 架构中的类型定义生成。</span><span class="sxs-lookup"><span data-stu-id="fc073-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="fc073-110">下面是定义可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化为 XML 或从 XML 序列化的 .NET Framework 类时需要了解的关键问题列表：</span><span class="sxs-lookup"><span data-stu-id="fc073-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="fc073-111">只有 .NET Framework 对象的公共字段和属性才能转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="fc073-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="fc073-112">仅当集合类实现 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.ICollection> 接口时才能将集合类的实例序列化为 XML。</span><span class="sxs-lookup"><span data-stu-id="fc073-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="fc073-113">实现 <xref:System.Collections.IDictionary> 接口的类，如 <xref:System.Collections.Hashtable>，不能序列化为 XML。</span><span class="sxs-lookup"><span data-stu-id="fc073-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="fc073-114"><xref:System.Xml.Serialization> 命名空间中的许多属性类型均可添加到 .NET Framework 类及其成员中，用于控制类实例的 XML 表示方式。</span><span class="sxs-lookup"><span data-stu-id="fc073-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="fc073-115">WCF 应用程序开发通常也以复杂类型的定义开始。</span><span class="sxs-lookup"><span data-stu-id="fc073-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="fc073-116">可以使用 WCF 与 ASP.NET Web 服务使用相同的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="fc073-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="fc073-117">WCF <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 可以添加到 .NET Framework 类型，以指示要将类型的实例序列化为 XML，并对类型的哪些特定字段或属性进行序列化，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="fc073-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<span data-ttu-id="fc073-118"><xref:System.Runtime.Serialization.DataContractAttribute> 表示要对零个或多个类型字段或属性进行序列化，而 <xref:System.Runtime.Serialization.DataMemberAttribute> 表示要对某个特定字段或属性进行序列化。</span><span class="sxs-lookup"><span data-stu-id="fc073-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="fc073-119"><xref:System.Runtime.Serialization.DataContractAttribute> 可应用于类或结构。</span><span class="sxs-lookup"><span data-stu-id="fc073-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="fc073-120"><xref:System.Runtime.Serialization.DataMemberAttribute> 可以应用于字段或属性 (Property)，对其应用此属性 (Attribute) 的字段和属性 (Property) 既可以是公共的也可以是私有的。</span><span class="sxs-lookup"><span data-stu-id="fc073-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="fc073-121">应用了的类型的实例在 <xref:System.Runtime.Serialization.DataContractAttribute> WCF 中称为数据协定。</span><span class="sxs-lookup"><span data-stu-id="fc073-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="fc073-122">它们通过 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化为 XML。</span><span class="sxs-lookup"><span data-stu-id="fc073-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="fc073-123">下面是使用 <xref:System.Runtime.Serialization.DataContractSerializer> 和使用 <xref:System.Xml.Serialization.XmlSerializer> 以及 <xref:System.Xml.Serialization> 命名空间的各种属性之间的重大差异列表。</span><span class="sxs-lookup"><span data-stu-id="fc073-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="fc073-124"><xref:System.Xml.Serialization.XmlSerializer> 和 <xref:System.Xml.Serialization> 命名空间的属性旨在让您可以将 .NET Framework 类型映射为在 XML 架构中定义的任意有效类型，因此它们对类型如何以 XML 方式表示提供了十分精确的控制。</span><span class="sxs-lookup"><span data-stu-id="fc073-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="fc073-125"><xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 则几乎不对类型如何以 XML 方式表示提供控制。</span><span class="sxs-lookup"><span data-stu-id="fc073-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="fc073-126">您只能指定用于在 XML 中表示类型及其字段或属性的命名空间和名称，以及字段和属性在 XML 中的显示顺序：</span><span class="sxs-lookup"><span data-stu-id="fc073-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  <span data-ttu-id="fc073-127">任何其他与用于表示 .NET 类型的 XML 结构相关的数据均由 <xref:System.Runtime.Serialization.DataContractSerializer> 确定。</span><span class="sxs-lookup"><span data-stu-id="fc073-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="fc073-128">通过不允许过多地控制如何以 XML 方式表示类型，<xref:System.Runtime.Serialization.DataContractSerializer> 序列化过程的可预知程度变得很高，因此，更容易实现优化。</span><span class="sxs-lookup"><span data-stu-id="fc073-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="fc073-129"><xref:System.Runtime.Serialization.DataContractSerializer> 设计的一个实用优势是它具有更好的性能，大约提高了 10%。</span><span class="sxs-lookup"><span data-stu-id="fc073-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="fc073-130">用于 <xref:System.Xml.Serialization.XmlSerializer> 的属性 (Attribute) 并不指明此类型的哪些字段或属性 (Property) 将序列化为 XML，而用于 <xref:System.Runtime.Serialization.DataMemberAttribute> 的 <xref:System.Runtime.Serialization.DataContractSerializer> 则显式指明将对哪些字段或属性 (Property) 执行序列化。</span><span class="sxs-lookup"><span data-stu-id="fc073-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="fc073-131">因此，数据协定是与应用程序所要发送和接收的数据的结构有关的显式协定。</span><span class="sxs-lookup"><span data-stu-id="fc073-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="fc073-132"><xref:System.Xml.Serialization.XmlSerializer> 只能将 .NET 对象的公共成员转换为 XML；而无论对象成员的访问修饰符如何，<xref:System.Runtime.Serialization.DataContractSerializer> 都可以将这些成员转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="fc073-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="fc073-133">由于可将各种类型的非公共成员序列化为 XML，因此，<xref:System.Runtime.Serialization.DataContractSerializer> 对于可序列化为 XML 的 .NET 类型的多样性限制较少。</span><span class="sxs-lookup"><span data-stu-id="fc073-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="fc073-134">尤其是，它可以转换为 XML 类型，如实现 <xref:System.Collections.Hashtable> 接口的 <xref:System.Collections.IDictionary>。</span><span class="sxs-lookup"><span data-stu-id="fc073-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="fc073-135"><xref:System.Runtime.Serialization.DataContractSerializer> 更有可能会将任意预先存在的 .NET 类型序列化为 XML 而无需修改类型的定义或开发类型的包装。</span><span class="sxs-lookup"><span data-stu-id="fc073-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="fc073-136">由于 <xref:System.Runtime.Serialization.DataContractSerializer> 可以访问类型的非公共成员，因此，它还要求完全信任，而 <xref:System.Xml.Serialization.XmlSerializer> 不要求。</span><span class="sxs-lookup"><span data-stu-id="fc073-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="fc073-137">完全信任代码访问权限提供对计算机上的所有资源的完全访问权限，可以使用执行代码的凭据访问该计算机上的所有资源。</span><span class="sxs-lookup"><span data-stu-id="fc073-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="fc073-138">当完全受信任的代码访问计算机上的所有资源时，应谨慎使用此选项。</span><span class="sxs-lookup"><span data-stu-id="fc073-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="fc073-139"><xref:System.Runtime.Serialization.DataContractSerializer> 中集成了一些对版本管理的支持：</span><span class="sxs-lookup"><span data-stu-id="fc073-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="fc073-140"><xref:System.Runtime.Serialization.DataMemberAttribute> 具有一个 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 属性，将它赋予 False 值可指示早期版本中不存在将成员添加到的新版本数据协定，因此使得包含新版协定的应用程序可以处理早期的版本。</span><span class="sxs-lookup"><span data-stu-id="fc073-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="fc073-141">通过让某个数据协定实现 <xref:System.Runtime.Serialization.IExtensibleDataObject> 接口，使得 <xref:System.Runtime.Serialization.DataContractSerializer> 可通过包含早期版本协定的应用程序传递新版数据协定中定义的成员。</span><span class="sxs-lookup"><span data-stu-id="fc073-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="fc073-142">不管存在何种差异，只要 XML 具有显式定义的命名空间，默认情况下，<xref:System.Xml.Serialization.XmlSerializer> 将类型序列化为的 XML 与 <xref:System.Runtime.Serialization.DataContractSerializer> 将类型序列化为的 XML 语义相同。</span><span class="sxs-lookup"><span data-stu-id="fc073-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="fc073-143">下面的类具有与这两个序列化程序一起使用的特性，由和转换为语义上完全相同的 XML <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> ：</span><span class="sxs-lookup"><span data-stu-id="fc073-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

<span data-ttu-id="fc073-144">Windows 软件开发工具包（SDK）包含一个名为 "Svcutil.exe" 的[元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)的命令行工具。</span><span class="sxs-lookup"><span data-stu-id="fc073-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="fc073-145">与用于 ASP.NET Web 服务的 xsd.exe 工具一样，Svcutil.exe 可以从 XML 架构生成 .NET 数据类型的定义。</span><span class="sxs-lookup"><span data-stu-id="fc073-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="fc073-146">如果 <xref:System.Runtime.Serialization.DataContractSerializer> 可发出由 XML 架构定义的格式的 XML，类型将为数据协定；否则，它们专用于通过 <xref:System.Xml.Serialization.XmlSerializer> 进行序列化。</span><span class="sxs-lookup"><span data-stu-id="fc073-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fc073-147">Svcutil.exe 还可以通过使用数据协定的开关从数据协定生成 XML 架构 `dataContractOnly` 。</span><span class="sxs-lookup"><span data-stu-id="fc073-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="fc073-148">尽管 ASP.NET Web 服务使用 <xref:System.Xml.Serialization.XmlSerializer> ，并且 wcf ASP.NET 兼容模式使 wcf 服务能够模仿 ASP.NET Web 服务的行为，但 ASP.NET 兼容性选项不会限制一个使用 <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="fc073-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fc073-149">用户仍然可以将 <xref:System.Runtime.Serialization.DataContractSerializer> 用于以 ASP.NET 兼容模式运行的服务。</span><span class="sxs-lookup"><span data-stu-id="fc073-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="fc073-150">服务开发</span><span class="sxs-lookup"><span data-stu-id="fc073-150">Service Development</span></span>

<span data-ttu-id="fc073-151">要使用 ASP.NET 开发服务，通常会将 <xref:System.Web.Services.WebService> 属性添加到类中，并将 <xref:System.Web.Services.WebMethodAttribute> 添加到该类中将作为服务操作使用的任意方法上：</span><span class="sxs-lookup"><span data-stu-id="fc073-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="fc073-152">ASP.NET 2.0 中引入了将属性 <xref:System.Web.Services.WebService> 和 <xref:System.Web.Services.WebMethodAttribute> 添加到接口（而不是类）的选项，并编写了一个类实现此接口：</span><span class="sxs-lookup"><span data-stu-id="fc073-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

<span data-ttu-id="fc073-153">使用此选项是首选方法，因为具有 <xref:System.Web.Services.WebService> 属性的接口包含服务所执行操作的协定，该服务可以在通过多种不同方式实现同一协定的各种类中重复使用。</span><span class="sxs-lookup"><span data-stu-id="fc073-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="fc073-154">WCF 服务通过定义一个或多个 WCF 端点提供。</span><span class="sxs-lookup"><span data-stu-id="fc073-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="fc073-155">终结点由地址、绑定和服务协定定义。</span><span class="sxs-lookup"><span data-stu-id="fc073-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="fc073-156">地址用于定义服务的位置。</span><span class="sxs-lookup"><span data-stu-id="fc073-156">The address defines where the service is located.</span></span> <span data-ttu-id="fc073-157">绑定用于指定与服务的通信方式。</span><span class="sxs-lookup"><span data-stu-id="fc073-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="fc073-158">服务协定用于定义服务可执行的操作。</span><span class="sxs-lookup"><span data-stu-id="fc073-158">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="fc073-159">通常最先定义服务协定，通过将 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 添加到接口中实现：</span><span class="sxs-lookup"><span data-stu-id="fc073-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="fc073-160"><xref:System.ServiceModel.ServiceContractAttribute>指定接口定义 WCF 服务协定，并 <xref:System.ServiceModel.OperationContractAttribute> 指示接口的哪些方法（如果有）定义服务协定的操作。</span><span class="sxs-lookup"><span data-stu-id="fc073-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="fc073-161">定义服务协定后，它将在类中实现，方法是使类实现服务协定定义的接口：</span><span class="sxs-lookup"><span data-stu-id="fc073-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="fc073-162">在 WCF 中，实现服务协定的类称为 "服务类型"。</span><span class="sxs-lookup"><span data-stu-id="fc073-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="fc073-163">下一步是将地址和绑定与服务类型关联。</span><span class="sxs-lookup"><span data-stu-id="fc073-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="fc073-164">通常通过直接编辑文件或使用 WCF 提供的配置编辑器在配置文件中完成此操作。</span><span class="sxs-lookup"><span data-stu-id="fc073-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="fc073-165">下面是配置文件的示例。</span><span class="sxs-lookup"><span data-stu-id="fc073-165">Here is an example of a configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

<span data-ttu-id="fc073-166">绑定指定用于与应用程序通信的协议集。</span><span class="sxs-lookup"><span data-stu-id="fc073-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="fc073-167">下表列出由系统提供的表示常用选项的绑定。</span><span class="sxs-lookup"><span data-stu-id="fc073-167">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="fc073-168">名称</span><span class="sxs-lookup"><span data-stu-id="fc073-168">Name</span></span>|<span data-ttu-id="fc073-169">目的</span><span class="sxs-lookup"><span data-stu-id="fc073-169">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="fc073-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-170">BasicHttpBinding</span></span>|<span data-ttu-id="fc073-171">可以与支持 WS-BasicProfile 1.1 和 Basic Security Profile 1.0 的 Web 服务和客户端相互操作。</span><span class="sxs-lookup"><span data-stu-id="fc073-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="fc073-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-172">WSHttpBinding</span></span>|<span data-ttu-id="fc073-173">可以与通过 HTTP 支持 WS\* 协议的 Web 服务和客户端相互操作。</span><span class="sxs-lookup"><span data-stu-id="fc073-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="fc073-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-174">WSDualHttpBinding</span></span>|<span data-ttu-id="fc073-175">双向 HTTP 通信，使用此绑定时初始消息的接收方不直接回复初始发送方，而是在一段时间内使用与 WS\* 协议一致的 HTTP 传输任意数量的响应。</span><span class="sxs-lookup"><span data-stu-id="fc073-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="fc073-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-176">WSFederationBinding</span></span>|<span data-ttu-id="fc073-177">访问服务资源时所用的 HTTP 通信可根据由显式标识的凭据提供程序发出的凭据进行控制。</span><span class="sxs-lookup"><span data-stu-id="fc073-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="fc073-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-178">NetTcpBinding</span></span>|<span data-ttu-id="fc073-179">跨网络在 WCF 软件实体之间进行安全、可靠、高性能的通信。</span><span class="sxs-lookup"><span data-stu-id="fc073-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="fc073-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="fc073-181">同一台计算机上 WCF 软件实体之间的安全、可靠、高性能的通信。</span><span class="sxs-lookup"><span data-stu-id="fc073-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="fc073-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-182">NetMsmqBinding</span></span>|<span data-ttu-id="fc073-183">使用 MSMQ 在 WCF 软件实体之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="fc073-183">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="fc073-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="fc073-185">使用 MSMQ 在 WCF 软件实体与其他软件实体之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="fc073-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="fc073-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="fc073-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="fc073-187">使用 Windows 对等网络建立 WCF 软件实体之间的通信。</span><span class="sxs-lookup"><span data-stu-id="fc073-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="fc073-188">系统提供的绑定 <xref:System.ServiceModel.BasicHttpBinding> 集成了 ASP.NET Web 服务支持的协议集。</span><span class="sxs-lookup"><span data-stu-id="fc073-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="fc073-189">WCF 应用程序的自定义绑定可以轻松定义为 WCF 用于实现各个协议的绑定元素类的集合。</span><span class="sxs-lookup"><span data-stu-id="fc073-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="fc073-190">可以将新的绑定元素编写为表示其他协议。</span><span class="sxs-lookup"><span data-stu-id="fc073-190">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="fc073-191">服务类型的内部行为可以使用一系列称为行为的类的属性对其进行调整。</span><span class="sxs-lookup"><span data-stu-id="fc073-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="fc073-192">其中，<xref:System.ServiceModel.ServiceBehaviorAttribute> 类用于指定服务类型为多线程。</span><span class="sxs-lookup"><span data-stu-id="fc073-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="fc073-193">某些行为是属性，如 <xref:System.ServiceModel.ServiceBehaviorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="fc073-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="fc073-194">其他具有管理员希望设置的属性的行为可以在配置应用程序时修改。</span><span class="sxs-lookup"><span data-stu-id="fc073-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="fc073-195">在编程服务类型中，通常使用 <xref:System.ServiceModel.OperationContext> 类。</span><span class="sxs-lookup"><span data-stu-id="fc073-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="fc073-196">它的静态 <xref:System.ServiceModel.OperationContext.Current%2A> 属性提供对有关运行操作上下文的信息的访问权限。</span><span class="sxs-lookup"><span data-stu-id="fc073-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="fc073-197"><xref:System.ServiceModel.OperationContext> 类似于 <xref:System.Web.HttpContext> 和 <xref:System.EnterpriseServices.ContextUtil> 类。</span><span class="sxs-lookup"><span data-stu-id="fc073-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="fc073-198">Hosting</span><span class="sxs-lookup"><span data-stu-id="fc073-198">Hosting</span></span>

<span data-ttu-id="fc073-199">ASP.NET Web 服务编译为类库程序集。</span><span class="sxs-lookup"><span data-stu-id="fc073-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="fc073-200">将提供一个称为服务文件且扩展名为 .asmx 的文件，该文件包含一条 `@ WebService` 指令，该指令标识的类包含表示服务和服务所在程序集的代码。</span><span class="sxs-lookup"><span data-stu-id="fc073-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

<span data-ttu-id="fc073-201">在 Internet 信息服务 (IIS) 中，服务文件将复制到 ASP.NET 应用程序根目录下，程序集则复制到此应用程序根目录的 \bin 子目录下。</span><span class="sxs-lookup"><span data-stu-id="fc073-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="fc073-202">然后，您可以在应用程序根目录下使用服务文件的统一资源定位符 (URL) 访问此应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc073-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="fc073-203">WCF 服务可随时在 IIS 5.1 或6.0 中托管，Windows 进程激活服务（WAS）作为 IIS 7.0 的一部分提供，并且在任何 .NET 应用程序中提供。</span><span class="sxs-lookup"><span data-stu-id="fc073-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="fc073-204">若要在 IIS 5.1 或 6.0 中承载某项服务，此服务必须使用 HTTP 作为通信传输协议。</span><span class="sxs-lookup"><span data-stu-id="fc073-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="fc073-205">若要在 IIS 5.1、6.0 或 WAS 中承载某项服务，请使用下列步骤：</span><span class="sxs-lookup"><span data-stu-id="fc073-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="fc073-206">将此服务类型编译为类库程序集。</span><span class="sxs-lookup"><span data-stu-id="fc073-206">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="fc073-207">使用标识服务类型的 `@ ServiceHost` 指令创建一个扩展名为 .svc 的服务文件：</span><span class="sxs-lookup"><span data-stu-id="fc073-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. <span data-ttu-id="fc073-208">将服务文件复制到虚拟目录下，并将程序集复制到该虚拟目录的 \bin 子目录下。</span><span class="sxs-lookup"><span data-stu-id="fc073-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="fc073-209">将配置文件复制到虚拟目录下，并将其命名为 Web.config。</span><span class="sxs-lookup"><span data-stu-id="fc073-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="fc073-210">然后，您可以在应用程序根目录下使用服务文件的 URL 访问此应用程序</span><span class="sxs-lookup"><span data-stu-id="fc073-210">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="fc073-211">若要在 .NET 应用程序中托管 WCF 服务，请将服务类型编译为该应用程序引用的类库程序集，并对该应用程序进行编程以使用类承载服务 <xref:System.ServiceModel.ServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="fc073-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="fc073-212">下面是所需基本编程的示例：</span><span class="sxs-lookup"><span data-stu-id="fc073-212">The following is an example of the basic programming required:</span></span>

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

<span data-ttu-id="fc073-213">此示例演示如何在构造 <xref:System.ServiceModel.ServiceHost> 时指定一个或多个传输协议的地址。</span><span class="sxs-lookup"><span data-stu-id="fc073-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="fc073-214">这些地址称为基址。</span><span class="sxs-lookup"><span data-stu-id="fc073-214">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="fc073-215">为 WCF 服务的任何终结点提供的地址是相对于终结点主机的基址的地址。</span><span class="sxs-lookup"><span data-stu-id="fc073-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="fc073-216">对于每个通信传输协议，宿主都可以有一个基址。</span><span class="sxs-lookup"><span data-stu-id="fc073-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="fc073-217">在上面的配置文件配置示例中，为终结点选定的 <xref:System.ServiceModel.BasicHttpBinding> 将 HTTP 用作传输协议，因此终结点的地址 `EchoService` 与宿主的 HTTP 基址相关。</span><span class="sxs-lookup"><span data-stu-id="fc073-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="fc073-218">对于前面的示例中的主机，HTTP 基址为 `http://www.contoso.com:8000/` 。</span><span class="sxs-lookup"><span data-stu-id="fc073-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="fc073-219">对于在 IIS 或 WAS 中承载的服务，其基址为服务的服务文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="fc073-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="fc073-220">只能使用在 IIS 或 WAS 中承载的服务，以及仅使用 HTTP 作为传输协议进行配置的服务，才能使用 WCF ASP.NET 兼容模式选项。</span><span class="sxs-lookup"><span data-stu-id="fc073-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="fc073-221">启用此选项需要执行下列步骤。</span><span class="sxs-lookup"><span data-stu-id="fc073-221">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="fc073-222">程序员必须将 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 属性添加到服务类型中，并指定是允许还是需要 ASP.NET 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="fc073-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="fc073-223">管理员必须将应用程序配置为使用 ASP.NET 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="fc073-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="fc073-224">WCF 应用程序也可以配置为使用 .asmx 作为其服务文件（而不是 .svc）的扩展。</span><span class="sxs-lookup"><span data-stu-id="fc073-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    <span data-ttu-id="fc073-225">使用此选项，你无需修改在将服务修改为使用 WCF 时配置为使用 .asmx 服务文件的 Url 的客户端。</span><span class="sxs-lookup"><span data-stu-id="fc073-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="fc073-226">客户端开发</span><span class="sxs-lookup"><span data-stu-id="fc073-226">Client Development</span></span>

<span data-ttu-id="fc073-227">ASP.NET Web 服务的客户端通过使用命令行工具 WSDL.exe 生成，该工具可将 .asmx 文件的 URL 作为输入提供。</span><span class="sxs-lookup"><span data-stu-id="fc073-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="fc073-228">WCF 提供的相应工具为 " [Svcutil.exe 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)"。</span><span class="sxs-lookup"><span data-stu-id="fc073-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="fc073-229">它使用服务协定的定义和 WCF 客户端类的定义生成代码模块。</span><span class="sxs-lookup"><span data-stu-id="fc073-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="fc073-230">它还使用服务的地址和绑定生成一个配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc073-230">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="fc073-231">通常，建议您基于异步模式对远程服务的客户端进行编程。</span><span class="sxs-lookup"><span data-stu-id="fc073-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="fc073-232">默认情况下，不论是同步模式还是异步模式，始终都会提供由 WSDL.exe 工具生成的代码。</span><span class="sxs-lookup"><span data-stu-id="fc073-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="fc073-233">可为任一模式提供 " [svcutil.exe" 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)生成的代码。</span><span class="sxs-lookup"><span data-stu-id="fc073-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="fc073-234">默认为对同步模式提供。</span><span class="sxs-lookup"><span data-stu-id="fc073-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="fc073-235">如果执行该工具时使用 `/async` 开关，则将为异步模式提供生成的代码。</span><span class="sxs-lookup"><span data-stu-id="fc073-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="fc073-236">不保证 ASP.NET 生成的 WCF 客户端类中的名称。默认情况下，NET 的 WSDL.EXE 工具与 Svcutil.exe 工具生成的 WCF 客户端类中的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="fc073-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="fc073-237">尤其是，在默认情况下，必须使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化的类的属性名将在 Svcutil.exe 工具生成的代码中获得后缀 Property，这与 WSDL.exe 工具的情况并不一样。</span><span class="sxs-lookup"><span data-stu-id="fc073-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="fc073-238">消息表示形式</span><span class="sxs-lookup"><span data-stu-id="fc073-238">Message Representation</span></span>

<span data-ttu-id="fc073-239">可以对由 ASP.NET Web 服务发送和接收的 SOAP 消息头执行自定义操作。</span><span class="sxs-lookup"><span data-stu-id="fc073-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="fc073-240">将从 <xref:System.Web.Services.Protocols.SoapHeader> 派生一个类，用于定义消息头的结构，然后 <xref:System.Web.Services.Protocols.SoapHeaderAttribute> 用于指示存在消息头。</span><span class="sxs-lookup"><span data-stu-id="fc073-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

<span data-ttu-id="fc073-241">WCF 提供属性、、 <xref:System.ServiceModel.MessageContractAttribute> 和， <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> 以描述服务发送和接收的 SOAP 消息的结构。</span><span class="sxs-lookup"><span data-stu-id="fc073-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

<span data-ttu-id="fc073-242">此语法将生成消息结构的显式表示形式，同时 ASP.NET Web 服务的代码也将暗示消息结构。</span><span class="sxs-lookup"><span data-stu-id="fc073-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="fc073-243">此外，在 ASP.NET 语法中，消息头表示为服务的属性，例如 `ProtocolHeader` 上一示例中的属性，而在 WCF 语法中，它们可以更准确地表示为消息的属性。</span><span class="sxs-lookup"><span data-stu-id="fc073-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="fc073-244">同时，WCF 还允许将消息标头添加到终结点的配置中。</span><span class="sxs-lookup"><span data-stu-id="fc073-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

<span data-ttu-id="fc073-245">使用此选项，可以在客户端或服务的代码中避免任何对基础协议标头的引用：标头将根据终结点的配置方式添加到消息中。</span><span class="sxs-lookup"><span data-stu-id="fc073-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="fc073-246">服务说明</span><span class="sxs-lookup"><span data-stu-id="fc073-246">Service Description</span></span>

<span data-ttu-id="fc073-247">使用查询 WSDL 对 ASP.NET Web 服务的 .asmx 文件发出 HTTP GET 请求将使 ASP.NET 生成描述服务的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="fc073-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="fc073-248">ASP.NET 将返回该 WSDL 作为此请求的响应。</span><span class="sxs-lookup"><span data-stu-id="fc073-248">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="fc073-249">通过 ASP.NET 2.0，用户可以验证服务是否与 Web 服务互操作性组织 (WS-I) 的基本配置文件 1.1 兼容，还可以插入一个声明表明服务与其 WSDL 兼容。</span><span class="sxs-lookup"><span data-stu-id="fc073-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="fc073-250">这可以通过使用 `ConformsTo` 属性的 `EmitConformanceClaims` 和 <xref:System.Web.Services.WebServiceBindingAttribute> 参数实现。</span><span class="sxs-lookup"><span data-stu-id="fc073-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="fc073-251">可以自定义 ASP.NET 为服务生成的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="fc073-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="fc073-252">通过创建 <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> 的派生类以将项目添加到 WSDL 中可实现自定义。</span><span class="sxs-lookup"><span data-stu-id="fc073-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="fc073-253">使用在 IIS 51、6.0 或中承载的 HTTP 终结点的 WCF 服务的 .svc 文件的查询 WSDL 发出 HTTP GET 请求会导致 WCF 使用 WSDL 进行响应，以描述该服务。</span><span class="sxs-lookup"><span data-stu-id="fc073-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="fc073-254">如果 httpGetEnabled 设置为 true，则使用查询 WSDL 对 .NET 应用程序所承载服务的 HTTP 基址发出 HTTP GET 请求具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="fc073-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="fc073-255">但是，WCF 还会使用其生成的用于描述服务的 WSDL 响应 Ws-metadataexchange 请求。</span><span class="sxs-lookup"><span data-stu-id="fc073-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="fc073-256">ASP.NET Web 服务没有对 WS-MetadataExchange 请求的内置支持。</span><span class="sxs-lookup"><span data-stu-id="fc073-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="fc073-257">WCF 生成的 WSDL 可以广泛地自定义。</span><span class="sxs-lookup"><span data-stu-id="fc073-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="fc073-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> 类提供了一些用于自定义 WSDL 的功能。</span><span class="sxs-lookup"><span data-stu-id="fc073-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="fc073-259">也可以将 WCF 配置为不生成 WSDL，而是使用给定 URL 处的静态 WSDL 文件。</span><span class="sxs-lookup"><span data-stu-id="fc073-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a><span data-ttu-id="fc073-260">异常处理</span><span class="sxs-lookup"><span data-stu-id="fc073-260">Exception Handling</span></span>

<span data-ttu-id="fc073-261">在 ASP.NET Web 服务中，未处理的异常将作为 SOAP 错误返回客户端。</span><span class="sxs-lookup"><span data-stu-id="fc073-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="fc073-262">您还可以显式抛出 <xref:System.Web.Services.Protocols.SoapException> 类的实例并对传输到客户端的 SOAP 错误内容加大控制力度。</span><span class="sxs-lookup"><span data-stu-id="fc073-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="fc073-263">在 WCF 服务中，未处理的异常不会作为 SOAP 错误返回到客户端，以防止无意中通过异常公开敏感信息。</span><span class="sxs-lookup"><span data-stu-id="fc073-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="fc073-264">为了进行调试，系统将提供一个配置设置以将未处理的异常返回客户端。</span><span class="sxs-lookup"><span data-stu-id="fc073-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="fc073-265">若要将 SOAP 错误返回客户端，您可以使用数据协定类型作为泛型类型抛出泛型类型的实例 <xref:System.ServiceModel.FaultException%601>。</span><span class="sxs-lookup"><span data-stu-id="fc073-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="fc073-266">您还可以将 <xref:System.ServiceModel.FaultContractAttribute> 属性添加到操作中以指定操作可能会生成的错误。</span><span class="sxs-lookup"><span data-stu-id="fc073-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

<span data-ttu-id="fc073-267">这样做会导致在服务的 WSDL 中显示对可能错误的建议，从而使客户端程序员可以预计操作可能会导致哪些错误，并编写相应的 Catch 语句。</span><span class="sxs-lookup"><span data-stu-id="fc073-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a><span data-ttu-id="fc073-268">状态管理</span><span class="sxs-lookup"><span data-stu-id="fc073-268">State Management</span></span>

<span data-ttu-id="fc073-269">用于实现 ASP.NET Web 服务的类可以从 <xref:System.Web.Services.WebService> 派生。</span><span class="sxs-lookup"><span data-stu-id="fc073-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="fc073-270">在此情况下，可以将此类编程为使用 <xref:System.Web.Services.WebService> 基类的“上下文”属性访问 <xref:System.Web.HttpContext> 对象。</span><span class="sxs-lookup"><span data-stu-id="fc073-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="fc073-271">通过使用 <xref:System.Web.HttpContext> 对象的 Application 属性，该对象可用于更新和检索应用程序状态信息，而且通过使用其 Session 属性，该对象可用于更新和检索会话状态信息。</span><span class="sxs-lookup"><span data-stu-id="fc073-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="fc073-272">ASP.NET 通过使用实际存储着 <xref:System.Web.HttpContext> 的 Session 属性对会话状态信息的访问位置提供高度控制。</span><span class="sxs-lookup"><span data-stu-id="fc073-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="fc073-273">它可以存储在 Cookie、数据库、当前服务器的内存或指定服务器的内存中。</span><span class="sxs-lookup"><span data-stu-id="fc073-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="fc073-274">在服务的配置文件中做出此项选择。</span><span class="sxs-lookup"><span data-stu-id="fc073-274">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="fc073-275">WCF 为状态管理提供可扩展对象。</span><span class="sxs-lookup"><span data-stu-id="fc073-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="fc073-276">可扩展对象就是实现 <xref:System.ServiceModel.IExtensibleObject%601> 的对象。</span><span class="sxs-lookup"><span data-stu-id="fc073-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="fc073-277">最重要的可扩展对象为 <xref:System.ServiceModel.ServiceHostBase> 和 <xref:System.ServiceModel.InstanceContext>。</span><span class="sxs-lookup"><span data-stu-id="fc073-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="fc073-278">`ServiceHostBase` 允许你保持同一个主机上所有服务类型的所有实例都可访问的状态，而 `InstanceContext` 允许你保持可以被某个服务类型的同一个实例中运行的任意代码访问的状态。</span><span class="sxs-lookup"><span data-stu-id="fc073-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="fc073-279">在此，服务类型 `TradingSystem` 具有一个， <xref:System.ServiceModel.ServiceBehaviorAttribute> 它指定从同一 WCF 客户端实例进行的所有调用都路由到服务类型的同一个实例。</span><span class="sxs-lookup"><span data-stu-id="fc073-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="fc073-280">`DealData` 类用于定义可以由某个服务类型的相同实例中运行的任意代码访问的状态。</span><span class="sxs-lookup"><span data-stu-id="fc073-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="fc073-281">在实现服务协定中任一操作的服务类型的代码中，将 `DealData` 状态对象添加到当前服务类型实例的状态中。</span><span class="sxs-lookup"><span data-stu-id="fc073-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="fc073-282">随后，可以使用实现另一个服务协定操作的代码检索和修改此状态对象。</span><span class="sxs-lookup"><span data-stu-id="fc073-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="fc073-283">尽管 ASP.NET 提供了对类中状态信息的 <xref:System.Web.HttpContext> 实际存储位置的控制，但 WCF 至少在其初始版本中不提供对存储可扩展对象的位置的控制。</span><span class="sxs-lookup"><span data-stu-id="fc073-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="fc073-284">这构成了为 WCF 服务选择 ASP.NET 兼容模式的最佳理由。</span><span class="sxs-lookup"><span data-stu-id="fc073-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="fc073-285">如果必须管理可配置状态，则选择 ASP.NET 兼容模式使您可以按照它们在 ASP.NET 中的使用方式使用 <xref:System.Web.HttpContext> 类的功能，而且还可以通过使用存储的 <xref:System.Web.HttpContext> 类配置状态信息的管理位置。</span><span class="sxs-lookup"><span data-stu-id="fc073-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="fc073-286">安全性</span><span class="sxs-lookup"><span data-stu-id="fc073-286">Security</span></span>

<span data-ttu-id="fc073-287">用于保证 ASP.NET Web 服务安全的选项就是那些用于保证任意 IIS 应用程序安全的选项。</span><span class="sxs-lookup"><span data-stu-id="fc073-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="fc073-288">因为 WCF 应用程序不仅可以在 IIS 中托管，也可以在任何 .NET 可执行文件中托管，所以用于保护 WCF 应用程序的选项必须与 IIS 的功能无关。</span><span class="sxs-lookup"><span data-stu-id="fc073-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="fc073-289">但是，为 ASP.NET Web 服务提供的功能也可用于在 ASP.NET 兼容模式下运行的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="fc073-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="fc073-290">安全性：身份验证</span><span class="sxs-lookup"><span data-stu-id="fc073-290">Security: Authentication</span></span>

<span data-ttu-id="fc073-291">IIS 可提供对应用程序的访问进行控制的功能，您可以使用此功能选择匿名访问或各种身份验证模式：Windows 身份验证、摘要式身份验证、基本身份验证和 .NET Passport 身份验证。</span><span class="sxs-lookup"><span data-stu-id="fc073-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="fc073-292">Windows 身份验证选项可以用于控制对 ASP.NET Web 服务的访问。</span><span class="sxs-lookup"><span data-stu-id="fc073-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="fc073-293">但是，当 WCF 应用程序承载于 IIS 中时，必须将 IIS 配置为允许对应用程序进行匿名访问，以便 WCF 本身可以管理身份验证，这在不同的选项之间支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="fc073-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="fc073-294">其他内置选项包括用户名令牌、X.509 证书、SAML 令牌和 CardSpace 卡，但是也可以定义自定义身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="fc073-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="fc073-295">安全性：模拟</span><span class="sxs-lookup"><span data-stu-id="fc073-295">Security: Impersonation</span></span>

<span data-ttu-id="fc073-296">ASP.NET 提供一个标识元素，ASP.NET Web 服务可通过使用该元素模拟当前请求提供了某个特定用户或任何用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="fc073-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="fc073-297">该元素可用于在 ASP.NET 兼容模式下运行的 WCF 应用程序中配置模拟。</span><span class="sxs-lookup"><span data-stu-id="fc073-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="fc073-298">WCF 配置系统提供自己的标识元素，用于指定要模拟的特定用户。</span><span class="sxs-lookup"><span data-stu-id="fc073-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="fc073-299">另外，WCF 客户端和服务可以单独配置为进行模拟。</span><span class="sxs-lookup"><span data-stu-id="fc073-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="fc073-300">当客户端发送请求时，可将它们配置为模拟当前用户。</span><span class="sxs-lookup"><span data-stu-id="fc073-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="fc073-301">可将服务操作配置为模拟当前请求提供了任意用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="fc073-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="fc073-302">安全性：使用访问控制列表进行授权</span><span class="sxs-lookup"><span data-stu-id="fc073-302">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="fc073-303">访问控制列表 (ACL) 可用于限制对 .asmx 文件的访问。</span><span class="sxs-lookup"><span data-stu-id="fc073-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="fc073-304">但在 ASP.NET 兼容模式下，将忽略 WCF .svc 文件上的 Acl。</span><span class="sxs-lookup"><span data-stu-id="fc073-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="fc073-305">安全性：基于角色的授权</span><span class="sxs-lookup"><span data-stu-id="fc073-305">Security: Role-based Authorization</span></span>

<span data-ttu-id="fc073-306">IIS Windows 身份验证选项可与由 ASP.NET 配置语言提供的授权元素一起使用，以便根据将用户指定到的 Windows 组简化对 ASP.NET Web 服务的基于角色的授权。</span><span class="sxs-lookup"><span data-stu-id="fc073-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="fc073-307">ASP.NET 2.0 引入了一种更常用的基于角色的授权机制：角色提供程序。</span><span class="sxs-lookup"><span data-stu-id="fc073-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="fc073-308">角色提供程序就是所有实现基本接口以查询对用户分配哪些角色的类，但每个角色提供程序都知道如何从其他来源检索此信息。</span><span class="sxs-lookup"><span data-stu-id="fc073-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="fc073-309">ASP.NET 2.0 提供一个可从 Microsoft SQL Server 数据库检索角色分配的角色提供程序，同时还提供另一个可从 Windows Server 2003 授权管理器检索角色分配的角色提供程序。</span><span class="sxs-lookup"><span data-stu-id="fc073-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="fc073-310">在任何 .NET 应用程序（包括 WCF 应用程序）中，实际上可以独立于 ASP.NET 使用角色提供程序机制。</span><span class="sxs-lookup"><span data-stu-id="fc073-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="fc073-311">以下 WCF 应用程序示例配置演示了如何使用 ASP.NET 角色提供程序，这是一个通过的方法选择的选项 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 。</span><span class="sxs-lookup"><span data-stu-id="fc073-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a><span data-ttu-id="fc073-312">安全性：基于声明的授权</span><span class="sxs-lookup"><span data-stu-id="fc073-312">Security: Claims-based Authorization</span></span>

<span data-ttu-id="fc073-313">WCF 的最重要的一项创新是，它完全支持基于声明对受保护资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="fc073-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="fc073-314">声明包含类型、权限和值等，例如驾驶执照。</span><span class="sxs-lookup"><span data-stu-id="fc073-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="fc073-315">它提出一组有关持有人的声明，其中一个是持有人的出生日期。</span><span class="sxs-lookup"><span data-stu-id="fc073-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="fc073-316">此声明的类型为出生日期，而声明的值为司机的出生日期。</span><span class="sxs-lookup"><span data-stu-id="fc073-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="fc073-317">声明授予持有人的权限指定持有人可对声明的值执行的操作。</span><span class="sxs-lookup"><span data-stu-id="fc073-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="fc073-318">如果是要声明司机的出生日期，权限为拥有：司机拥有该出生日期但是不能更改它。</span><span class="sxs-lookup"><span data-stu-id="fc073-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="fc073-319">基于声明的授权包含基于角色的授权，因为角色也是一种声明类型。</span><span class="sxs-lookup"><span data-stu-id="fc073-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="fc073-320">基于声明的授权可通过将一组声明与操作的访问要求进行比较实现，根据比较的结果，可获得操作的访问权或遭到拒绝。</span><span class="sxs-lookup"><span data-stu-id="fc073-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="fc073-321">在 WCF 中，可以指定一个用于运行基于声明的授权的类，也可以通过为的属性赋值来指定一个值 `ServiceAuthorizationManager` <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 。</span><span class="sxs-lookup"><span data-stu-id="fc073-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="fc073-322">用于运行基于声明的授权的类必须派生自只有一种重写方法（即 <xref:System.ServiceModel.ServiceAuthorizationManager>）的 `AccessCheck()`。</span><span class="sxs-lookup"><span data-stu-id="fc073-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="fc073-323">每当调用服务的操作并提供对象时，WCF 都将调用该方法 <xref:System.ServiceModel.OperationContext> ，该对象在其属性中具有用户的声明 `ServiceSecurityContext.AuthorizationContext` 。</span><span class="sxs-lookup"><span data-stu-id="fc073-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="fc073-324">WCF 从用户提供的用于身份验证的任何安全令牌收集有关用户的声明的工作，这会使评估这些声明是否足以满足相关操作的任务。</span><span class="sxs-lookup"><span data-stu-id="fc073-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="fc073-325">WCF 自动将来自任何类型的安全令牌的声明组合在一起，这是一种高度重要的创新，因为它会根据声明完全独立于身份验证机制来授权代码。</span><span class="sxs-lookup"><span data-stu-id="fc073-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="fc073-326">与此相反，使用 ACL 或 ASP.NET 中的角色进行授权则与 Windows 身份验证息息相关。</span><span class="sxs-lookup"><span data-stu-id="fc073-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="fc073-327">安全性：机密性</span><span class="sxs-lookup"><span data-stu-id="fc073-327">Security: Confidentiality</span></span>

<span data-ttu-id="fc073-328">通过将 IIS 中的应用程序配置为使用安全超文本传输协议 (HTTPS)，可以在传输级别确保与 ASP.NET Web 服务交换的消息的机密性。</span><span class="sxs-lookup"><span data-stu-id="fc073-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="fc073-329">对于在 IIS 中承载的 WCF 应用程序也是如此。</span><span class="sxs-lookup"><span data-stu-id="fc073-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="fc073-330">但是，托管在 IIS 之外的 WCF 应用程序也可以配置为使用安全传输协议。</span><span class="sxs-lookup"><span data-stu-id="fc073-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="fc073-331">更重要的是，还可以使用 WS 安全协议将 WCF 应用程序配置为在传输消息之前对其进行保护。</span><span class="sxs-lookup"><span data-stu-id="fc073-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="fc073-332">如果使用 WS-Security 协议保护消息正文的安全，则消息正文到达最终目的地之前在中介中加密传输。</span><span class="sxs-lookup"><span data-stu-id="fc073-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="fc073-333">全球化</span><span class="sxs-lookup"><span data-stu-id="fc073-333">Globalization</span></span>

<span data-ttu-id="fc073-334">通过 ASP.NET 配置语言，您可以为这些服务单独指定区域性。</span><span class="sxs-lookup"><span data-stu-id="fc073-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="fc073-335">WCF 不支持 ASP.NET 兼容模式下的该配置设置。</span><span class="sxs-lookup"><span data-stu-id="fc073-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="fc073-336">若要本地化不使用 ASP.NET 兼容模式的 WCF 服务，请将服务类型编译为区域性特定的程序集，并为每个区域性特定的程序集提供单独的区域性特定的终结点。</span><span class="sxs-lookup"><span data-stu-id="fc073-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc073-337">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc073-337">See also</span></span>

- [<span data-ttu-id="fc073-338">基于目标和使用的标准比较 ASP.NET Web 服务与 WCF</span><span class="sxs-lookup"><span data-stu-id="fc073-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
