---
title: <c> - C# 编程指南
description: 了解 XML <c> 标记。 此标记将说明中的单行文本标记为代码，而 <code> indicates multiple lines.
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382017"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="2086e-104">\<c>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2086e-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2086e-105">语法</span><span class="sxs-lookup"><span data-stu-id="2086e-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="2086e-106">参数</span><span class="sxs-lookup"><span data-stu-id="2086e-106">Parameters</span></span>

- `text`

  <span data-ttu-id="2086e-107">要指示为代码的文本。</span><span class="sxs-lookup"><span data-stu-id="2086e-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2086e-108">备注</span><span class="sxs-lookup"><span data-stu-id="2086e-108">Remarks</span></span>

<span data-ttu-id="2086e-109">使用 `<c>` 标记可以指示应将说明内的文本标记为代码。</span><span class="sxs-lookup"><span data-stu-id="2086e-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="2086e-110">使用 [\<code>](./code.md) 指示作为代码的多行文本。</span><span class="sxs-lookup"><span data-stu-id="2086e-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="2086e-111">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="2086e-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2086e-112">示例</span><span class="sxs-lookup"><span data-stu-id="2086e-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="2086e-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="2086e-113">See also</span></span>

- [<span data-ttu-id="2086e-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2086e-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2086e-115">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="2086e-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
