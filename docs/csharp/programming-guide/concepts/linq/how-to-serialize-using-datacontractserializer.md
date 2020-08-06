---
title: 如何使用 DataContractSerializer 进行序列化 (C#)
description: 了解如何使用 DataContractSerializer 序列化对象。 参阅示例，该示例创建一些对象，然后将它们序列化为文本文件，接着对它们进行反序列化。
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: b713f36cde594f7cd7011073345d33c6f46585e0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301523"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="a28da-104">如何使用 DataContractSerializer 进行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="a28da-104">How to serialize using DataContractSerializer (C#)</span></span>
<span data-ttu-id="a28da-105">本主题显示一个使用 <xref:System.Runtime.Serialization.DataContractSerializer> 进行序列化和反序列化的示例。</span><span class="sxs-lookup"><span data-stu-id="a28da-105">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a28da-106">示例</span><span class="sxs-lookup"><span data-stu-id="a28da-106">Example</span></span>  
 <span data-ttu-id="a28da-107">下面的示例创建多个包含 <xref:System.Xml.Linq.XElement> 对象的对象。</span><span class="sxs-lookup"><span data-stu-id="a28da-107">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="a28da-108">然后将它们序列化为文本文件，接着从文本文件对它们进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="a28da-108">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Linq;  
using System.IO;  
using System.Runtime.Serialization;  
  
public class XLinqTest  
{  
    public static void Main()  
    {  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
        Test<XElementNullContainer>(new XElementNullContainer());  
    }  
  
    public static void Test<T>(T obj)  
    {  
        DataContractSerializer s = new DataContractSerializer(typeof(T));  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))  
        {  
            Console.WriteLine("Testing for type: {0}", typeof(T));
            s.WriteObject(fs, obj);  
        }  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))  
        {  
            object s2 = s.ReadObject(fs);  
            if (s2 == null)  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");  
            else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());  
        }  
    }  
  
    public static XElement CreateXElement()  
    {  
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));  
    }  
}  
  
[DataContract]  
public class XElementContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
}  
  
[DataContract]  
public class XElementNullContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
        member = null;  
    }  
}  
```  
  
 <span data-ttu-id="a28da-109">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a28da-109">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
