---
title: <include> - C# 编程指南
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: bf41019c775fed25afe4bdb9453a8e52f44856b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287345"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="567c2-102">\<include>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="567c2-102">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="567c2-103">语法</span><span class="sxs-lookup"><span data-stu-id="567c2-103">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="567c2-104">参数</span><span class="sxs-lookup"><span data-stu-id="567c2-104">Parameters</span></span>

- `filename`

  <span data-ttu-id="567c2-105">包含文档的 XML 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="567c2-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="567c2-106">可使用相对于源代码文件的路径限定文件名。</span><span class="sxs-lookup"><span data-stu-id="567c2-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="567c2-107">使用单引号 (' ') 将 `filename` 括起来。</span><span class="sxs-lookup"><span data-stu-id="567c2-107">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="567c2-108">`filename` 中标记的路径，它指向标记 `name`。</span><span class="sxs-lookup"><span data-stu-id="567c2-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="567c2-109">使用单引号 (' ') 将路径括起来。</span><span class="sxs-lookup"><span data-stu-id="567c2-109">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="567c2-110">标记中的名称说明符（位于注释之前）；`name` 将有 `id`。</span><span class="sxs-lookup"><span data-stu-id="567c2-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="567c2-111">标记的 ID（位于注释之前）。</span><span class="sxs-lookup"><span data-stu-id="567c2-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="567c2-112">用双引号 (" ") 将 ID 括起来。</span><span class="sxs-lookup"><span data-stu-id="567c2-112">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="567c2-113">备注</span><span class="sxs-lookup"><span data-stu-id="567c2-113">Remarks</span></span>

<span data-ttu-id="567c2-114">通过 `<include>` 标记，可在其他文件中引用描述源代码中类型和成员的注释。</span><span class="sxs-lookup"><span data-stu-id="567c2-114">The `<include>` tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="567c2-115">这是对直接在源代码文件中放入文档注释的替代方法。</span><span class="sxs-lookup"><span data-stu-id="567c2-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="567c2-116">通过将文档放入不同文件，可以单独从源代码对文档应用源控件。</span><span class="sxs-lookup"><span data-stu-id="567c2-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="567c2-117">一人可以签出源代码文件，而其他人可以签出文档文件。</span><span class="sxs-lookup"><span data-stu-id="567c2-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="567c2-118">`<include>` 标记使用 XML XPath 语法。</span><span class="sxs-lookup"><span data-stu-id="567c2-118">The `<include>` tag uses the XML XPath syntax.</span></span> <span data-ttu-id="567c2-119">有关如何自定义 `<include>` 用法的信息，请参阅 XPath 文档。</span><span class="sxs-lookup"><span data-stu-id="567c2-119">Refer to XPath documentation for ways to customize your `<include>` use.</span></span>

## <a name="example"></a><span data-ttu-id="567c2-120">示例</span><span class="sxs-lookup"><span data-stu-id="567c2-120">Example</span></span>

<span data-ttu-id="567c2-121">这是多文件示例。</span><span class="sxs-lookup"><span data-stu-id="567c2-121">This is a multifile example.</span></span> <span data-ttu-id="567c2-122">下面是第一个文件，使用 `<include>`。</span><span class="sxs-lookup"><span data-stu-id="567c2-122">The following is the first file, which uses `<include>`.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="567c2-123">第二个文件是 xml_include_tag.doc，包含下列文档注释。</span><span class="sxs-lookup"><span data-stu-id="567c2-123">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a><span data-ttu-id="567c2-124">程序输出</span><span class="sxs-lookup"><span data-stu-id="567c2-124">Program output</span></span>

<span data-ttu-id="567c2-125">使用以下命令行编译 Test 和 Test2 类时，便会生成下面的输出：`-doc:DocFileName.xml.`。在 Visual Studio 的项目设计器的“生成”窗格中，指定 XML 文档注释选项。</span><span class="sxs-lookup"><span data-stu-id="567c2-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="567c2-126">当 C# 编译器发现 `<include>` 标记时，它将在 xml_include_tag.doc（而不是当前源文件）中搜索文档注释。</span><span class="sxs-lookup"><span data-stu-id="567c2-126">When the C# compiler sees the `<include>` tag, it searches for documentation comments in *xml_include_tag.doc* instead of the current source file.</span></span> <span data-ttu-id="567c2-127">然后编译器生成 DocFileName.xml，这是由文档工具（如 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB)）所使用的文件，用于生成最终文档。</span><span class="sxs-lookup"><span data-stu-id="567c2-127">The compiler then generates *DocFileName.xml*, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a><span data-ttu-id="567c2-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="567c2-128">See also</span></span>

- [<span data-ttu-id="567c2-129">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="567c2-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="567c2-130">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="567c2-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
