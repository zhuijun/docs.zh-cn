---
title: 如何将对象数据写入 XML 文件 (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 6f18ae194d2ed70f633665a29772622319ea9493
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241989"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="d7126-102">如何将对象数据写入 XML 文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="d7126-102">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="d7126-103">本示例使用 <xref:System.Xml.Serialization.XmlSerializer> 类从某个类将对象写入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="d7126-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7126-104">示例</span><span class="sxs-lookup"><span data-stu-id="d7126-104">Example</span></span>  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7126-105">编译代码</span><span class="sxs-lookup"><span data-stu-id="d7126-105">Compiling the Code</span></span>  
 <span data-ttu-id="d7126-106">所序列化的类必须有一个公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="d7126-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d7126-107">可靠编程</span><span class="sxs-lookup"><span data-stu-id="d7126-107">Robust Programming</span></span>  
 <span data-ttu-id="d7126-108">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="d7126-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d7126-109">进行序列化的类没有公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="d7126-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="d7126-110">文件存在且为只读 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d7126-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d7126-111">路径过长 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="d7126-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d7126-112">磁盘已满 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d7126-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="d7126-113">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="d7126-113">.NET Security</span></span>  
 <span data-ttu-id="d7126-114">此示例在文件尚未存在时创建新文件。</span><span class="sxs-lookup"><span data-stu-id="d7126-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="d7126-115">如果某个应用程序需要创建文件，则该应用程序需要针对文件夹的 `Create` 访问权限。</span><span class="sxs-lookup"><span data-stu-id="d7126-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="d7126-116">如果文件已存在，则该应用程序只需要 `Write` 访问权限（这是较弱的特权）。</span><span class="sxs-lookup"><span data-stu-id="d7126-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="d7126-117">如有可能，在部署过程中创建文件，并且仅授予针对单个文件的 `Read` 访问权限（而不是针对 `Create` 文件夹的访问权限）会更加安全。</span><span class="sxs-lookup"><span data-stu-id="d7126-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7126-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="d7126-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="d7126-119">如何从 XML 文件读取对象数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="d7126-119">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="d7126-120">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="d7126-120">Serialization (C#)</span></span>](./index.md)
