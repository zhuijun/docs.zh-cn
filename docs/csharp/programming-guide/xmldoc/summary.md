---
title: <summary> - C# 编程指南
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: f6984c60e6a7132e94c5c91837535484b12f93c5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590613"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="84380-102">\<summary>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="84380-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="84380-103">语法</span><span class="sxs-lookup"><span data-stu-id="84380-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="84380-104">参数</span><span class="sxs-lookup"><span data-stu-id="84380-104">Parameters</span></span>

- `description`

  <span data-ttu-id="84380-105">对象的摘要。</span><span class="sxs-lookup"><span data-stu-id="84380-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="84380-106">备注</span><span class="sxs-lookup"><span data-stu-id="84380-106">Remarks</span></span>

<span data-ttu-id="84380-107">`<summary>` 标记应当用于描述类型或类型成员。</span><span class="sxs-lookup"><span data-stu-id="84380-107">The `<summary>` tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="84380-108">使用 [\<remarks>](./remarks.md) 可针对某个类型说明添加补充信息。</span><span class="sxs-lookup"><span data-stu-id="84380-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="84380-109">使用 [cref 属性](./cref-attribute.md)可启用文档工具（如 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB)）来创建指向代码元素的文档页的内部超链接。</span><span class="sxs-lookup"><span data-stu-id="84380-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="84380-110">`<summary>` 标记的文本是唯一有关 IntelliSense 中的类型的信息源，它也显示在对象浏览器窗口中。</span><span class="sxs-lookup"><span data-stu-id="84380-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="84380-111">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="84380-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="84380-112">若要基于编译器生成的文件创建最终文档，可以创建一个自定义工具，也可以使用 [DocFX](https://dotnet.github.io/docfx/) 或 [Sandcastle](https://github.com/EWSoftware/SHFB) 等工具。</span><span class="sxs-lookup"><span data-stu-id="84380-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="84380-113">示例</span><span class="sxs-lookup"><span data-stu-id="84380-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="84380-114">前面的示例生成下面的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="84380-114">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            </summary>
            <seealso cref="M:TestClass.Main"/>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="84380-115">示例</span><span class="sxs-lookup"><span data-stu-id="84380-115">Example</span></span>

<span data-ttu-id="84380-116">下面的示例演示如何对泛型类型进行 `cref` 引用。</span><span class="sxs-lookup"><span data-stu-id="84380-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="84380-117">前面的示例生成下面的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="84380-117">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="84380-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="84380-118">See also</span></span>

- [<span data-ttu-id="84380-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="84380-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="84380-120">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="84380-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
