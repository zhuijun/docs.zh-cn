---
title: <c> - C# 编程指南
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
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287462"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="9ff1d-102">\<c>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="9ff1d-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ff1d-103">语法</span><span class="sxs-lookup"><span data-stu-id="9ff1d-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="9ff1d-104">参数</span><span class="sxs-lookup"><span data-stu-id="9ff1d-104">Parameters</span></span>

- `text`

  <span data-ttu-id="9ff1d-105">要指示为代码的文本。</span><span class="sxs-lookup"><span data-stu-id="9ff1d-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ff1d-106">备注</span><span class="sxs-lookup"><span data-stu-id="9ff1d-106">Remarks</span></span>

<span data-ttu-id="9ff1d-107">使用 `<c>` 标记可以指示应将说明内的文本标记为代码。</span><span class="sxs-lookup"><span data-stu-id="9ff1d-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="9ff1d-108">使用 [\<code>](./code.md) 指示作为代码的多行文本。</span><span class="sxs-lookup"><span data-stu-id="9ff1d-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="9ff1d-109">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="9ff1d-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9ff1d-110">示例</span><span class="sxs-lookup"><span data-stu-id="9ff1d-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="9ff1d-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ff1d-111">See also</span></span>

- [<span data-ttu-id="9ff1d-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="9ff1d-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="9ff1d-113">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="9ff1d-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
