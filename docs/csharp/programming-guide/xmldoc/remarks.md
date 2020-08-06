---
title: <remarks> - C# 编程指南
description: 了解 XML <remarks> 标记。 此标记用于添加有关某个类型的信息，从而补充由以下指定的信息： <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381497"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="ab731-106">\<remarks>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="ab731-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab731-107">语法</span><span class="sxs-lookup"><span data-stu-id="ab731-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="ab731-108">参数</span><span class="sxs-lookup"><span data-stu-id="ab731-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="ab731-109">对成员的说明。</span><span class="sxs-lookup"><span data-stu-id="ab731-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab731-110">备注</span><span class="sxs-lookup"><span data-stu-id="ab731-110">Remarks</span></span>

<span data-ttu-id="ab731-111">`<remarks>` 标记用于添加有关某个类型的信息，从而补充由 [\<summary>](./summary.md) 指定的信息。</span><span class="sxs-lookup"><span data-stu-id="ab731-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="ab731-112">此信息显示在对象浏览器窗口中。</span><span class="sxs-lookup"><span data-stu-id="ab731-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="ab731-113">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="ab731-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="ab731-114">示例</span><span class="sxs-lookup"><span data-stu-id="ab731-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="ab731-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab731-115">See also</span></span>

- [<span data-ttu-id="ab731-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="ab731-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ab731-117">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="ab731-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
