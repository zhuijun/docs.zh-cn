---
title: 如何执行文本到 XML 的流式转换 (C#)
description: 了解如何使用 C# 执行文本到 XML 的流式转换，在这种情况下，你可以一次流式处理一行文本文件，并使用 LINQ 查询来处理文本文件。
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: f933064be70d39b59cf7dbe51b4ee92e5226647a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104751"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>如何执行文本到 XML 的流式转换 (C#)

处理文本文件的一种方法是编写使用 `yield return` 构造一次流式处理一行文本文件的扩展方法。 然后可以编写以迟缓延迟方式处理文本文件的 LINQ 查询。 如果之后使用 <xref:System.Xml.Linq.XStreamingElement> 对输出进行流式处理，则可以创建占用最少量内存的从文本文件到 XML 的转换，而不管源文本文件大小如何。

 关于流式转换存在一些告诫。 流式转换最适用于可以一次性处理整个文件并且可以按照源文档中的行顺序处理各行的情况。 如果必须多次处理文件或者必须在处理行之前对行进行排序，则将失去使用流式技术所具有的许多好处。

## <a name="example"></a>示例

 下面的文本文件 People.txt 是本示例的源文件。

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 下面的代码包含以延迟方式流式处理文本文件中各行的扩展方法。

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

 该示例产生下面的输出：

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XStreamingElement>
