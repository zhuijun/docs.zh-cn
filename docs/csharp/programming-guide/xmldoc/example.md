---
title: <example> - C# 编程指南
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: e8d26f82562cc5140662f5b32ea9fedf5481d8f8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287374"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="61926-102">\<example>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="61926-102">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="61926-103">语法</span><span class="sxs-lookup"><span data-stu-id="61926-103">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="61926-104">参数</span><span class="sxs-lookup"><span data-stu-id="61926-104">Parameters</span></span>

- `description`

  <span data-ttu-id="61926-105">代码示例的说明。</span><span class="sxs-lookup"><span data-stu-id="61926-105">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="61926-106">备注</span><span class="sxs-lookup"><span data-stu-id="61926-106">Remarks</span></span>

<span data-ttu-id="61926-107">借助 `<example>` 标记，可以指定如何使用方法或其他库成员的示例。</span><span class="sxs-lookup"><span data-stu-id="61926-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="61926-108">这通常涉及到使用 [\<code>](./code.md) 标记。</span><span class="sxs-lookup"><span data-stu-id="61926-108">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="61926-109">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="61926-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="61926-110">示例</span><span class="sxs-lookup"><span data-stu-id="61926-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="61926-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="61926-111">See also</span></span>

- [<span data-ttu-id="61926-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="61926-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="61926-113">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="61926-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
