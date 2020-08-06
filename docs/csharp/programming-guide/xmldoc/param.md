---
title: <param> - C# 编程指南
description: 了解 XML <param> 标记。 在方法声明的注释中使用了此标记来描述方法参数之一。
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381549"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="f4b27-105">\<param>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="f4b27-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4b27-106">语法</span><span class="sxs-lookup"><span data-stu-id="f4b27-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="f4b27-107">参数</span><span class="sxs-lookup"><span data-stu-id="f4b27-107">Parameters</span></span>

- `name`

  <span data-ttu-id="f4b27-108">方法参数的名称。</span><span class="sxs-lookup"><span data-stu-id="f4b27-108">The name of a method parameter.</span></span> <span data-ttu-id="f4b27-109">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="f4b27-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="f4b27-110">参数的说明。</span><span class="sxs-lookup"><span data-stu-id="f4b27-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4b27-111">备注</span><span class="sxs-lookup"><span data-stu-id="f4b27-111">Remarks</span></span>

<span data-ttu-id="f4b27-112">在方法声明的注释中，应使用 `<param>` 标记来描述方法参数之一。</span><span class="sxs-lookup"><span data-stu-id="f4b27-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="f4b27-113">若要记录多个参数，请使用多个 `<param>` 标记。</span><span class="sxs-lookup"><span data-stu-id="f4b27-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="f4b27-114">`<param>` 标记的文本显示在 IntelliSense、对象浏览器和代码注释 Web 报表中。</span><span class="sxs-lookup"><span data-stu-id="f4b27-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="f4b27-115">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="f4b27-115">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f4b27-116">示例</span><span class="sxs-lookup"><span data-stu-id="f4b27-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="f4b27-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="f4b27-117">See also</span></span>

- [<span data-ttu-id="f4b27-118">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="f4b27-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f4b27-119">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="f4b27-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
