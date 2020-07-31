---
title: <see> - C# 编程指南
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863781"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="a694f-102">\<see>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="a694f-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a694f-103">语法</span><span class="sxs-lookup"><span data-stu-id="a694f-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="a694f-104">参数</span><span class="sxs-lookup"><span data-stu-id="a694f-104">Parameters</span></span>

- <span data-ttu-id="a694f-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="a694f-105">cref = "`member`"</span></span>

  <span data-ttu-id="a694f-106">对可从当前编译环境调用的成员或字段的引用。</span><span class="sxs-lookup"><span data-stu-id="a694f-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a694f-107">编译器检查是否存在给定的码位元素，并将 `member` 传递到输出 XML 中的元素名称。</span><span class="sxs-lookup"><span data-stu-id="a694f-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="a694f-108">将成员置于双引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="a694f-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="a694f-109">备注</span><span class="sxs-lookup"><span data-stu-id="a694f-109">Remarks</span></span>

<span data-ttu-id="a694f-110">`<see>` 标记可用于从文本内指定链接。</span><span class="sxs-lookup"><span data-stu-id="a694f-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="a694f-111">使用 [\<seealso>](./seealso.md) 指示文本应该放在“另请参阅”部分中。</span><span class="sxs-lookup"><span data-stu-id="a694f-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="a694f-112">使用 [cref 属性](./cref-attribute.md)创建指向代码元素的文档页的内部超链接。</span><span class="sxs-lookup"><span data-stu-id="a694f-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="a694f-113">此外，``href`` 还是一个有效属性，将用作超链接。</span><span class="sxs-lookup"><span data-stu-id="a694f-113">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="a694f-114">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="a694f-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="a694f-115">下面的示例展示摘要部分中的 `<see>` 标记。</span><span class="sxs-lookup"><span data-stu-id="a694f-115">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="a694f-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="a694f-116">See also</span></span>

- [<span data-ttu-id="a694f-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="a694f-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a694f-118">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="a694f-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
