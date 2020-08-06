---
title: <value> - C# 编程指南
description: 了解 XML <value> 标记。 此标记可用于描述属性表示的值。
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380769"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="a55e9-105">\<value>（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="a55e9-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a55e9-106">语法</span><span class="sxs-lookup"><span data-stu-id="a55e9-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="a55e9-107">参数</span><span class="sxs-lookup"><span data-stu-id="a55e9-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="a55e9-108">属性的说明。</span><span class="sxs-lookup"><span data-stu-id="a55e9-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="a55e9-109">备注</span><span class="sxs-lookup"><span data-stu-id="a55e9-109">Remarks</span></span>

<span data-ttu-id="a55e9-110">`<value>` 标记可用于描述属性表示的值。</span><span class="sxs-lookup"><span data-stu-id="a55e9-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="a55e9-111">在 Visual Studio .NET 开发环境中通过代码向导添加属性时，将添加新属性的 [\<summary>](./summary.md) 标记。</span><span class="sxs-lookup"><span data-stu-id="a55e9-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="a55e9-112">然后，应手动添加 `<value>` 标记，以描述属性表示的值。</span><span class="sxs-lookup"><span data-stu-id="a55e9-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="a55e9-113">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="a55e9-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a55e9-114">示例</span><span class="sxs-lookup"><span data-stu-id="a55e9-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="a55e9-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="a55e9-115">See also</span></span>

- [<span data-ttu-id="a55e9-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="a55e9-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a55e9-117">建议的文档注释标记</span><span class="sxs-lookup"><span data-stu-id="a55e9-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
