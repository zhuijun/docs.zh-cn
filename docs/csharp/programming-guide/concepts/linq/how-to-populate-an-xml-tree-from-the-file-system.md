---
title: 如何从文件系统填充 XML 树 (C#)
description: 了解如何从以 C# 编写的文件系统填充 XML 树。 此示例填充 XML，然后查询树以计算所有文件的总大小。
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 676261656be7d306294c9912b75edcb51a31cccc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104762"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="06d01-104">如何从文件系统填充 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="06d01-104">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="06d01-105">XML 树有一种有用的常见应用，即作为层次结构名称/值数据存储区。</span><span class="sxs-lookup"><span data-stu-id="06d01-105">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="06d01-106">您可以使用层次结构数据填充 XML 树，然后对它进行查询、转换和序列化（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="06d01-106">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="06d01-107">在这种用法中，很多 XML 特定的语义（如命名空间和空白行为）都不重要。</span><span class="sxs-lookup"><span data-stu-id="06d01-107">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="06d01-108">相反，你将 XML 树用作内存中的小型单用户层次结构数据库。</span><span class="sxs-lookup"><span data-stu-id="06d01-108">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06d01-109">示例</span><span class="sxs-lookup"><span data-stu-id="06d01-109">Example</span></span>  
 <span data-ttu-id="06d01-110">下面的示例使用递归从本地文件系统填充 XML 树。</span><span class="sxs-lookup"><span data-stu-id="06d01-110">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="06d01-111">然后查询该树，计算树中所有文件的总大小。</span><span class="sxs-lookup"><span data-stu-id="06d01-111">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="06d01-112">本示例生成类似下面的输出：</span><span class="sxs-lookup"><span data-stu-id="06d01-112">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
