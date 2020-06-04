---
title: XML 数据类型的转换
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b6e6f2c4b28e9220727bf0fe1a958a7b69111571
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202158"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="7e8ec-102">XML 数据类型的转换</span><span class="sxs-lookup"><span data-stu-id="7e8ec-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="7e8ec-103">XmlConvert 类中的大多数方法都可用于在字符串和强类型格式之间转换数据。</span><span class="sxs-lookup"><span data-stu-id="7e8ec-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="7e8ec-104">这些方法与区域设置无关。</span><span class="sxs-lookup"><span data-stu-id="7e8ec-104">Methods are locale independent.</span></span> <span data-ttu-id="7e8ec-105">这意味着它们在执行转换时不考虑任何区域设置。</span><span class="sxs-lookup"><span data-stu-id="7e8ec-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="7e8ec-106">将字符串作为类型读取</span><span class="sxs-lookup"><span data-stu-id="7e8ec-106">Reading String as types</span></span>  
 <span data-ttu-id="7e8ec-107">下面的示例读取字符串，并将它转换为 DateTime 类型。</span><span class="sxs-lookup"><span data-stu-id="7e8ec-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="7e8ec-108">给定以下 XML 输入：</span><span class="sxs-lookup"><span data-stu-id="7e8ec-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="7e8ec-109">**输入**</span><span class="sxs-lookup"><span data-stu-id="7e8ec-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="7e8ec-110">下面的代码将字符串转换为 DateTime 格式：</span><span class="sxs-lookup"><span data-stu-id="7e8ec-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="7e8ec-111">将字符串作为类型写入</span><span class="sxs-lookup"><span data-stu-id="7e8ec-111">Writing Strings as types</span></span>  
 <span data-ttu-id="7e8ec-112">下面的示例读取 Int32，并将它转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="7e8ec-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="7e8ec-113">给定以下 XML 输入：</span><span class="sxs-lookup"><span data-stu-id="7e8ec-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="7e8ec-114">**输入**</span><span class="sxs-lookup"><span data-stu-id="7e8ec-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="7e8ec-115">下面的代码将 Int32 转换为 String：</span><span class="sxs-lookup"><span data-stu-id="7e8ec-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e8ec-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="7e8ec-116">See also</span></span>

- [<span data-ttu-id="7e8ec-117">将字符串转换为 .NET Framework 数据类型</span><span class="sxs-lookup"><span data-stu-id="7e8ec-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="7e8ec-118">将 .NET Framework 类型转换为字符串</span><span class="sxs-lookup"><span data-stu-id="7e8ec-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
