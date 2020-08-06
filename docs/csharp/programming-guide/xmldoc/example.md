---
title: <example> - C# 编程指南
description: 了解 XML <example> 标记。 借助此标记，可以指定如何使用方法或其他库成员的示例。
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381523"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="67b32-105">\<example>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="67b32-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="67b32-106">语法</span><span class="sxs-lookup"><span data-stu-id="67b32-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="67b32-107">参数</span><span class="sxs-lookup"><span data-stu-id="67b32-107">Parameters</span></span>

- `description`

  <span data-ttu-id="67b32-108">代码示例的说明。</span><span class="sxs-lookup"><span data-stu-id="67b32-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="67b32-109">备注</span><span class="sxs-lookup"><span data-stu-id="67b32-109">Remarks</span></span>

<span data-ttu-id="67b32-110">借助 `<example>` 标记，可以指定如何使用方法或其他库成员的示例。</span><span class="sxs-lookup"><span data-stu-id="67b32-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="67b32-111">这通常涉及到使用 [\<code>](./code.md) 标记。</span><span class="sxs-lookup"><span data-stu-id="67b32-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="67b32-112">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="67b32-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="67b32-113">示例</span><span class="sxs-lookup"><span data-stu-id="67b32-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="67b32-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67b32-114">See also</span></span>

- [<span data-ttu-id="67b32-115">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="67b32-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="67b32-116">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="67b32-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
