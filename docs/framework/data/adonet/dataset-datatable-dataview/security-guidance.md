---
title: 数据集和 DataTable 安全指南
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: e9973df02ff478eedc932099fb8be0526a97b899
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679450"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="e7efa-102">数据集和 DataTable 安全指南</span><span class="sxs-lookup"><span data-stu-id="e7efa-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="e7efa-103">本文适用于：</span><span class="sxs-lookup"><span data-stu-id="e7efa-103">This article applies to:</span></span>

* <span data-ttu-id="e7efa-104">.NET Framework（所有版本）</span><span class="sxs-lookup"><span data-stu-id="e7efa-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="e7efa-105">.NET Core 和更高版本</span><span class="sxs-lookup"><span data-stu-id="e7efa-105">.NET Core and later</span></span>
* <span data-ttu-id="e7efa-106">.NET 5.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="e7efa-106">.NET 5.0 and later</span></span>

<span data-ttu-id="e7efa-107">[数据集](/dotnet/api/system.data.dataset)和[DataTable](/dotnet/api/system.data.datatable)类型是旧的 .net 组件，可将数据集表示为托管对象。</span><span class="sxs-lookup"><span data-stu-id="e7efa-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="e7efa-108">这些组件在 .NET 1.0 中作为原始 [ADO.NET 基础结构](./index.md)的一部分引入。</span><span class="sxs-lookup"><span data-stu-id="e7efa-108">These components were introduced in .NET 1.0 as part of the original [ADO.NET infrastructure](./index.md).</span></span> <span data-ttu-id="e7efa-109">其目标是通过关系数据集提供托管视图，并将数据的基础数据源抽象到 XML、SQL 或其他技术。</span><span class="sxs-lookup"><span data-stu-id="e7efa-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="e7efa-110">有关 ADO.NET 的详细信息，包括更多新式数据视图模式，请参阅 [ADO.NET 文档](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](../index.md).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="e7efa-111">从 XML 反序列化数据集或 DataTable 时的默认限制</span><span class="sxs-lookup"><span data-stu-id="e7efa-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="e7efa-112">在所有受支持版本的 .NET Framework、.NET Core 和 .NET 上， `DataSet` 并对 `DataTable` 可能存在于反序列化数据中的对象类型施加以下限制。</span><span class="sxs-lookup"><span data-stu-id="e7efa-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="e7efa-113">默认情况下，此列表限制为：</span><span class="sxs-lookup"><span data-stu-id="e7efa-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="e7efa-114">基元和基元等效项：、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `bool` `char` `sbyte` `byte` `short` `ushort` `int` `uint` `long` `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` 和 `SqlString` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="e7efa-115">常用的非基元： `Type` 、 `Uri` 和 `BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="e7efa-116">常用的 _系统_ 类型： `Color` 、 `Point` 、 `PointF` 、、、 `Rectangle` `RectangleF` `Size` 和 `SizeF` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="e7efa-117">`Enum` 各种.</span><span class="sxs-lookup"><span data-stu-id="e7efa-117">`Enum` types.</span></span>
* <span data-ttu-id="e7efa-118">上述类型的数组和列表。</span><span class="sxs-lookup"><span data-stu-id="e7efa-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="e7efa-119">如果传入的 XML 数据包含其类型不在此列表中的对象：</span><span class="sxs-lookup"><span data-stu-id="e7efa-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="e7efa-120">使用以下消息和堆栈跟踪引发异常。</span><span class="sxs-lookup"><span data-stu-id="e7efa-120">An exception is thrown with the following message and stack trace.</span></span>  
<span data-ttu-id="e7efa-121">错误消息：</span><span class="sxs-lookup"><span data-stu-id="e7efa-121">Error Message:</span></span>  
<span data-ttu-id="e7efa-122">\<Type Name\>此处不允许使用 InvalidOperationException： Type '、Version =、 \<n.n.n.n\> Culture = \<culture\> 、PublicKeyToken = \<token value\> '。</span><span class="sxs-lookup"><span data-stu-id="e7efa-122">System.InvalidOperationException : Type '\<Type Name\>, Version=\<n.n.n.n\>, Culture=\<culture\>, PublicKeyToken=\<token value\>' is not allowed here.</span></span> <span data-ttu-id="e7efa-123">[https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227)有关更多详细信息，请参阅。</span><span class="sxs-lookup"><span data-stu-id="e7efa-123">See [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) for more details.</span></span>  
<span data-ttu-id="e7efa-124">堆栈跟踪：</span><span class="sxs-lookup"><span data-stu-id="e7efa-124">Stack Trace:</span></span>  
<span data-ttu-id="e7efa-125">在 TypeLimiter. EnsureTypeIsAllowed (Type type，TypeLimiter capturedLimiter) </span><span class="sxs-lookup"><span data-stu-id="e7efa-125">at System.Data.TypeLimiter.EnsureTypeIsAllowed(Type type, TypeLimiter capturedLimiter)</span></span>  
<span data-ttu-id="e7efa-126">在 UpdateColumnType (类型类型，StorageType typeCode) </span><span class="sxs-lookup"><span data-stu-id="e7efa-126">at System.Data.DataColumn.UpdateColumnType(Type type, StorageType typeCode)</span></span>  
<span data-ttu-id="e7efa-127">在 set_DataType (类型值) </span><span class="sxs-lookup"><span data-stu-id="e7efa-127">at System.Data.DataColumn.set_DataType(Type value)</span></span>  

* <span data-ttu-id="e7efa-128">反序列化操作失败。</span><span class="sxs-lookup"><span data-stu-id="e7efa-128">The deserialization operation fails.</span></span>

<span data-ttu-id="e7efa-129">将 XML 加载到现有的 `DataSet` 或 `DataTable` 实例时，也会考虑现有的列定义。</span><span class="sxs-lookup"><span data-stu-id="e7efa-129">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="e7efa-130">如果表已包含自定义类型的列定义，则在 XML 反序列化操作期间，该类型暂时添加到允许列表中。</span><span class="sxs-lookup"><span data-stu-id="e7efa-130">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

> [!NOTE]
> <span data-ttu-id="e7efa-131">向添加列后 `DataTable` ， `ReadXml` 将不会从 XML 读取架构，如果架构不匹配，也不会读取记录，因此，你需要自行添加所有列以使用此方法。</span><span class="sxs-lookup"><span data-stu-id="e7efa-131">Once you add columns to a `DataTable`, `ReadXml` will not read the schema from the XML, and if the schema does not match it will also not read in the records, so you will need to add all the columns yourself to use this method.</span></span>

```csharp
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

<span data-ttu-id="e7efa-132">当使用 `XmlSerializer` 反序列化或的实例时，对象类型限制也适用 `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-132">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="e7efa-133">但是，当使用 `BinaryFormatter` 反序列化或的实例时，它们可能不适用 `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-133">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="e7efa-134">使用时，不应用对象类型限制 `DataAdapter.Fill` ，例如，在 `DataTable` 不使用 XML 反序列化 api 的情况下直接从数据库填充实例时。</span><span class="sxs-lookup"><span data-stu-id="e7efa-134">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="e7efa-135">扩展允许的类型列表</span><span class="sxs-lookup"><span data-stu-id="e7efa-135">Extend the list of allowed types</span></span>

<span data-ttu-id="e7efa-136">除了上面列出的内置类型外，应用程序还可以扩展允许的类型列表以包括自定义类型。</span><span class="sxs-lookup"><span data-stu-id="e7efa-136">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="e7efa-137">如果扩展允许的类型列表，则更改会_all_影响 `DataSet` `DataTable` 应用内的所有和实例。</span><span class="sxs-lookup"><span data-stu-id="e7efa-137">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="e7efa-138">不能从内置允许类型列表中删除类型。</span><span class="sxs-lookup"><span data-stu-id="e7efa-138">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="e7efa-139">通过配置 ( 扩展 .NET Framework 4.0-4.8) </span><span class="sxs-lookup"><span data-stu-id="e7efa-139">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="e7efa-140">_App.config_ 可用于扩展允许的类型列表。</span><span class="sxs-lookup"><span data-stu-id="e7efa-140">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="e7efa-141">扩展允许的类型列表：</span><span class="sxs-lookup"><span data-stu-id="e7efa-141">To extend the allowed types list:</span></span>

* <span data-ttu-id="e7efa-142">使用 `<configSections>` 元素可添加对 " _system.object_ 配置" 部分的引用。</span><span class="sxs-lookup"><span data-stu-id="e7efa-142">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="e7efa-143">使用 `<system.data.dataset.serialization>` / `<allowedTypes>` 指定其他类型。</span><span class="sxs-lookup"><span data-stu-id="e7efa-143">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="e7efa-144">每个 `<add>` 元素只能使用其程序集限定类型名称指定一种类型。</span><span class="sxs-lookup"><span data-stu-id="e7efa-144">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="e7efa-145">若要将其他类型添加到 "允许的类型" 列表中，请使用多个 `<add>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e7efa-145">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="e7efa-146">下面的示例演示如何通过添加自定义类型来扩展允许的类型列表 `Fabrikam.CustomType` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-146">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="e7efa-147">若要检索某个类型的程序集限定名称，请使用 [AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) 属性，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="e7efa-147">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```csharp
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="e7efa-148">通过配置 ( 扩展 .NET Framework 2.0-3.5) </span><span class="sxs-lookup"><span data-stu-id="e7efa-148">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="e7efa-149">如果你的应用面向 .NET Framework 2.0 或3.5，你仍可以使用上述 _App.config_ 机制来扩展允许的类型列表。</span><span class="sxs-lookup"><span data-stu-id="e7efa-149">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="e7efa-150">但是，你 `<configSections>` 的元素看上去将略有不同，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-150">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="e7efa-151">以编程方式扩展 ( .NET Framework，.NET Core，.NET 5.0 +) </span><span class="sxs-lookup"><span data-stu-id="e7efa-151">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="e7efa-152">还可以通过将[DataSetDefaultAllowedTypes 与众所周知的密钥](/dotnet/api/system.appdomain.setdata)_系统_一起使用，以编程方式扩展允许的类型列表，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e7efa-152">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```csharp
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="e7efa-153">如果使用扩展机制，则与密钥 _DataSetDefaultAllowedTypes_ 关联的值的类型必须为 `Type[]` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-153">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="e7efa-154">在 .NET Framework 上，可以使用 _App.config_ 和来扩展允许的类型列表 `AppDomain.SetData` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-154">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="e7efa-155">在这种情况下， `DataSet` 和 `DataTable` 将允许将对象作为数据的一部分进行反序列化（如果其类型存在于任一列表中）。</span><span class="sxs-lookup"><span data-stu-id="e7efa-155">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="e7efa-156">在审核模式下运行应用 ( .NET Framework) </span><span class="sxs-lookup"><span data-stu-id="e7efa-156">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="e7efa-157">在 .NET Framework 中， `DataSet` 并 `DataTable` 提供审核模式功能。</span><span class="sxs-lookup"><span data-stu-id="e7efa-157">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="e7efa-158">当启用审核模式时， `DataSet` 并 `DataTable` 根据允许的类型列表比较传入对象的类型。</span><span class="sxs-lookup"><span data-stu-id="e7efa-158">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="e7efa-159">但是，如果显示不允许其类型的对象，则 **不** 会引发异常。</span><span class="sxs-lookup"><span data-stu-id="e7efa-159">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="e7efa-160">相反， `DataSet` 并 `DataTable` 通知任何附加的 `TraceListener` 实例存在可疑类型，从而允许 `TraceListener` 记录此信息。</span><span class="sxs-lookup"><span data-stu-id="e7efa-160">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="e7efa-161">不会引发异常，并且反序列化操作将继续。</span><span class="sxs-lookup"><span data-stu-id="e7efa-161">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="e7efa-162">在 "审核模式" 下运行应用程序时，只应使用临时度量值进行测试。</span><span class="sxs-lookup"><span data-stu-id="e7efa-162">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="e7efa-163">当启用审核模式时， `DataSet` 并且 `DataTable` 不强制实施类型限制，这可能会在应用内引入安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="e7efa-163">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="e7efa-164">有关详细信息，请参阅标题为删除[不受信任输入](#swr)相关的[所有类型限制](#ratr)和安全性部分。</span><span class="sxs-lookup"><span data-stu-id="e7efa-164">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="e7efa-165">可以通过 _App.config_启用审核模式：</span><span class="sxs-lookup"><span data-stu-id="e7efa-165">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="e7efa-166">请参阅本文档中的 [扩展配置](#etc) 部分，了解要为元素放入的适当值 `<configSections>` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-166">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="e7efa-167">使用 `<allowedTypes auditOnly="true">` 启用审核模式，如以下标记所示。</span><span class="sxs-lookup"><span data-stu-id="e7efa-167">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="e7efa-168">一旦启用了审核模式，就可以使用_App.config_将您首选的内置 `TraceListener` `DataSet` `TraceSource.` 跟踪_System.Data.DataSet_源名称连接到 "system.string"。</span><span class="sxs-lookup"><span data-stu-id="e7efa-168">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="e7efa-169">下面的示例演示如何将跟踪事件写入控制台 _和_ 磁盘上的日志文件。</span><span class="sxs-lookup"><span data-stu-id="e7efa-169">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

<span data-ttu-id="e7efa-170">有关和的详细 `TraceSource` 信息 `TraceListener` ，请参阅文档 [如何：将 TraceSource 和筛选器与跟踪侦听器一起使用](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-170">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e7efa-171">在审核模式下运行应用在 .NET Core 或 .NET 5.0 及更高版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="e7efa-171">Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="e7efa-172">删除所有类型限制</span><span class="sxs-lookup"><span data-stu-id="e7efa-172">Remove all type restrictions</span></span>

<span data-ttu-id="e7efa-173">如果应用必须从和中移除所有类型限制 `DataSet` 限制 `DataTable` ：</span><span class="sxs-lookup"><span data-stu-id="e7efa-173">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="e7efa-174">有几个选项可用于取消类型限制限制。</span><span class="sxs-lookup"><span data-stu-id="e7efa-174">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="e7efa-175">可用的选项取决于应用的目标框架。</span><span class="sxs-lookup"><span data-stu-id="e7efa-175">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="e7efa-176">删除所有类型限制可能会在应用内引入安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="e7efa-176">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="e7efa-177">使用此机制时，请确保应用 **不** 使用 `DataSet` 或 `DataTable` 读取不受信任的输入。</span><span class="sxs-lookup"><span data-stu-id="e7efa-177">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="e7efa-178">有关详细信息，请参阅 [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) 和标题为 " [有关不受信任的输入的安全](#swr)" 的部分。</span><span class="sxs-lookup"><span data-stu-id="e7efa-178">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="e7efa-179">通过 AppContext 配置 ( .NET Framework 4.6-4.8、.NET Core 2.1 及更高版本、.NET 5.0 和更高版本) </span><span class="sxs-lookup"><span data-stu-id="e7efa-179">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="e7efa-180">`AppContext` `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` 当设置为时，开关会 `true` 从和中移除所有类型限制限制 `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-180">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="e7efa-181">在 .NET Framework 中，可以通过 _App.config_启用此开关，如以下配置所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-181">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="e7efa-182">在 ASP.NET 中， `<AppContextSwitchOverrides>` 元素不可用。</span><span class="sxs-lookup"><span data-stu-id="e7efa-182">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="e7efa-183">相反，可以通过 _Web.config_启用交换机，如以下配置所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-183">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="e7efa-184">有关详细信息，请参阅 [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="e7efa-184">For more information, see the [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element.</span></span>

<span data-ttu-id="e7efa-185">在 .NET Core、.NET 5 和 ASP.NET Core 中，此设置由 _runtimeconfig.js_控制，如以下 JSON 中所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-185">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="e7efa-186">有关详细信息，请参阅 [".Net Core 运行时配置设置"](../../../../core/run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-186">For more information, see [".NET Core run-time configuration settings"](../../../../core/run-time-config/index.md).</span></span>

<span data-ttu-id="e7efa-187">`AllowArbitraryDataSetTypeInstantiation` 还可以通过 [AppContext](/dotnet/api/system.appcontext.setswitch) （而不是配置文件）以编程方式进行设置，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-187">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```csharp
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="e7efa-188">如果选择前面的编程方法，则对的调用 `AppContext.SetSwitch` 应在应用程序启动初期进行。</span><span class="sxs-lookup"><span data-stu-id="e7efa-188">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="e7efa-189">通过计算机范围内的注册表 ( .NET Framework 2.0-4.8) </span><span class="sxs-lookup"><span data-stu-id="e7efa-189">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="e7efa-190">如果不可用 `AppContext` ，则可以使用 Windows 注册表禁用类型限制检查：</span><span class="sxs-lookup"><span data-stu-id="e7efa-190">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="e7efa-191">管理员必须配置注册表。</span><span class="sxs-lookup"><span data-stu-id="e7efa-191">An administrator must configure the registry.</span></span>
* <span data-ttu-id="e7efa-192">使用注册表是计算机范围的更改，将影响计算机上运行的 _所有_ 应用。</span><span class="sxs-lookup"><span data-stu-id="e7efa-192">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="e7efa-193">类型</span><span class="sxs-lookup"><span data-stu-id="e7efa-193">Type</span></span>  |  <span data-ttu-id="e7efa-194">值</span><span class="sxs-lookup"><span data-stu-id="e7efa-194">Value</span></span> |
|---|---|
| <span data-ttu-id="e7efa-195">**注册表项**</span><span class="sxs-lookup"><span data-stu-id="e7efa-195">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="e7efa-196">**值名称**</span><span class="sxs-lookup"><span data-stu-id="e7efa-196">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="e7efa-197">**值类型**</span><span class="sxs-lookup"><span data-stu-id="e7efa-197">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="e7efa-198">**值数据**</span><span class="sxs-lookup"><span data-stu-id="e7efa-198">**Value data**</span></span> | `true` |

<span data-ttu-id="e7efa-199">在64位操作系统中，需要为上面显示的64位密钥 (添加此值) 和32位密钥。</span><span class="sxs-lookup"><span data-stu-id="e7efa-199">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="e7efa-200">32位键位于 `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-200">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="e7efa-201">有关使用注册表进行配置的详细信息 `AppContext` ，请参阅 ["库使用者的 AppContext"](/dotnet/api/system.appcontext#appcontext-for-library-consumers)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-201">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="e7efa-202">不受信任输入相关的安全</span><span class="sxs-lookup"><span data-stu-id="e7efa-202">Safety with regard to untrusted input</span></span>

<span data-ttu-id="e7efa-203">尽管 `DataSet` 和 `DataTable` 确实对允许在反序列化 XML 有效负载时存在的类型施加默认限制，但__ `DataSet` `DataTable` 在使用不受信任的输入进行填充时，和都是不安全的。__</span><span class="sxs-lookup"><span data-stu-id="e7efa-203">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="e7efa-204">下面是 `DataSet` 或 `DataTable` 实例可能读取不受信任的输入的一系列非详尽列表。</span><span class="sxs-lookup"><span data-stu-id="e7efa-204">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="e7efa-205">`DataAdapter`引用数据库， `DataAdapter.Fill` 方法用于使用 `DataSet` 数据库查询的内容来填充。</span><span class="sxs-lookup"><span data-stu-id="e7efa-205">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="e7efa-206">`DataSet.ReadXml`或 `DataTable.ReadXml` 方法用于读取包含列和行信息的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e7efa-206">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="e7efa-207">`DataSet`或 `DataTable` 实例序列化为 ASP.NET (SOAP) web 服务或 WCF 终结点。</span><span class="sxs-lookup"><span data-stu-id="e7efa-207">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="e7efa-208">序列化程序（如） `XmlSerializer` 用于 `DataSet` 从 XML 流反序列化或 `DataTable` 实例。</span><span class="sxs-lookup"><span data-stu-id="e7efa-208">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="e7efa-209">序列化程序（如） `JsonConvert` 用于 `DataSet` 从 JSON 流反序列化或 `DataTable` 实例。</span><span class="sxs-lookup"><span data-stu-id="e7efa-209">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="e7efa-210">`JsonConvert` 是常用的第三方 [Newtonsoft.Js](https://www.newtonsoft.com/json) 库中的一种方法。</span><span class="sxs-lookup"><span data-stu-id="e7efa-210">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="e7efa-211">序列化程序（如） `BinaryFormatter` 用于 `DataSet` `DataTable` 从原始字节流中反序列化或实例。</span><span class="sxs-lookup"><span data-stu-id="e7efa-211">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="e7efa-212">本文档讨论上述方案的安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="e7efa-212">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="e7efa-213">用于 `DataAdapter.Fill` `DataSet` 从不受信任的数据源填充</span><span class="sxs-lookup"><span data-stu-id="e7efa-213">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="e7efa-214">`DataSet` `DataAdapter` 通过使用[ `DataAdapter.Fill` 方法](/dotnet/api/system.data.common.dataadapter.fill)，可以从中填充实例，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e7efa-214">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```csharp
// Assumes that connection is a valid SqlConnection object.
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);

DataSet customers = new DataSet();
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="e7efa-215"> (上面的代码示例是 [从 DataAdapter 填充数据集中](../populating-a-dataset-from-a-dataadapter.md)找到的更大示例的一部分。 ) </span><span class="sxs-lookup"><span data-stu-id="e7efa-215">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span></span>

> <span data-ttu-id="e7efa-216">大多数应用程序都可以简化，并假定其数据库层受信任。</span><span class="sxs-lookup"><span data-stu-id="e7efa-216">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="e7efa-217">但是，如果您正在对应用程序进行 [威胁建模](https://www.microsoft.com/securityengineering/sdl/threatmodeling) ，则威胁模型可能会将应用程序 (客户端) 和数据库层之间的信任边界视为 (服务器) 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-217">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="e7efa-218">在客户端和服务器之间使用 [相互身份验证](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) 或 [AAD 身份验证](/azure/azure-sql/database/authentication-aad-overview) 是一种帮助解决与此相关的风险的方法。</span><span class="sxs-lookup"><span data-stu-id="e7efa-218">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="e7efa-219">本部分的剩余部分讨论连接到不受信任的服务器的客户端可能的结果。</span><span class="sxs-lookup"><span data-stu-id="e7efa-219">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="e7efa-220">指向 `DataAdapter` 不受信任的数据源的后果取决于 `DataAdapter` 其自身的实现。</span><span class="sxs-lookup"><span data-stu-id="e7efa-220">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="e7efa-221">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="e7efa-221">SqlDataAdapter</span></span>

<span data-ttu-id="e7efa-222">对于内置类型 [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)，引用不受信任的数据源可能会导致拒绝服务 (DoS) 攻击。</span><span class="sxs-lookup"><span data-stu-id="e7efa-222">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="e7efa-223">DoS 攻击可能导致应用变得无响应或崩溃。</span><span class="sxs-lookup"><span data-stu-id="e7efa-223">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="e7efa-224">如果攻击者可以在应用程序中使用 DLL，则他们还可以实现本地代码执行。</span><span class="sxs-lookup"><span data-stu-id="e7efa-224">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="e7efa-225">其他 DataAdapter 类型</span><span class="sxs-lookup"><span data-stu-id="e7efa-225">Other DataAdapter types</span></span>

<span data-ttu-id="e7efa-226">第三方 `DataAdapter` 实现必须对其在不受信任的输入中提供的安全保证进行自我评估。</span><span class="sxs-lookup"><span data-stu-id="e7efa-226">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="e7efa-227">.NET 无法确保与这些实现有关的任何安全保障。</span><span class="sxs-lookup"><span data-stu-id="e7efa-227">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="e7efa-228">ReadXml 和 ReadXml</span><span class="sxs-lookup"><span data-stu-id="e7efa-228">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="e7efa-229">`DataSet.ReadXml` `DataTable.ReadXml` 与不受信任的输入一起使用时，和方法是安全的。</span><span class="sxs-lookup"><span data-stu-id="e7efa-229">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="e7efa-230">强烈建议使用者改为考虑使用本文档后面所述的备选方案之一。</span><span class="sxs-lookup"><span data-stu-id="e7efa-230">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="e7efa-231">和的实现 `DataSet.ReadXml` `DataTable.ReadXml` 最初是在序列化漏洞成为一种很好理解的威胁类别之前创建的。</span><span class="sxs-lookup"><span data-stu-id="e7efa-231">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="e7efa-232">因此，代码不遵循当前安全最佳做法。</span><span class="sxs-lookup"><span data-stu-id="e7efa-232">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="e7efa-233">这些 Api 可用作攻击者对 web 应用执行 DoS 攻击的媒介。</span><span class="sxs-lookup"><span data-stu-id="e7efa-233">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="e7efa-234">这些攻击可能会导致 web 服务无响应或导致意外的进程终止。</span><span class="sxs-lookup"><span data-stu-id="e7efa-234">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="e7efa-235">此框架不提供对这些攻击类别的缓解措施，.NET 认为 "按设计" 了此行为。</span><span class="sxs-lookup"><span data-stu-id="e7efa-235">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="e7efa-236">.NET 已发布安全更新，可在和中缓解某些问题，例如信息泄漏或远程代码执行 `DataSet.ReadXml` `DataTable.ReadXml` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-236">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="e7efa-237">.NET 安全更新可能无法提供对这些威胁类别的完整保护。</span><span class="sxs-lookup"><span data-stu-id="e7efa-237">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="e7efa-238">使用者应该评估其各个应用场景，并考虑他们遇到这些风险的可能性。</span><span class="sxs-lookup"><span data-stu-id="e7efa-238">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="e7efa-239">使用者应该知道，在某些情况下，这些 Api 的安全更新可能影响应用程序的兼容性。</span><span class="sxs-lookup"><span data-stu-id="e7efa-239">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="e7efa-240">此外，还可能会发现，.NET 不能几乎不能发布安全更新。</span><span class="sxs-lookup"><span data-stu-id="e7efa-240">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="e7efa-241">建议使用以下 Api 的使用者：</span><span class="sxs-lookup"><span data-stu-id="e7efa-241">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="e7efa-242">请考虑使用本文档后面所述的一种替代方法。</span><span class="sxs-lookup"><span data-stu-id="e7efa-242">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="e7efa-243">对其应用执行单独的风险评估。</span><span class="sxs-lookup"><span data-stu-id="e7efa-243">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="e7efa-244">使用者唯一负责确定是否要使用这些 Api。</span><span class="sxs-lookup"><span data-stu-id="e7efa-244">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="e7efa-245">消费者应评估任何安全、技术和法律风险，包括使用这些 Api 时可能附带的法规要求。</span><span class="sxs-lookup"><span data-stu-id="e7efa-245">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="e7efa-246">通过 ASP.NET web 服务或 WCF 进行数据集和 DataTable</span><span class="sxs-lookup"><span data-stu-id="e7efa-246">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="e7efa-247">可以接受 `DataSet` `DataTable` ASP.NET (SOAP) web 服务中的或实例，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-247">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

```csharp
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

<span data-ttu-id="e7efa-248">这种情况下的变体不接受 `DataSet` 或 `DataTable` 直接作为参数，而是将其作为整体 SOAP 序列化对象图的一部分接受，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-248">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

```csharp
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e7efa-249">或者，使用 WCF 而不是 ASP.NET web 服务：</span><span class="sxs-lookup"><span data-stu-id="e7efa-249">Or, using WCF instead of ASP.NET web services:</span></span>

```csharp
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e7efa-250">在所有这些情况下，威胁模型和安全保证都与 [ReadXml 和 ReadXml 节](#dsrdtr)相同。</span><span class="sxs-lookup"><span data-stu-id="e7efa-250">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="e7efa-251">通过 XmlSerializer 反序列化数据集或 DataTable</span><span class="sxs-lookup"><span data-stu-id="e7efa-251">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="e7efa-252">开发人员可以使用 `XmlSerializer` 反序列化 `DataSet` 和 `DataTable` 实例，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-252">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```csharp
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e7efa-253">在这些情况下，威胁模型和安全保证与[ReadXml 和 ReadXml 节](#dsrdtr)相同</span><span class="sxs-lookup"><span data-stu-id="e7efa-253">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="e7efa-254">通过 JsonConvert 反序列化 DataSet 或 DataTable</span><span class="sxs-lookup"><span data-stu-id="e7efa-254">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="e7efa-255">常见的第三方 Newtonsoft.json 库 [JSON.NET](https://www.newtonsoft.com/json) 可用于反序列化 `DataSet` 和 `DataTable` 实例，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="e7efa-255">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```csharp
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObject<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObject<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e7efa-256">`DataSet` `DataTable` 以这种方式从不受信任的 JSON blob 反序列化或反序列化是不安全的。</span><span class="sxs-lookup"><span data-stu-id="e7efa-256">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="e7efa-257">此模式容易遭受拒绝服务攻击。</span><span class="sxs-lookup"><span data-stu-id="e7efa-257">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="e7efa-258">此类攻击可能导致应用崩溃或使其无响应。</span><span class="sxs-lookup"><span data-stu-id="e7efa-258">Such an attack could crash the app or render it unresponsive.</span></span>

> [!NOTE]
> <span data-ttu-id="e7efa-259">Microsoft 不保证或支持实现第三方库，如 _Newtonsoft.Js_。</span><span class="sxs-lookup"><span data-stu-id="e7efa-259">Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="e7efa-260">此信息是为完整性提供的，并且在撰写本文的时间准确无误。</span><span class="sxs-lookup"><span data-stu-id="e7efa-260">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="e7efa-261">通过 BinaryFormatter 反序列化 DataSet 或 DataTable</span><span class="sxs-lookup"><span data-stu-id="e7efa-261">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="e7efa-262">开发人员决不能使用 `BinaryFormatter` 、 `NetDataContractSerializer` 、 `SoapFormatter` 或相关的 ***unsafe*** 格式化 `DataSet` `DataTable` 程序从不受信任的负载反序列化或实例：</span><span class="sxs-lookup"><span data-stu-id="e7efa-262">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related ***unsafe*** formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

* <span data-ttu-id="e7efa-263">这很容易受到完全远程代码执行攻击。</span><span class="sxs-lookup"><span data-stu-id="e7efa-263">This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="e7efa-264">使用自定义 `SerializationBinder` 并不足以防止这种攻击。</span><span class="sxs-lookup"><span data-stu-id="e7efa-264">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="e7efa-265">安全替换</span><span class="sxs-lookup"><span data-stu-id="e7efa-265">Safe replacements</span></span>

<span data-ttu-id="e7efa-266">对于以下两种应用：</span><span class="sxs-lookup"><span data-stu-id="e7efa-266">For apps that either:</span></span>

* <span data-ttu-id="e7efa-267">接受 `DataSet` 或 `DataTable` 通过 .asmx SOAP 终结点或 WCF 终结点。</span><span class="sxs-lookup"><span data-stu-id="e7efa-267">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="e7efa-268">将不受信任的数据反序列化为或的实例 `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-268">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="e7efa-269">请考虑将对象模型替换为使用 [实体框架](/ef)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-269">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="e7efa-270">实体框架：</span><span class="sxs-lookup"><span data-stu-id="e7efa-270">Entity Framework:</span></span>

* <span data-ttu-id="e7efa-271">是一个丰富的、面向对象的新型框架，可表示关系数据。</span><span class="sxs-lookup"><span data-stu-id="e7efa-271">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="e7efa-272">引入 [了一种不同](/ef/core/providers/) 的数据库提供程序生态系统，使您可以轻松地通过实体框架对象模型来投影数据库查询。</span><span class="sxs-lookup"><span data-stu-id="e7efa-272">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="e7efa-273">在反序列化来自不受信任源的数据时提供内置保护。</span><span class="sxs-lookup"><span data-stu-id="e7efa-273">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="e7efa-274">对于使用 `.aspx` SOAP 终结点的应用，请考虑将这些终结点更改为使用 [WCF](../../../wcf/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-274">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](../../../wcf/index.md).</span></span> <span data-ttu-id="e7efa-275">WCF 是为 web 服务提供的更好的替代功能 `.asmx` 。</span><span class="sxs-lookup"><span data-stu-id="e7efa-275">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="e7efa-276">[可以通过 SOAP 公开](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)WCF 终结点，以便与现有调用方兼容。</span><span class="sxs-lookup"><span data-stu-id="e7efa-276">WCF endpoints [can be exposed via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) for compatibility with existing callers.</span></span>

## <a name="code-analyzers"></a><span data-ttu-id="e7efa-277">代码分析器</span><span class="sxs-lookup"><span data-stu-id="e7efa-277">Code analyzers</span></span>

<span data-ttu-id="e7efa-278">代码分析器安全规则在您的源代码编译后运行，可帮助找到与 c # 中的此安全问题和 Visual Basic 代码相关的漏洞。</span><span class="sxs-lookup"><span data-stu-id="e7efa-278">Code analyzer security rules, which run when your source code is compiled, can help to find vulnerabilities related to this security issue in C# and Visual Basic code.</span></span> <span data-ttu-id="e7efa-279">CodeAnalysis. FxCopAnalyzers 是在 [nuget.org](https://www.nuget.org/)上分发的代码分析器 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="e7efa-279">Microsoft.CodeAnalysis.FxCopAnalyzers is a NuGet package of code analyzers that's distributed on [nuget.org](https://www.nuget.org/).</span></span>

<span data-ttu-id="e7efa-280">有关代码分析器的概述，请参阅 [源代码分析器概述](/visualstudio/code-quality/roslyn-analyzers-overview)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-280">For an overview of code analyzers, see [Overview of source code analyzers](/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

<span data-ttu-id="e7efa-281">启用以下 CodeAnalysis FxCopAnalyzers 规则：</span><span class="sxs-lookup"><span data-stu-id="e7efa-281">Enable the following Microsoft.CodeAnalysis.FxCopAnalyzers rules:</span></span>

- <span data-ttu-id="e7efa-282">[CA2350](/visualstudio/code-quality/ca2350)：不要使用 DataTable. ReadXml ( 包含不受信任数据的 # A1</span><span class="sxs-lookup"><span data-stu-id="e7efa-282">[CA2350](/visualstudio/code-quality/ca2350): Do not use DataTable.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="e7efa-283">[CA2351](/visualstudio/code-quality/ca2351)：不要使用 ReadXml ( 包含不受信任数据的 # A1</span><span class="sxs-lookup"><span data-stu-id="e7efa-283">[CA2351](/visualstudio/code-quality/ca2351): Do not use DataSet.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="e7efa-284">[CA2352](/visualstudio/code-quality/ca2352)：可序列化的类型中的不安全数据集或 DataTable 可能易受到远程代码执行攻击</span><span class="sxs-lookup"><span data-stu-id="e7efa-284">[CA2352](/visualstudio/code-quality/ca2352): Unsafe DataSet or DataTable in serializable type can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="e7efa-285">[CA2353](/visualstudio/code-quality/ca2353)：可序列化类型中的不安全数据集或 DataTable</span><span class="sxs-lookup"><span data-stu-id="e7efa-285">[CA2353](/visualstudio/code-quality/ca2353): Unsafe DataSet or DataTable in serializable type</span></span>
- <span data-ttu-id="e7efa-286">[CA2354](/visualstudio/code-quality/ca2354)：反序列化对象图中不安全的数据集或 DataTable 可能易受到远程代码执行攻击</span><span class="sxs-lookup"><span data-stu-id="e7efa-286">[CA2354](/visualstudio/code-quality/ca2354): Unsafe DataSet or DataTable in deserialized object graph can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="e7efa-287">[CA2355](/visualstudio/code-quality/ca2355)：反序列化对象图中发现不安全的数据集或 DataTable 类型</span><span class="sxs-lookup"><span data-stu-id="e7efa-287">[CA2355](/visualstudio/code-quality/ca2355): Unsafe DataSet or DataTable type found in deserializable object graph</span></span>
- <span data-ttu-id="e7efa-288">[CA2356](/visualstudio/code-quality/ca2356)： web 反序列化对象图中的不安全数据集或 DataTable 类型</span><span class="sxs-lookup"><span data-stu-id="e7efa-288">[CA2356](/visualstudio/code-quality/ca2356): Unsafe DataSet or DataTable type in web deserializable object graph</span></span>
- <span data-ttu-id="e7efa-289">[CA2361](/visualstudio/code-quality/ca2361)：确保包含 DataSet 的自动生成的类。 ReadXml ( # A1 不与不受信任的数据一起使用</span><span class="sxs-lookup"><span data-stu-id="e7efa-289">[CA2361](/visualstudio/code-quality/ca2361): Ensure autogenerated class containing DataSet.ReadXml() is not used with untrusted data</span></span>
- <span data-ttu-id="e7efa-290">[CA2362](/visualstudio/code-quality/ca2362)：自动生成序列化类型中的不安全数据集或 DataTable 可能易受到远程代码执行攻击</span><span class="sxs-lookup"><span data-stu-id="e7efa-290">[CA2362](/visualstudio/code-quality/ca2362): Unsafe DataSet or DataTable in autogenerated serializable type can be vulnerable to remote code execution attacks</span></span>

<span data-ttu-id="e7efa-291">有关配置规则的详细信息，请参阅 [使用代码分析器](/visualstudio/code-quality/use-roslyn-analyzers)。</span><span class="sxs-lookup"><span data-stu-id="e7efa-291">For more information about configuring rules, see [Use code analyzers](/visualstudio/code-quality/use-roslyn-analyzers).</span></span>

<span data-ttu-id="e7efa-292">以下 NuGet 包中提供了新的安全规则：</span><span class="sxs-lookup"><span data-stu-id="e7efa-292">The new security rules are available in the following NuGet packages:</span></span>

- <span data-ttu-id="e7efa-293">CodeAnalysis. FxCopAnalyzers 3.3.0： for Visual Studio 2019 版本16.3 或更高版本</span><span class="sxs-lookup"><span data-stu-id="e7efa-293">Microsoft.CodeAnalysis.FxCopAnalyzers 3.3.0: for Visual Studio 2019 version 16.3 or later</span></span>
- <span data-ttu-id="e7efa-294">CodeAnalysis. FxCopAnalyzers 2.9.11： for Visual Studio 2017 版本15.9 或更高版本</span><span class="sxs-lookup"><span data-stu-id="e7efa-294">Microsoft.CodeAnalysis.FxCopAnalyzers 2.9.11: for Visual Studio 2017 version 15.9 or later</span></span>
