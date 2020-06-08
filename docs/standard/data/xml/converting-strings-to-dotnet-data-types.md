---
title: 将字符串转换为 .NET Framework 数据类型
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: fda5441c58d14b91a9eca16fff9149c8795f95b9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289221"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="529da-102">将字符串转换为 .NET Framework 数据类型</span><span class="sxs-lookup"><span data-stu-id="529da-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="529da-103">若要将字符串转换为 .NET Framework 数据类型，请使用满足应用要求的 XmlConvert  方法。</span><span class="sxs-lookup"><span data-stu-id="529da-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="529da-104">有关 XmlConvert  类提供的所有转换方法的列表，请参阅 <xref:System.Xml.XmlConvert>。</span><span class="sxs-lookup"><span data-stu-id="529da-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="529da-105">从 ToString  方法返回的字符串是传入数据的字符串版本。</span><span class="sxs-lookup"><span data-stu-id="529da-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="529da-106">此外，还有若干 .NET Framework 类型仍使用 XmlConvert  类进行转换，但它们不使用 System.Convert  类中的方法。</span><span class="sxs-lookup"><span data-stu-id="529da-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="529da-107">XmlConvert  类遵循 XML 架构 (XSD) 数据类型规范，并有 XMLConvert  可以映射到的数据类型。</span><span class="sxs-lookup"><span data-stu-id="529da-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="529da-108">下表列出了 .NET Framework 数据类型和使用 XML 架构 (XSD) 数据类型映射返回的字符串类型。</span><span class="sxs-lookup"><span data-stu-id="529da-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="529da-109">不能使用 System.Convert  处理这些 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="529da-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="529da-110">.NET Framework 类型</span><span class="sxs-lookup"><span data-stu-id="529da-110">.NET Framework type</span></span>|<span data-ttu-id="529da-111">返回的字符串</span><span class="sxs-lookup"><span data-stu-id="529da-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="529da-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="529da-112">Boolean</span></span>|<span data-ttu-id="529da-113">“true”、“false”</span><span class="sxs-lookup"><span data-stu-id="529da-113">"true", "false"</span></span>|  
|<span data-ttu-id="529da-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="529da-115">“INF”</span><span class="sxs-lookup"><span data-stu-id="529da-115">"INF"</span></span>|  
|<span data-ttu-id="529da-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="529da-117">“-INF”</span><span class="sxs-lookup"><span data-stu-id="529da-117">"-INF"</span></span>|  
|<span data-ttu-id="529da-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="529da-119">“INF”</span><span class="sxs-lookup"><span data-stu-id="529da-119">"INF"</span></span>|  
|<span data-ttu-id="529da-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="529da-121">“-INF”</span><span class="sxs-lookup"><span data-stu-id="529da-121">"-INF"</span></span>|  
|<span data-ttu-id="529da-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="529da-122">DateTime</span></span>|<span data-ttu-id="529da-123">格式为“yyyy-MM-ddTHH:mm:sszzzzzz”及其子集。</span><span class="sxs-lookup"><span data-stu-id="529da-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="529da-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="529da-124">Timespan</span></span>|<span data-ttu-id="529da-125">格式是 PnYnMnTnHnMnS，例如 `P2Y10M15DT10H30M20S` 表示长 2 年 10 个月 15 天 10 小时 30 分钟 20 秒的持续时间。</span><span class="sxs-lookup"><span data-stu-id="529da-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="529da-126">如果使用 ToString  方法将表中所列的任何 .NET Framework 类型转换为字符串，返回的字符串不是基类型，而是 XML 架构 (XSD) 字符串类型。</span><span class="sxs-lookup"><span data-stu-id="529da-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="529da-127">DateTime  和 Timespan  值类型的区别在于，DateTime  表示时间上的某个时刻，而 TimeSpan  则表示时间间隔。</span><span class="sxs-lookup"><span data-stu-id="529da-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="529da-128">XML 架构 (XSD) 数据类型规范中指定了 DateTime  和 Timespan  格式。</span><span class="sxs-lookup"><span data-stu-id="529da-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="529da-129">例如：</span><span class="sxs-lookup"><span data-stu-id="529da-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="529da-130">**输出**</span><span class="sxs-lookup"><span data-stu-id="529da-130">**Output**</span></span>  
  
 <span data-ttu-id="529da-131">`<Date>2001-08-04T00:00:00</Date>`。</span><span class="sxs-lookup"><span data-stu-id="529da-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="529da-132">下面的代码将整数转换为字符串：</span><span class="sxs-lookup"><span data-stu-id="529da-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="529da-133">**输出**</span><span class="sxs-lookup"><span data-stu-id="529da-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="529da-134">不过，如果将字符串转换为 Boolean  、Single  或 Double  ，返回的 .NET Framework 类型与使用 System.Convert  类返回的类型不同。</span><span class="sxs-lookup"><span data-stu-id="529da-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="529da-135">将字符串转换为 Boolean</span><span class="sxs-lookup"><span data-stu-id="529da-135">String to Boolean</span></span>  
 <span data-ttu-id="529da-136">下表列出了使用 ToBoolean  方法将字符串转换为 Boolean  时，针对给定输入字符串生成的类型。</span><span class="sxs-lookup"><span data-stu-id="529da-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="529da-137">有效的字符串输入参数</span><span class="sxs-lookup"><span data-stu-id="529da-137">Valid string input parameter</span></span>|<span data-ttu-id="529da-138">.NET Framework 输出类型</span><span class="sxs-lookup"><span data-stu-id="529da-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="529da-139">“true”</span><span class="sxs-lookup"><span data-stu-id="529da-139">"true"</span></span>|<span data-ttu-id="529da-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="529da-140">Boolean.True</span></span>|  
|<span data-ttu-id="529da-141">"1"</span><span class="sxs-lookup"><span data-stu-id="529da-141">"1"</span></span>|<span data-ttu-id="529da-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="529da-142">Boolean.True</span></span>|  
|<span data-ttu-id="529da-143">“false”</span><span class="sxs-lookup"><span data-stu-id="529da-143">"false"</span></span>|<span data-ttu-id="529da-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="529da-144">Boolean.False</span></span>|  
|<span data-ttu-id="529da-145">“0”</span><span class="sxs-lookup"><span data-stu-id="529da-145">"0"</span></span>|<span data-ttu-id="529da-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="529da-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="529da-147">例如，给定以下 XML：</span><span class="sxs-lookup"><span data-stu-id="529da-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="529da-148">**输入**</span><span class="sxs-lookup"><span data-stu-id="529da-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 <span data-ttu-id="529da-149">两者均可通过下列代码理解，其中 bvalue  为 System.Boolean.True  ：</span><span class="sxs-lookup"><span data-stu-id="529da-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="529da-150">将字符串转换为 Single</span><span class="sxs-lookup"><span data-stu-id="529da-150">String to Single</span></span>  
 <span data-ttu-id="529da-151">下表列出了使用 ToSingle  方法将字符串转换为 Single  时，针对给定输入字符串生成的类型。</span><span class="sxs-lookup"><span data-stu-id="529da-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="529da-152">有效的字符串输入参数</span><span class="sxs-lookup"><span data-stu-id="529da-152">Valid string input parameter</span></span>|<span data-ttu-id="529da-153">.NET Framework 输出类型</span><span class="sxs-lookup"><span data-stu-id="529da-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="529da-154">“INF”</span><span class="sxs-lookup"><span data-stu-id="529da-154">"INF"</span></span>|<span data-ttu-id="529da-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="529da-156">“-INF”</span><span class="sxs-lookup"><span data-stu-id="529da-156">"-INF"</span></span>|<span data-ttu-id="529da-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="529da-158">将字符串转换为 Double</span><span class="sxs-lookup"><span data-stu-id="529da-158">String to Double</span></span>  
 <span data-ttu-id="529da-159">下表列出了使用 ToDouble  方法将字符串转换为 Single  时，针对给定输入字符串生成的类型。</span><span class="sxs-lookup"><span data-stu-id="529da-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="529da-160">有效的字符串输入参数</span><span class="sxs-lookup"><span data-stu-id="529da-160">Valid string input parameter</span></span>|<span data-ttu-id="529da-161">.NET Framework 输出类型</span><span class="sxs-lookup"><span data-stu-id="529da-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="529da-162">“INF”</span><span class="sxs-lookup"><span data-stu-id="529da-162">"INF"</span></span>|<span data-ttu-id="529da-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="529da-164">“-INF”</span><span class="sxs-lookup"><span data-stu-id="529da-164">"-INF"</span></span>|<span data-ttu-id="529da-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="529da-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="529da-166">下面的代码写出 `<Infinity>INF</Infinity>`：</span><span class="sxs-lookup"><span data-stu-id="529da-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="529da-167">请参阅</span><span class="sxs-lookup"><span data-stu-id="529da-167">See also</span></span>

- [<span data-ttu-id="529da-168">XML 数据类型转换</span><span class="sxs-lookup"><span data-stu-id="529da-168">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="529da-169">将 .NET Framework 类型转换为字符串</span><span class="sxs-lookup"><span data-stu-id="529da-169">Converting .NET Framework Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
