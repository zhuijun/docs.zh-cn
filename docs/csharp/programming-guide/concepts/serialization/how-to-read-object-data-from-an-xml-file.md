---
title: 如何从 XML 文件读取对象数据 (C#)
description: 本 C# 示例使用 XmlSerializer 类读取之前写入 XML 文件的对象数据。
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 8d607424201cfad08df1c5ffbfb66a114b31886d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178757"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="be77b-103">如何从 XML 文件读取对象数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="be77b-103">How to read object data from an XML file (C#)</span></span>

<span data-ttu-id="be77b-104">本示例使用 <xref:System.Xml.Serialization.XmlSerializer> 类读取之前写入 XML 文件的对象数据。</span><span class="sxs-lookup"><span data-stu-id="be77b-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be77b-105">示例</span><span class="sxs-lookup"><span data-stu-id="be77b-105">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be77b-106">编译代码</span><span class="sxs-lookup"><span data-stu-id="be77b-106">Compiling the Code</span></span>  

<span data-ttu-id="be77b-107">将文件名称“c:\temp\SerializationOverview.xml”替换为包含序列化数据的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="be77b-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="be77b-108">有关序列化数据的详细信息，请参阅[如何将对象数据写入 XML 文件 (C#)](./how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="be77b-108">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="be77b-109">类必须有一个公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="be77b-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="be77b-110">只有公共属性和字段才会进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="be77b-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="be77b-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="be77b-111">Robust Programming</span></span>  

 <span data-ttu-id="be77b-112">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="be77b-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="be77b-113">进行序列化的类没有公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="be77b-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="be77b-114">文件中的数据不表示要进行反序列化的类中的数据。</span><span class="sxs-lookup"><span data-stu-id="be77b-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="be77b-115">该文件不存在 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="be77b-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="be77b-116">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="be77b-116">.NET Security</span></span>  

 <span data-ttu-id="be77b-117">始终验证输入，并且绝不会反序列化来自不受信任源的数据。</span><span class="sxs-lookup"><span data-stu-id="be77b-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="be77b-118">重新创建的对象会在具有对它进行反序列化的代码的权限的本地计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="be77b-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="be77b-119">在应用程序中使用输入的数据之前，需验证所有的输入内容。</span><span class="sxs-lookup"><span data-stu-id="be77b-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be77b-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="be77b-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="be77b-121">如何将对象数据写入 XML 文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="be77b-121">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="be77b-122">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="be77b-122">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="be77b-123">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="be77b-123">C# Programming Guide</span></span>](../../index.md)
