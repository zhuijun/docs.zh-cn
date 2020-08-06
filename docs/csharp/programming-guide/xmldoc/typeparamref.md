---
title: <typeparamref> - C# 编程指南
description: 了解 XML <typeparamref> 标记。 通过此标记，文档文件的使用者可显著设置字体格式，例如采用斜体。
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380717"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="4484d-104">\<typeparamref>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4484d-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4484d-105">语法</span><span class="sxs-lookup"><span data-stu-id="4484d-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="4484d-106">parameters</span><span class="sxs-lookup"><span data-stu-id="4484d-106">Parameters</span></span>

- `name`

  <span data-ttu-id="4484d-107">类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="4484d-107">The name of the type parameter.</span></span> <span data-ttu-id="4484d-108">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="4484d-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="4484d-109">备注</span><span class="sxs-lookup"><span data-stu-id="4484d-109">Remarks</span></span>

<span data-ttu-id="4484d-110">有关泛型类型中的类型参数及方法的详细信息，请参阅[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4484d-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="4484d-111">通过此标记，文档文件的使用者可显著设置字体格式，例如采用斜体。</span><span class="sxs-lookup"><span data-stu-id="4484d-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="4484d-112">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="4484d-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4484d-113">示例</span><span class="sxs-lookup"><span data-stu-id="4484d-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="4484d-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="4484d-114">See also</span></span>

- [<span data-ttu-id="4484d-115">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="4484d-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4484d-116">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="4484d-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
