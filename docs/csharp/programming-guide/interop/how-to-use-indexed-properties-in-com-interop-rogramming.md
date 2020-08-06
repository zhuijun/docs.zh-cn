---
title: 如何在 COM 互操作编程中使用索引属性 - C# 编程指南
description: 了解索引属性改进了在此 C# 示例中使用具有参数的 COM 属性的方式。
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: abd785864bd79d455024cb4501c76a21b349aa91
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303005"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="d8d98-103">如何在 COM 互操作编程中使用索引属性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="d8d98-103">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="d8d98-104">索引属性改进了在 C# 编程中使用具有参数的 COM 属性的方式。</span><span class="sxs-lookup"><span data-stu-id="d8d98-104">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="d8d98-105">结合使用索引属性与 Visual C# 中的其他功能（如[命名实参和可选实参](../classes-and-structs/named-and-optional-arguments.md)、一种新类型（[动态](../../language-reference/builtin-types/reference-types.md)）以及[嵌入类型信息](../../../standard/assembly/embed-types-visual-studio.md)）可以增强 Microsoft Office 编程。</span><span class="sxs-lookup"><span data-stu-id="d8d98-105">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="d8d98-106">在早期版本的 C# 中，仅当 `get` 方法没有参数且 `set` 方法有且只有一个值参数时，方法才能作为属性访问。</span><span class="sxs-lookup"><span data-stu-id="d8d98-106">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="d8d98-107">但是，并非所有 COM 属性都符合上述限制。</span><span class="sxs-lookup"><span data-stu-id="d8d98-107">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="d8d98-108">例如，Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> 属性具有一个 `get` 访问器，它需要该范围名称的一个参数。</span><span class="sxs-lookup"><span data-stu-id="d8d98-108">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="d8d98-109">过去，由于无法直接访问 `Range` 属性，因此必须使用 `get_Range` 方法，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d8d98-109">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="d8d98-110">利用索引属性，你可以改为编写以下代码：</span><span class="sxs-lookup"><span data-stu-id="d8d98-110">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="d8d98-111">上一示例还使用了[可选实参](../classes-and-structs/named-and-optional-arguments.md)功能，以便忽略 `Type.Missing`。</span><span class="sxs-lookup"><span data-stu-id="d8d98-111">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="d8d98-112">与在 C# 3.0 及更早版本中设置 <xref:Microsoft.Office.Interop.Excel.Range> 对象的 `Value` 属性的值类似，需要两个参数。</span><span class="sxs-lookup"><span data-stu-id="d8d98-112">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="d8d98-113">一个为指定范围值类型的可选参数提供实参。</span><span class="sxs-lookup"><span data-stu-id="d8d98-113">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="d8d98-114">另一个提供 `Value` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d8d98-114">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="d8d98-115">下面的示例说明了这些方法。</span><span class="sxs-lookup"><span data-stu-id="d8d98-115">The following examples illustrate these techniques.</span></span> <span data-ttu-id="d8d98-116">两者都将 A1 单元格的值设置为 `Name`。</span><span class="sxs-lookup"><span data-stu-id="d8d98-116">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="d8d98-117">利用索引属性，你可以改为编写以下代码。</span><span class="sxs-lookup"><span data-stu-id="d8d98-117">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="d8d98-118">你不能创建自己的索引属性。</span><span class="sxs-lookup"><span data-stu-id="d8d98-118">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="d8d98-119">该功能仅支持使用现有索引属性。</span><span class="sxs-lookup"><span data-stu-id="d8d98-119">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8d98-120">示例</span><span class="sxs-lookup"><span data-stu-id="d8d98-120">Example</span></span>  
 <span data-ttu-id="d8d98-121">以下代码显示完整示例。</span><span class="sxs-lookup"><span data-stu-id="d8d98-121">The following code shows a complete example.</span></span> <span data-ttu-id="d8d98-122">有关如何设置访问 Office API 的项目的详细信息，请参阅[如何使用 C# 功能访问 Office 互操作对象](./how-to-access-office-onterop-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="d8d98-122">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d8d98-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="d8d98-123">See also</span></span>

- [<span data-ttu-id="d8d98-124">命名参数和可选参数</span><span class="sxs-lookup"><span data-stu-id="d8d98-124">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="d8d98-125">dynamic</span><span class="sxs-lookup"><span data-stu-id="d8d98-125">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="d8d98-126">使用类型 dynamic</span><span class="sxs-lookup"><span data-stu-id="d8d98-126">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="d8d98-127">如何在 Office 编程中使用命名参数和可选参数</span><span class="sxs-lookup"><span data-stu-id="d8d98-127">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="d8d98-128">如何使用 C# 功能访问 Office 互操作对象</span><span class="sxs-lookup"><span data-stu-id="d8d98-128">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="d8d98-129">演练：Office 编程</span><span class="sxs-lookup"><span data-stu-id="d8d98-129">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
