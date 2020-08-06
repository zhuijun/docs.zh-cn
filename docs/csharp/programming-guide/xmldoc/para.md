---
title: <para> - C# 编程指南
description: 了解 XML <para> 标记。 使用此标记，可以将结构添加到另一个标记中的文本，例如 <summary>, <remarks>或 <returns>.
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: 146078bcb556b4085724ddcdac561ea868ab0481
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381848"
---
# <a name="para-c-programming-guide"></a><span data-ttu-id="b56cc-108">\<para>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="b56cc-108">\<para> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b56cc-109">语法</span><span class="sxs-lookup"><span data-stu-id="b56cc-109">Syntax</span></span>

```xml
<para>content</para>
```

## <a name="parameters"></a><span data-ttu-id="b56cc-110">参数</span><span class="sxs-lookup"><span data-stu-id="b56cc-110">Parameters</span></span>

- `content`

  <span data-ttu-id="b56cc-111">段落文本。</span><span class="sxs-lookup"><span data-stu-id="b56cc-111">The text of the paragraph.</span></span>

## <a name="remarks"></a><span data-ttu-id="b56cc-112">备注</span><span class="sxs-lookup"><span data-stu-id="b56cc-112">Remarks</span></span>

<span data-ttu-id="b56cc-113">`<para>` 标记用于标记内，例如 [\<summary>](./summary.md)、[\<remarks>](./remarks.md) 或 [\<returns>](./returns.md)，允许向文本添加结构。</span><span class="sxs-lookup"><span data-stu-id="b56cc-113">The `<para>` tag is for use inside a tag, such as [\<summary>](./summary.md), [\<remarks>](./remarks.md), or [\<returns>](./returns.md), and lets you add structure to the text.</span></span>

<span data-ttu-id="b56cc-114">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="b56cc-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b56cc-115">示例</span><span class="sxs-lookup"><span data-stu-id="b56cc-115">Example</span></span>

<span data-ttu-id="b56cc-116">有关使用 `<para>` 的示例，请参阅 [\<summary>](./summary.md)。</span><span class="sxs-lookup"><span data-stu-id="b56cc-116">See [\<summary>](./summary.md) for an example of using `<para>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b56cc-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="b56cc-117">See also</span></span>

- [<span data-ttu-id="b56cc-118">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="b56cc-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b56cc-119">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="b56cc-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
