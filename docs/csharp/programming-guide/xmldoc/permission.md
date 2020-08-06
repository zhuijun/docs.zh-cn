---
title: <permission> - C# 编程指南
description: 了解 XML <permission> 标记。 此标记可用于记录成员访问权限，而 PermissionSet 类可用于指定对成员的访问权限。
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381718"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="57c31-105">\<permission>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="57c31-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="57c31-106">语法</span><span class="sxs-lookup"><span data-stu-id="57c31-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="57c31-107">参数</span><span class="sxs-lookup"><span data-stu-id="57c31-107">Parameters</span></span>

- <span data-ttu-id="57c31-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="57c31-108">cref = " `member`"</span></span>

  <span data-ttu-id="57c31-109">对可从当前编译环境调用的成员或字段的引用。</span><span class="sxs-lookup"><span data-stu-id="57c31-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="57c31-110">编译器检查是否存在给定的代码元素，并将 `member` 转换为输出 XML 中规范的元素名称。</span><span class="sxs-lookup"><span data-stu-id="57c31-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="57c31-111">成员必须出现在双引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="57c31-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="57c31-112">有关如何创建对泛型类型的 cref 引用的信息，请参阅 [cref 特性](./cref-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="57c31-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="57c31-113">对成员访问权限的说明。</span><span class="sxs-lookup"><span data-stu-id="57c31-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="57c31-114">备注</span><span class="sxs-lookup"><span data-stu-id="57c31-114">Remarks</span></span>

<span data-ttu-id="57c31-115">使用 `<permission>` 标记可以记录成员访问权限。</span><span class="sxs-lookup"><span data-stu-id="57c31-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="57c31-116"><xref:System.Security.PermissionSet> 类可指定对成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="57c31-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="57c31-117">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="57c31-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="57c31-118">示例</span><span class="sxs-lookup"><span data-stu-id="57c31-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="57c31-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="57c31-119">See also</span></span>

- [<span data-ttu-id="57c31-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="57c31-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="57c31-121">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="57c31-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
