---
title: 如何：将对象数据写入 XML 文件
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 9608a48cb8b3fac1c71affa7a0a17e9789f94b18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413149"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="f6a74-102">如何：将对象数据写入 XML 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6a74-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="f6a74-103">本示例使用 <xref:System.Xml.Serialization.XmlSerializer> 类从某个类将对象写入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="f6a74-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6a74-104">示例</span><span class="sxs-lookup"><span data-stu-id="f6a74-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="f6a74-105">编译代码</span><span class="sxs-lookup"><span data-stu-id="f6a74-105">Compile the code</span></span>  
 <span data-ttu-id="f6a74-106">类必须有一个公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="f6a74-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6a74-107">可靠编程</span><span class="sxs-lookup"><span data-stu-id="f6a74-107">Robust Programming</span></span>  
 <span data-ttu-id="f6a74-108">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="f6a74-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f6a74-109">进行序列化的类没有公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="f6a74-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="f6a74-110">文件存在且为只读 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="f6a74-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f6a74-111">路径过长 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="f6a74-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f6a74-112">磁盘已满 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="f6a74-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f6a74-113">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="f6a74-113">.NET Framework Security</span></span>  
 <span data-ttu-id="f6a74-114">此示例在文件尚未存在时创建新文件。</span><span class="sxs-lookup"><span data-stu-id="f6a74-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="f6a74-115">如果某个应用程序需要创建文件，则该应用程序需要针对文件夹的 `Create` 访问权限。</span><span class="sxs-lookup"><span data-stu-id="f6a74-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="f6a74-116">如果文件已存在，则该应用程序只需要 `Write` 访问权限（这是较弱的特权）。</span><span class="sxs-lookup"><span data-stu-id="f6a74-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="f6a74-117">如有可能，在部署过程中创建文件，并且仅授予针对单个文件的 `Read` 访问权限（而不是针对 `Create` 文件夹的访问权限）会更加安全。</span><span class="sxs-lookup"><span data-stu-id="f6a74-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a74-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6a74-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="f6a74-119">如何：读取 XML 文件中的对象数据 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6a74-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](how-to-read-object-data-from-an-xml-file.md)
- <span data-ttu-id="f6a74-120">序列化 (Visual Basic)[](index.md)</span><span class="sxs-lookup"><span data-stu-id="f6a74-120">[Serialization (Visual Basic)](index.md)</span></span>
