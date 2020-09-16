---
title: 常见 XAML 语言基元的内置类型
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: ec0e2a29a191d5057ce66a5f3272d00e92b01bd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540024"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="3a382-102">常见 XAML 语言基元的内置类型</span><span class="sxs-lookup"><span data-stu-id="3a382-102">Built-in types for common XAML language primitives</span></span>

<span data-ttu-id="3a382-103">XAML 2009 引入了对多种数据类型的 XAML 语言级支持（这些数据类型是公共语言运行时 (CLR) 和其他编程语言中的常用基元）。</span><span class="sxs-lookup"><span data-stu-id="3a382-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="3a382-104">XAML 2009 增加了对以下基元的支持： `x:Object`、 `x:Boolean`、 `x:Char`、 `x:String`、 `x:Decimal`、 `x:Single`、 `x:Double`、 `x:Int16`、 `x:Int32`、 `x:Int64`、 `x:TimeSpan`、 `x:Uri`、 `x:Byte`和 `x:Array`</span><span class="sxs-lookup"><span data-stu-id="3a382-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="3a382-105">用于 XAML 标记中语言基元的早期方法</span><span class="sxs-lookup"><span data-stu-id="3a382-105">Previous Techniques for Language Primitives in XAML Markup</span></span>

 <span data-ttu-id="3a382-106">在早期 WPF 版本的 XAML 中，可以通过映射程序集以及包含 .NET Framework 的 CLR 基元定义类的命名空间来引用 CLR 语言基元。</span><span class="sxs-lookup"><span data-stu-id="3a382-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="3a382-107">它们中的大部分都位于 mscorlib 程序集和 <xref:System> 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="3a382-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="3a382-108">例如，要使用 <xref:System.Int32>，可以声明以下映射（用法示例如后面所示）：</span><span class="sxs-lookup"><span data-stu-id="3a382-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="3a382-109">XAML 2009 语言基元</span><span class="sxs-lookup"><span data-stu-id="3a382-109">XAML 2009 Language Primitives</span></span>

<span data-ttu-id="3a382-110">按照约定，将显示 XAML 的语言基元以及所有其他 XAML 语言元素，包括 `x:` 前缀。</span><span class="sxs-lookup"><span data-stu-id="3a382-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="3a382-111">这是 XAML 语言元素在实际标记中的典型用法。</span><span class="sxs-lookup"><span data-stu-id="3a382-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="3a382-112">WPF 中 XAML 的概念性文档以及 XAML 规范遵从此约定。</span><span class="sxs-lookup"><span data-stu-id="3a382-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>

### <a name="xobject"></a><span data-ttu-id="3a382-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="3a382-113">x:Object</span></span>

<span data-ttu-id="3a382-114">对于 CLR 支持， `x:Object` 基元对应于 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="3a382-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>

<span data-ttu-id="3a382-115">此基元通常不在应用程序标记中使用，但对于某些情况（如检查 XAML 类型系统中的可分配性）可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="3a382-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>

### <a name="xboolean"></a><span data-ttu-id="3a382-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="3a382-116">x:Boolean</span></span>

<span data-ttu-id="3a382-117">对于 CLR 支持， `x:Boolean` 基元对应于 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="3a382-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>

<span data-ttu-id="3a382-118">XAML 分析 `x:Boolean` 的值时不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3a382-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="3a382-119">请注意， `x:Bool` 不是可接受的备选基元。</span><span class="sxs-lookup"><span data-stu-id="3a382-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="3a382-120">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.17 和第5.4.11 节的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xchar"></a><span data-ttu-id="3a382-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="3a382-121">x:Char</span></span>

<span data-ttu-id="3a382-122">对于 CLR 支持， `x:Char` 基元对应于 <xref:System.Char>。</span><span class="sxs-lookup"><span data-stu-id="3a382-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>

<span data-ttu-id="3a382-123">String 和 char 类型在 XML 级别与文件的整个编码进行交互。</span><span class="sxs-lookup"><span data-stu-id="3a382-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="3a382-124">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.7 和5.4.1 的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xstring"></a><span data-ttu-id="3a382-125">x:String</span><span class="sxs-lookup"><span data-stu-id="3a382-125">x:String</span></span>

<span data-ttu-id="3a382-126">对于 CLR 支持， `x:String` 基元对应于 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="3a382-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>

<span data-ttu-id="3a382-127">String 和 char 类型在 XML 级别与文件的整个编码进行交互。</span><span class="sxs-lookup"><span data-stu-id="3a382-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="3a382-128">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.6 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdecimal"></a><span data-ttu-id="3a382-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="3a382-129">x:Decimal</span></span>

<span data-ttu-id="3a382-130">对于 CLR 支持， `x:Decimal` 基元对应于 <xref:System.Decimal>。</span><span class="sxs-lookup"><span data-stu-id="3a382-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>

<span data-ttu-id="3a382-131">XAML 分析本质上在区域性下完成 `en-US` 。</span><span class="sxs-lookup"><span data-stu-id="3a382-131">XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="3a382-132">在 `en-US` 区域性设置下，小数部分的正确分隔符始终为句点 (`.`)，而与开发环境的区域性设置或在运行时加载 XAML 的最终客户端目标的区域性设置无关。</span><span class="sxs-lookup"><span data-stu-id="3a382-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>

<span data-ttu-id="3a382-133">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.14 和第5.4.8 节的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xsingle"></a><span data-ttu-id="3a382-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="3a382-134">x:Single</span></span>

<span data-ttu-id="3a382-135">对于 CLR 支持， `x:Single` 基元对应于 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="3a382-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>

<span data-ttu-id="3a382-136">除了数值之外， `x:Single` 的文本语法还允许使用标记 `Infinity`、 `-Infinity`和 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="3a382-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="3a382-137">这些标记被视为区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3a382-137">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="3a382-138">`x:Single` 支持采用科学记数法格式的值，条件是文本语法中的第一个字符为 `e` 或 `E`。</span><span class="sxs-lookup"><span data-stu-id="3a382-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>

<span data-ttu-id="3a382-139">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.8 和5.4.2 的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdouble"></a><span data-ttu-id="3a382-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="3a382-140">x:Double</span></span>

<span data-ttu-id="3a382-141">对于 CLR 支持， `x:Double` 基元对应于 <xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="3a382-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>

<span data-ttu-id="3a382-142">除了数值之外， `x:Double` 的文本语法还允许使用标记 `Infinity`、 `-Infinity`和 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="3a382-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="3a382-143">这些标记被视为区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3a382-143">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="3a382-144">`x:Double` 支持采用科学记数法格式的值。</span><span class="sxs-lookup"><span data-stu-id="3a382-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="3a382-145">使用字符 `e` 或 `E` 可引入指数部分。</span><span class="sxs-lookup"><span data-stu-id="3a382-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>

<span data-ttu-id="3a382-146">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.9 和5.4.3 的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint16"></a><span data-ttu-id="3a382-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="3a382-147">x:Int16</span></span>

<span data-ttu-id="3a382-148">对于 CLR 支持， `x:Int16` 基元对应于 <xref:System.Int16> ，并且 `x:Int16` 被视为带符号。</span><span class="sxs-lookup"><span data-stu-id="3a382-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="3a382-149">在 XAML 中，文本语法中没有加号 (`+`) 表示是一个带符号的正值。</span><span class="sxs-lookup"><span data-stu-id="3a382-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="3a382-150">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.11 和第5.4.5 节的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint32"></a><span data-ttu-id="3a382-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="3a382-151">x:Int32</span></span>

<span data-ttu-id="3a382-152">对于 CLR 支持， `x:Int32` 基元对应于 <xref:System.Int32>。</span><span class="sxs-lookup"><span data-stu-id="3a382-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="3a382-153">`x:Int32` 被视为带符号。</span><span class="sxs-lookup"><span data-stu-id="3a382-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="3a382-154">在 XAML 中，文本语法中没有加号 (`+`) 表示是一个带符号的正值。</span><span class="sxs-lookup"><span data-stu-id="3a382-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="3a382-155">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.12 和第5.4.6 节的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint64"></a><span data-ttu-id="3a382-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="3a382-156">x:Int64</span></span>

<span data-ttu-id="3a382-157">对于 CLR 支持， `x:Int64` 基元对应于 <xref:System.Int64>。</span><span class="sxs-lookup"><span data-stu-id="3a382-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="3a382-158">`x:Int64` 被视为带符号。</span><span class="sxs-lookup"><span data-stu-id="3a382-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="3a382-159">在 XAML 中，文本语法中没有加号 (`+`) 表示是一个带符号的正值。</span><span class="sxs-lookup"><span data-stu-id="3a382-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="3a382-160">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.13 和第5.4.7 节的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xtimespan"></a><span data-ttu-id="3a382-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3a382-161">x:TimeSpan</span></span>

<span data-ttu-id="3a382-162">对于 CLR 支持， `x:TimeSpan` 基元对应于 <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="3a382-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>

<span data-ttu-id="3a382-163">时间日期格式的 XAML 分析本质上在区域性下完成 `en-US` 。</span><span class="sxs-lookup"><span data-stu-id="3a382-163">XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>

<span data-ttu-id="3a382-164">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.16 和第5.4.10 节的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xuri"></a><span data-ttu-id="3a382-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="3a382-165">x:Uri</span></span>

<span data-ttu-id="3a382-166">对于 CLR 支持， `x:Uri` 基元对应于 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="3a382-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>

<span data-ttu-id="3a382-167">检查协议不是 `x:Uri`的 XAML 定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="3a382-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>

<span data-ttu-id="3a382-168">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.15 和第5.4.9 节的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xbyte"></a><span data-ttu-id="3a382-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="3a382-169">x:Byte</span></span>

<span data-ttu-id="3a382-170">对于 CLR 支持， `x:Byte` 基元对应于 <xref:System.Byte>。</span><span class="sxs-lookup"><span data-stu-id="3a382-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="3a382-171"><xref:System.Byte>  /  `x:Byte` 被视为无符号。</span><span class="sxs-lookup"><span data-stu-id="3a382-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>

<span data-ttu-id="3a382-172">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.10 和5.4.4 的 MS xaml 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xarray"></a><span data-ttu-id="3a382-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="3a382-173">x:Array</span></span>

<span data-ttu-id="3a382-174">对于 CLR 支持， `x:Array` 基元对应于 <xref:System.Array>。</span><span class="sxs-lookup"><span data-stu-id="3a382-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>

<span data-ttu-id="3a382-175">可以在 XAML 2006 中使用标记扩展语法定义一个数组；而 XAML 2009 语法是语言定义的基元，不需要访问标记扩展。</span><span class="sxs-lookup"><span data-stu-id="3a382-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="3a382-176">有关 XAML 2006 支持的更多信息，请参阅 [x:Array Markup Extension](xarray-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="3a382-176">For more information about XAML 2006 support, see [x:Array Markup Extension](xarray-markup-extension.md).</span></span>

<span data-ttu-id="3a382-177">有关 XAML 语言规范的定义，请参阅[ \[ \] 5.2.18 部分](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="3a382-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="wpf-support"></a><span data-ttu-id="3a382-178">WPF 支持</span><span class="sxs-lookup"><span data-stu-id="3a382-178">WPF Support</span></span>

<span data-ttu-id="3a382-179">在 WPF 中，可以使用 XAML 2009 功能，但仅针对未进行标记编译的 XAML。</span><span class="sxs-lookup"><span data-stu-id="3a382-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="3a382-180">WPF 的已编译标记的 XAML 以及 XAML 的 BAML 形式当前不支持 XAML 2009 关键字和功能。</span><span class="sxs-lookup"><span data-stu-id="3a382-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="3a382-181">可使用 XAML 2009 功能以及 WPF 的一种情况是创作宽松 XAML，然后使用 <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>将该 XAML 加载到 WPF 运行时和对象图中。</span><span class="sxs-lookup"><span data-stu-id="3a382-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3a382-182">WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 及其 <xref:System.Windows.Markup.XamlReader.Load%2A> 可以将 XAML 2009 语言关键字和功能处理成一个有效的对象图表示形式。</span><span class="sxs-lookup"><span data-stu-id="3a382-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
