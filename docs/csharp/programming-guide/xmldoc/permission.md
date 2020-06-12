---
title: <permission> - C# 编程指南
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bb7172042f0b472d03c3fa2d9dbd0d4d4265076b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287267"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="24808-102">\<permission>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="24808-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="24808-103">语法</span><span class="sxs-lookup"><span data-stu-id="24808-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="24808-104">参数</span><span class="sxs-lookup"><span data-stu-id="24808-104">Parameters</span></span>

- <span data-ttu-id="24808-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="24808-105">cref = " `member`"</span></span>

  <span data-ttu-id="24808-106">对可从当前编译环境调用的成员或字段的引用。</span><span class="sxs-lookup"><span data-stu-id="24808-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="24808-107">编译器检查是否存在给定的代码元素，并将 `member` 转换为输出 XML 中规范的元素名称。</span><span class="sxs-lookup"><span data-stu-id="24808-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="24808-108">成员必须出现在双引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="24808-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="24808-109">有关如何创建对泛型类型的 cref 引用的信息，请参阅 [cref 特性](./cref-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="24808-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="24808-110">对成员访问权限的说明。</span><span class="sxs-lookup"><span data-stu-id="24808-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="24808-111">备注</span><span class="sxs-lookup"><span data-stu-id="24808-111">Remarks</span></span>

<span data-ttu-id="24808-112">使用 `<permission>` 标记可以记录成员访问权限。</span><span class="sxs-lookup"><span data-stu-id="24808-112">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="24808-113"><xref:System.Security.PermissionSet> 类可指定对成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="24808-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="24808-114">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="24808-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="24808-115">示例</span><span class="sxs-lookup"><span data-stu-id="24808-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="24808-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="24808-116">See also</span></span>

- [<span data-ttu-id="24808-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="24808-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="24808-118">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="24808-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
