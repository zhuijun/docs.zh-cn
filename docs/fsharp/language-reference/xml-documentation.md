---
title: XML 文档
description: '了解有关 F # 的支持，以便从注释生成文档。'
ms.date: 05/16/2016
ms.openlocfilehash: 03d14cef910d149f0c7a2f3a49c8cf4606ac5305
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556572"
---
# <a name="xml-documentation"></a>XML 文档

可以在 F # 中生成三斜杠 (///) 代码注释中的文档。 XML 注释可以在代码文件中的声明之前 () 或签名 ( fsi.exe) 文件中。

## <a name="generating-documentation-from-comments"></a>从注释生成文档

F # 中通过注释生成文档的支持与其他 .NET Framework 语言的支持相同。 与其他 .NET Framework 语言一样， [-doc 编译器选项](./compiler-options.md) 使你能够生成一个 XML 文件，该文件包含可通过使用 [DocFX](https://dotnet.github.io/docfx/) 或 [Sandcastle](https://github.com/EWSoftware/SHFB)等工具转换为文档的信息。 使用与用其他 .NET Framework 语言编写的程序集设计的工具所生成的文档通常会生成一个基于编译形式的 F # 构造的 Api 视图。 除非专门支持 F # 的工具，否则这些工具生成的文档与 API 的 F # 视图不匹配。

有关如何从 XML 生成文档的详细信息，请参阅 [Xml 文档注释 &#40;C&#35; 编程指南&#41;](../../csharp/programming-guide/xmldoc/index.md)。

## <a name="recommended-tags"></a>建议的标记

可以通过两种方法来编写 XML 文档注释。 一种方式是仅在三斜杠注释中直接编写文档，而无需使用 XML 标记。 如果执行此操作，整个注释文本将被视为紧随其后的代码构造的摘要文档。 如果只想编写每个构造的简短摘要，请使用此方法。 另一种方法是使用 XML 标记来提供更多结构化文档。 第二种方法允许您为简短摘要指定单独的注释、附加备注、每个参数和类型参数的文档以及引发的异常以及对返回值的说明。 下表描述了在 F # XML 代码注释中识别的 XML 标记。

|标记语法|说明|
|----------|-----------|
|**\<c\>**_全文_**\</c\>**|指定 *文本* 为代码。 文档生成器可以使用此标记以适用于代码的字体显示文本。|
|**\<summary\>**_全文_**\</summary\>**|指定 *文本* 为程序元素的简短说明。 描述通常是一两个句子。|
|**\<remarks\>**_全文_**\</remarks\>**|指定 *文本* 包含有关程序元素的补充信息。|
|**\<param name="**_name_**"\>**_2008_**\</param\>**|指定函数或方法参数的名称和说明。|
|**\<typeparam name="**_name_**"\>**_2008_**\</typeparam\>**|指定类型参数的名称和说明。|
|**\<returns\>**_全文_**\</returns\>**|指定 *文本* 描述函数或方法的返回值。|
|**\<exception cref="**_type_**"\>**_2008_**\</exception\>**|指定可以生成的异常的类型以及引发此异常的情况。|
|**\<see cref="**_reference_**"\>**_全文_**\</see\>**|指定指向其他程序元素的内联链接。 *引用*是显示在 XML 文档文件中的名称。 *文本*是链接中显示的文本。|
|**\<seealso cref="**_reference_**"/\>**|指定另一种类型的文档的链接。 *引用*是显示在 XML 文档文件中的名称。 另请参阅链接通常显示在文档页的底部。|
|**\<para\>**_全文_**\</para\>**|指定文本段落。 用于分隔 **备注** 标记内的文本。|

## <a name="example"></a>示例

### <a name="description"></a>说明

下面是签名文件中的典型 XML 文档注释。

### <a name="code"></a>代码

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>示例

### <a name="description"></a>说明

下面的示例显示了不带 XML 标记的替代方法。 在此示例中，注释中的整个文本都被视为一个摘要。 请注意，如果未显式指定摘要标记，则不应指定其他标记，如 **param** 或 **返回** 标记。

### <a name="code"></a>代码

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)
- [编译器选项](compiler-options.md)
