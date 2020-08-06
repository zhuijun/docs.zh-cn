---
title: <typeparam> - C# 编程指南
description: 了解 XML <typeparam> 标记。 在泛型类型或方法声明的注释中使用了此标记来描述类型参数。
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380782"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="e87dc-105">\<typeparam>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="e87dc-105">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e87dc-106">语法</span><span class="sxs-lookup"><span data-stu-id="e87dc-106">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="e87dc-107">parameters</span><span class="sxs-lookup"><span data-stu-id="e87dc-107">Parameters</span></span>

- `name`

  <span data-ttu-id="e87dc-108">类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="e87dc-108">The name of the type parameter.</span></span> <span data-ttu-id="e87dc-109">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="e87dc-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="e87dc-110">类型参数的说明。</span><span class="sxs-lookup"><span data-stu-id="e87dc-110">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="e87dc-111">备注</span><span class="sxs-lookup"><span data-stu-id="e87dc-111">Remarks</span></span>

<span data-ttu-id="e87dc-112">在泛型类型或方法声明的注释中，应使用 `<typeparam>` 标记来描述类型参数。</span><span class="sxs-lookup"><span data-stu-id="e87dc-112">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="e87dc-113">为泛型类型或方法的每个类型参数添加标记。</span><span class="sxs-lookup"><span data-stu-id="e87dc-113">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="e87dc-114">有关详细信息，请参阅[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e87dc-114">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="e87dc-115">`<typeparam>` 标记的文本将显示在 IntelliSense、[对象浏览器窗口](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)代码注释 Web 报表。</span><span class="sxs-lookup"><span data-stu-id="e87dc-115">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="e87dc-116">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="e87dc-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="e87dc-117">示例</span><span class="sxs-lookup"><span data-stu-id="e87dc-117">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="e87dc-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="e87dc-118">See also</span></span>

- [<span data-ttu-id="e87dc-119">C# 参考</span><span class="sxs-lookup"><span data-stu-id="e87dc-119">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e87dc-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="e87dc-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e87dc-121">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="e87dc-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
