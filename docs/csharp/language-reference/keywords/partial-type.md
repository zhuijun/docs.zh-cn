---
description: 分部类型 - C# 参考
title: 分部类型 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 8ae98805eea7231e3a15cb74e636313e796796a2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117982"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="259c5-103">分部类型（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="259c5-103">partial type (C# Reference)</span></span>

<span data-ttu-id="259c5-104">通过分部类型可以定义要拆分到多个文件中的类、结构或接口。</span><span class="sxs-lookup"><span data-stu-id="259c5-104">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="259c5-105">在 File1.cs 中：</span><span class="sxs-lookup"><span data-stu-id="259c5-105">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="259c5-106">在 File2.cs 中，声明：</span><span class="sxs-lookup"><span data-stu-id="259c5-106">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="259c5-107">备注</span><span class="sxs-lookup"><span data-stu-id="259c5-107">Remarks</span></span>

<span data-ttu-id="259c5-108">在处理大型项目或自动生成的代码（如 [Windows 窗体设计器](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)提供的代码）时，在多个文件间拆分类、结构或接口类型可能会非常有用。</span><span class="sxs-lookup"><span data-stu-id="259c5-108">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="259c5-109">分部类型可以包含[分部方法](partial-method.md)。</span><span class="sxs-lookup"><span data-stu-id="259c5-109">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="259c5-110">有关详细信息，请参阅[分部类和方法](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="259c5-110">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="259c5-111">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="259c5-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="259c5-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="259c5-112">See also</span></span>

- [<span data-ttu-id="259c5-113">C# 参考</span><span class="sxs-lookup"><span data-stu-id="259c5-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="259c5-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="259c5-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="259c5-115">修饰符</span><span class="sxs-lookup"><span data-stu-id="259c5-115">Modifiers</span></span>](index.md)
- [<span data-ttu-id="259c5-116">泛型介绍</span><span class="sxs-lookup"><span data-stu-id="259c5-116">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
