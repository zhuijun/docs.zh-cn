---
title: <paramref> - C# 编程指南
description: 了解 XML <paramref> 标记。 此标记提供一种指示代码中的某个词为参数的方法。
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381835"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="240a6-104">\<paramref>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="240a6-104">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="240a6-105">语法</span><span class="sxs-lookup"><span data-stu-id="240a6-105">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="240a6-106">参数</span><span class="sxs-lookup"><span data-stu-id="240a6-106">Parameters</span></span>

- `name`

  <span data-ttu-id="240a6-107">要引用的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="240a6-107">The name of the parameter to refer to.</span></span> <span data-ttu-id="240a6-108">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="240a6-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="240a6-109">备注</span><span class="sxs-lookup"><span data-stu-id="240a6-109">Remarks</span></span>

<span data-ttu-id="240a6-110">`<paramref>` 标记提供一种方式，用于指示 `<summary>` 或 `<remarks>` 块等代码注释中的单词引用某个参数。</span><span class="sxs-lookup"><span data-stu-id="240a6-110">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="240a6-111">可以处理 XML 文件以明显的方式设置此单词的格式，如使用粗体或斜体。</span><span class="sxs-lookup"><span data-stu-id="240a6-111">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="240a6-112">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="240a6-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="240a6-113">示例</span><span class="sxs-lookup"><span data-stu-id="240a6-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="240a6-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="240a6-114">See also</span></span>

- [<span data-ttu-id="240a6-115">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="240a6-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="240a6-116">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="240a6-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
