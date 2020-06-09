---
title: DataContract 代理项
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 9677e3cf024e6c1e5b2f3360423ab55536748495
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600031"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="f2677-102">DataContract 代理项</span><span class="sxs-lookup"><span data-stu-id="f2677-102">DataContract Surrogate</span></span>
<span data-ttu-id="f2677-103">本示例演示如何使用数据协定代理类自定义诸如序列化、反序列化、架构导出和架构导入之类的过程。</span><span class="sxs-lookup"><span data-stu-id="f2677-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="f2677-104">此示例演示如何在客户端和服务器方案（其中数据在 Windows Communication Foundation （WCF）客户端和服务之间进行序列化和传输）中使用代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2677-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="f2677-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f2677-106">此示例使用下面的服务协定：</span><span class="sxs-lookup"><span data-stu-id="f2677-106">The sample uses the following service contract:</span></span>  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 <span data-ttu-id="f2677-107">`AddEmployee` 操作允许用户添加有关新雇员的数据，`GetEmployee` 操作支持按姓名搜索雇员。</span><span class="sxs-lookup"><span data-stu-id="f2677-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="f2677-108">这些操作使用下面的数据类型：</span><span class="sxs-lookup"><span data-stu-id="f2677-108">These operations use the following data type:</span></span>  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 <span data-ttu-id="f2677-109">在 `Employee` 类型中，`Person` 类（显示在下面的示例代码中）不能由 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化，因为它不是有效的数据协定类。</span><span class="sxs-lookup"><span data-stu-id="f2677-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="f2677-110">可以将 <xref:System.Runtime.Serialization.DataContractAttribute> 属性应用于 `Person` 类，但不是始终都可以这样做。</span><span class="sxs-lookup"><span data-stu-id="f2677-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="f2677-111">例如，`Person` 类可能是在您无法控制的独立程序集中定义的。</span><span class="sxs-lookup"><span data-stu-id="f2677-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="f2677-112">在此限制下，序列化 `Person` 类的一种方式是用标记为 <xref:System.Runtime.Serialization.DataContractAttribute> 的另一个类替换此类并将必要数据复制到新类中。</span><span class="sxs-lookup"><span data-stu-id="f2677-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="f2677-113">目标是使 `Person` 类显示为 <xref:System.Runtime.Serialization.DataContractSerializer> 的 DataContract。</span><span class="sxs-lookup"><span data-stu-id="f2677-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="f2677-114">请注意，这是序列化非数据协定类的一种方式。</span><span class="sxs-lookup"><span data-stu-id="f2677-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="f2677-115">本示例通过逻辑方式用名为 `Person` 的另一个类替换 `PersonSurrogated` 类。</span><span class="sxs-lookup"><span data-stu-id="f2677-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 <span data-ttu-id="f2677-116">数据协定代理项用于实现此替换。</span><span class="sxs-lookup"><span data-stu-id="f2677-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="f2677-117">数据协定代理项是实现 <xref:System.Runtime.Serialization.IDataContractSurrogate> 的类。</span><span class="sxs-lookup"><span data-stu-id="f2677-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="f2677-118">在本示例中，`AllowNonSerializableTypesSurrogate` 类实现此接口。</span><span class="sxs-lookup"><span data-stu-id="f2677-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="f2677-119">在接口实现中，第一项任务是建立从 `Person` 到 `PersonSurrogated` 的类型映射。</span><span class="sxs-lookup"><span data-stu-id="f2677-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="f2677-120">序列化时和架构导出时都使用此映射。</span><span class="sxs-lookup"><span data-stu-id="f2677-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="f2677-121">此映射通过实现 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> 方法来实现。</span><span class="sxs-lookup"><span data-stu-id="f2677-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="f2677-122">在序列化过程中，<xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> 方法将 `Person` 实例映射到 `PersonSurrogated` 实例，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="f2677-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="f2677-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> 方法为反序列化提供反向映射，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="f2677-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="f2677-124">为了在架构导如过程中将 `PersonSurrogated` 数据协定映射到现有 `Person` 类，本示例实现 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> 方法，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="f2677-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 <span data-ttu-id="f2677-125">下面的示例代码完成 <xref:System.Runtime.Serialization.IDataContractSurrogate> 接口的实现。</span><span class="sxs-lookup"><span data-stu-id="f2677-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 <span data-ttu-id="f2677-126">在本示例中，由一个名为 `AllowNonSerializableTypesAttribute` 的属性在 ServiceModel 中启用该代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="f2677-127">开发人员需要在他们的服务协定上应用此属性，如上面的 `IPersonnelDataService` 服务协定所示。</span><span class="sxs-lookup"><span data-stu-id="f2677-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="f2677-128">此属性实现 `IContractBehavior` 并在其 `ApplyClientBehavior` 和 `ApplyDispatchBehavior` 方法中对操作设置该代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="f2677-129">本例中该属性并不是必要的，它在此示例中仅用于演示目的。</span><span class="sxs-lookup"><span data-stu-id="f2677-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="f2677-130">用户也可以使用代码或使用配置，手动添加类似的 `IContractBehavior`、`IEndpointBehavior` 或 `IOperationBehavior` 来启用代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="f2677-131">`IContractBehavior` 实现通过检查操作是否已注册 `DataContractSerializerOperationBehavior` 来查找使用 DataContract 的操作。</span><span class="sxs-lookup"><span data-stu-id="f2677-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="f2677-132">如果已注册，则对该行为设置 `DataContractSurrogate` 属性。</span><span class="sxs-lookup"><span data-stu-id="f2677-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="f2677-133">下面的示例代码演示如何完成以上过程。</span><span class="sxs-lookup"><span data-stu-id="f2677-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="f2677-134">在此操作行为上设置代理项可以为序列化和反序列化启用该代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 <span data-ttu-id="f2677-135">需要采取附加步骤才能插入元数据生成期间所要使用的代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="f2677-136">完成此过程的一种机制是提供本示例所演示的 `IWsdlExportExtension`。</span><span class="sxs-lookup"><span data-stu-id="f2677-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="f2677-137">另一种方式是直接修改 `WsdlExporter`。</span><span class="sxs-lookup"><span data-stu-id="f2677-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="f2677-138">`AllowNonSerializableTypesAttribute`特性实现 `IWsdlExportExtension` 和 `IContractBehavior` 。</span><span class="sxs-lookup"><span data-stu-id="f2677-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="f2677-139">`IContractBehavior` `IEndpointBehavior` 在这种情况下，扩展可以是或。</span><span class="sxs-lookup"><span data-stu-id="f2677-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="f2677-140">其 `IWsdlExportExtension.ExportContract` 方法实现通过将代理项添加到为 DataContract 生成架构的过程中使用的`XsdDataContractExporter` 来启用该代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="f2677-141">下面的代码段演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f2677-141">The following code snippet shows how to do this.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 <span data-ttu-id="f2677-142">运行示例时，客户端将调用 AddEmployee，然后调用 GetEmployee 以检查第一个调用是否成功。</span><span class="sxs-lookup"><span data-stu-id="f2677-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="f2677-143">GetEmployee 操作请求的结果显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="f2677-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="f2677-144">若要查找员工并打印 "找到"，GetEmployee 操作必须成功。</span><span class="sxs-lookup"><span data-stu-id="f2677-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2677-145">本示例演示如何插入用于序列化、反序列化和元数据生成的代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="f2677-146">示例不演示如何插入用于从元数据中生成代码的代理项。</span><span class="sxs-lookup"><span data-stu-id="f2677-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="f2677-147">若要查看如何使用代理项插入客户端代码生成的示例，请参阅[自定义 WSDL 发布](custom-wsdl-publication.md)示例。</span><span class="sxs-lookup"><span data-stu-id="f2677-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f2677-148">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="f2677-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f2677-149">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f2677-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f2677-150">若要生成 c # 版本的解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f2677-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f2677-151">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f2677-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f2677-152">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="f2677-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2677-153">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="f2677-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f2677-154">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="f2677-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2677-155">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="f2677-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
