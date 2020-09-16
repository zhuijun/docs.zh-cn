---
title: XamlName 语法
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: ceb027938b6d4313babbe02949e0b6dd5ee85589
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556689"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="b1701-102">XamlName 语法</span><span class="sxs-lookup"><span data-stu-id="b1701-102">XamlName Grammar</span></span>

<span data-ttu-id="b1701-103">XamlName 语法是在 XAML 语言规范 [MS-CHAP] 中定义的一种特定语法，此处将在此处重现此语法。</span><span class="sxs-lookup"><span data-stu-id="b1701-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="b1701-104">从 XAML 规范</span><span class="sxs-lookup"><span data-stu-id="b1701-104">From the XAML Specification</span></span>

<span data-ttu-id="b1701-105">[MS-CHAP] 规范定义语法 XamlName，用于标识用于类型和属性的合法符号标识符集。</span><span class="sxs-lookup"><span data-stu-id="b1701-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="b1701-106">XamlName 类型的字符串值必须符合以下语法：</span><span class="sxs-lookup"><span data-stu-id="b1701-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="b1701-107">它假定 Unicode 字符数据库中定义的以下常规类别值</span><span class="sxs-lookup"><span data-stu-id="b1701-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="b1701-108">Unicode 类别</span><span class="sxs-lookup"><span data-stu-id="b1701-108">Unicode category</span></span>   | <span data-ttu-id="b1701-109">说明</span><span class="sxs-lookup"><span data-stu-id="b1701-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="b1701-110">Lu</span><span class="sxs-lookup"><span data-stu-id="b1701-110">Lu</span></span>                 | <span data-ttu-id="b1701-111">字母，大写</span><span class="sxs-lookup"><span data-stu-id="b1701-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="b1701-112">Ll</span><span class="sxs-lookup"><span data-stu-id="b1701-112">Ll</span></span>                 | <span data-ttu-id="b1701-113">字母，小写</span><span class="sxs-lookup"><span data-stu-id="b1701-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="b1701-114">Lt</span><span class="sxs-lookup"><span data-stu-id="b1701-114">Lt</span></span>                 | <span data-ttu-id="b1701-115">字母，首字母大写</span><span class="sxs-lookup"><span data-stu-id="b1701-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="b1701-116">Lm</span><span class="sxs-lookup"><span data-stu-id="b1701-116">Lm</span></span>                 | <span data-ttu-id="b1701-117">字母，修饰符</span><span class="sxs-lookup"><span data-stu-id="b1701-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="b1701-118">Lo</span><span class="sxs-lookup"><span data-stu-id="b1701-118">Lo</span></span>                 | <span data-ttu-id="b1701-119">字母，其他</span><span class="sxs-lookup"><span data-stu-id="b1701-119">Letter, Other</span></span>                 |
| <span data-ttu-id="b1701-120">Mn</span><span class="sxs-lookup"><span data-stu-id="b1701-120">Mn</span></span>                 | <span data-ttu-id="b1701-121">标记，非间距</span><span class="sxs-lookup"><span data-stu-id="b1701-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="b1701-122">Mc</span><span class="sxs-lookup"><span data-stu-id="b1701-122">Mc</span></span>                 | <span data-ttu-id="b1701-123">标记，间距组合</span><span class="sxs-lookup"><span data-stu-id="b1701-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="b1701-124">Nd</span><span class="sxs-lookup"><span data-stu-id="b1701-124">Nd</span></span>                 | <span data-ttu-id="b1701-125">Number、Decimal</span><span class="sxs-lookup"><span data-stu-id="b1701-125">Number, Decimal</span></span>               |
| <span data-ttu-id="b1701-126">Nl</span><span class="sxs-lookup"><span data-stu-id="b1701-126">Nl</span></span>                 | <span data-ttu-id="b1701-127">数字，字母</span><span class="sxs-lookup"><span data-stu-id="b1701-127">Number, Letter</span></span>                |

<span data-ttu-id="b1701-128">XAML 定义了第二个语法 DottedXamlName，用于属性和事件限定引用，还用于附加成员。</span><span class="sxs-lookup"><span data-stu-id="b1701-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="b1701-129">有关详细信息，请参阅 <xref:System.Windows.DependencyProperty> 和 [XAML 概述 (WPF) ](../fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="b1701-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="b1701-130">DottedXamlName 类型的字符串值必须符合以下语法：</span><span class="sxs-lookup"><span data-stu-id="b1701-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="b1701-131">备注</span><span class="sxs-lookup"><span data-stu-id="b1701-131">Remarks</span></span>

<span data-ttu-id="b1701-132">有关完整规范，请参阅 " [ \[ MS- \] XAML](/previous-versions/msp-n-p/ff650760(v=pandp.10))"。</span><span class="sxs-lookup"><span data-stu-id="b1701-132">For the complete specification, see [\[MS-XAML\]](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
