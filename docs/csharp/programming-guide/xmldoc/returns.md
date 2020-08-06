---
title: <returns> - C# 编程指南
description: 了解 XML <returns> 标记。 在方法声明的注释中使用了此标记来描述返回值。
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381393"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="2ef83-105">\<returns>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2ef83-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ef83-106">语法</span><span class="sxs-lookup"><span data-stu-id="2ef83-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="2ef83-107">参数</span><span class="sxs-lookup"><span data-stu-id="2ef83-107">Parameters</span></span>

- `description`

  <span data-ttu-id="2ef83-108">返回值的说明。</span><span class="sxs-lookup"><span data-stu-id="2ef83-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ef83-109">备注</span><span class="sxs-lookup"><span data-stu-id="2ef83-109">Remarks</span></span>

<span data-ttu-id="2ef83-110">在方法声明的注释中应使用 `<returns>` 标记来描述返回值。</span><span class="sxs-lookup"><span data-stu-id="2ef83-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="2ef83-111">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="2ef83-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2ef83-112">示例</span><span class="sxs-lookup"><span data-stu-id="2ef83-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="2ef83-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ef83-113">See also</span></span>

- [<span data-ttu-id="2ef83-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2ef83-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2ef83-115">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="2ef83-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
