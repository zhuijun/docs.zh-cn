---
title: Date 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 46c25e14db56d4cc3c6d59ec7649b37c35676e2e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387421"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="8c597-102">Date 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c597-102">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="8c597-103">保存 IEEE 64 位（8 字节）值，它代表从 0001 年 1 月 1 日到 9999 年 12 月 31 日的日期，12:00:00 AM（午夜）到 11:59:59.9999999 PM 的时间。</span><span class="sxs-lookup"><span data-stu-id="8c597-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="8c597-104">每个增量表示自公历 1 年 1 月 1 日开始后经过的 100 纳秒的时间。</span><span class="sxs-lookup"><span data-stu-id="8c597-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="8c597-105">最大值表示 10000 年 1 月 1 日开始之前的 100 纳秒。</span><span class="sxs-lookup"><span data-stu-id="8c597-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c597-106">备注</span><span class="sxs-lookup"><span data-stu-id="8c597-106">Remarks</span></span>

<span data-ttu-id="8c597-107">使用 `Date` 数据类型包含日期值、时间值或日期和时间值。</span><span class="sxs-lookup"><span data-stu-id="8c597-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="8c597-108">`Date` 的默认值为 0001 年 1 月 1 日 0:00:00（午夜）。</span><span class="sxs-lookup"><span data-stu-id="8c597-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="8c597-109">可以从 <xref:Microsoft.VisualBasic.DateAndTime> 类获取当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="8c597-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="8c597-110">格式要求</span><span class="sxs-lookup"><span data-stu-id="8c597-110">Format Requirements</span></span>

<span data-ttu-id="8c597-111">必须将 `Date` 文字括在数字符号 (`# #`) 内。</span><span class="sxs-lookup"><span data-stu-id="8c597-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="8c597-112">必须以 M/d/yyyy 格式（例如 `#5/31/1993#`）或 yyyy-MM-dd 格式（例如 `#1993-5-31#`）指定日期值。</span><span class="sxs-lookup"><span data-stu-id="8c597-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="8c597-113">首先指定年份时，可以使用斜杠。</span><span class="sxs-lookup"><span data-stu-id="8c597-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="8c597-114">此需求与你所在的区域设置以及计算机的日期和时间格式设置相互独立。</span><span class="sxs-lookup"><span data-stu-id="8c597-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="8c597-115">此限制的原因是，代码的含义永远不会依据应用程序在其中运行的区域设置而改变。</span><span class="sxs-lookup"><span data-stu-id="8c597-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="8c597-116">假设硬编码 `Date` 文字 `#3/4/1998#` 意图使其表示 1998 年 3 月 4 日。</span><span class="sxs-lookup"><span data-stu-id="8c597-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="8c597-117">在使用 mm/dd/yyyy 的区域，3/4/1998 将按照你的意图进行编译。</span><span class="sxs-lookup"><span data-stu-id="8c597-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="8c597-118">但假设你将应用程序部署在多个国家/地区。</span><span class="sxs-lookup"><span data-stu-id="8c597-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="8c597-119">在使用 dd/mm/yyyy 的区域，硬编码的文本将编译为 1998 年 4 月 3 日。</span><span class="sxs-lookup"><span data-stu-id="8c597-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="8c597-120">在使用 yyyy/mm/dd 的区域，该文字将会无效（0003 年 4 月 1998 日）并导致编译器错误。</span><span class="sxs-lookup"><span data-stu-id="8c597-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="8c597-121">问题解决</span><span class="sxs-lookup"><span data-stu-id="8c597-121">Workarounds</span></span>

<span data-ttu-id="8c597-122">若要将 `Date` 文字转换为你所在区域的格式或自定义格式，请将该文字提供给 <xref:Microsoft.VisualBasic.Strings.Format%2A> 函数，并指定预定义的或用户定义的日期格式。</span><span class="sxs-lookup"><span data-stu-id="8c597-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="8c597-123">下面的示例对这种情况进行了演示。</span><span class="sxs-lookup"><span data-stu-id="8c597-123">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="8c597-124">或者，可以使用 <xref:System.DateTime> 结构的重载构造函数之一来组合日期和时间值。</span><span class="sxs-lookup"><span data-stu-id="8c597-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="8c597-125">以下示例创建一个表示 1993 年 3 月 31 日下午 12:14 的值。</span><span class="sxs-lookup"><span data-stu-id="8c597-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="8c597-126">小时格式</span><span class="sxs-lookup"><span data-stu-id="8c597-126">Hour Format</span></span>

<span data-ttu-id="8c597-127">可以 12 小时制或 24 小时制格式指定时间值，例如 `#1:15:30 PM#` 或 `#13:15:30#`。</span><span class="sxs-lookup"><span data-stu-id="8c597-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="8c597-128">但是，如果未指定分钟或秒，则必须指定 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="8c597-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="8c597-129">日期和时间默认值</span><span class="sxs-lookup"><span data-stu-id="8c597-129">Date and Time Defaults</span></span>

<span data-ttu-id="8c597-130">如果不在日期/时间文字中包括日期，则 Visual Basic 会将值的日期部分设置为 0001 年 1 月 1 日。</span><span class="sxs-lookup"><span data-stu-id="8c597-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="8c597-131">如果不在日期/时间文字中包括时间，则 Visual Basic 会将值的时间部分设置为一天的开始，即午夜 (0:00:00)。</span><span class="sxs-lookup"><span data-stu-id="8c597-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="8c597-132">类型转换</span><span class="sxs-lookup"><span data-stu-id="8c597-132">Type Conversions</span></span>

<span data-ttu-id="8c597-133">如果将 `Date` 值转换为 `String` 类型，则 Visual Basic 根据由运行时区域设置指定的短日期格式呈现日期，根据运行时区域设置指定的时间格式（12 小时制或 24 小时制）呈现时间。</span><span class="sxs-lookup"><span data-stu-id="8c597-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="8c597-134">编程提示</span><span class="sxs-lookup"><span data-stu-id="8c597-134">Programming Tips</span></span>

- <span data-ttu-id="8c597-135">**互操作注意事项。**</span><span class="sxs-lookup"><span data-stu-id="8c597-135">**Interop Considerations.**</span></span> <span data-ttu-id="8c597-136">如果你与不是为 .NET Framework 编写的组件（如自动化或 COM 对象）交互，请记住，其他环境中的日期/时间类型与 Visual Basic `Date` 类型不兼容。</span><span class="sxs-lookup"><span data-stu-id="8c597-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="8c597-137">如果将日期/时间自变量传递给此类组件，请在新的 Visual Basic 代码中将其声明为 `Double` 而不是 `Date`，并使用转换方法 <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> 和 <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8c597-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8c597-138">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="8c597-138">**Type Characters.**</span></span> <span data-ttu-id="8c597-139">`Date`没有文本类型字符或标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="8c597-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="8c597-140">但是，编译器会将括在数字符号 (`# #`) 内的文本作为 `Date`。</span><span class="sxs-lookup"><span data-stu-id="8c597-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="8c597-141">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="8c597-141">**Framework Type.**</span></span> <span data-ttu-id="8c597-142">.NET Framework 中的对应类型是 <xref:System.DateTime?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="8c597-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="8c597-143">示例</span><span class="sxs-lookup"><span data-stu-id="8c597-143">Example</span></span>

<span data-ttu-id="8c597-144">`Date` 数据类型的变量或常数都包含日期和时间。</span><span class="sxs-lookup"><span data-stu-id="8c597-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="8c597-145">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="8c597-145">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="8c597-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c597-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="8c597-147">数据类型</span><span class="sxs-lookup"><span data-stu-id="8c597-147">Data Types</span></span>](index.md)
- [<span data-ttu-id="8c597-148">标准日期和时间格式字符串</span><span class="sxs-lookup"><span data-stu-id="8c597-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="8c597-149">自定义日期和时间格式字符串</span><span class="sxs-lookup"><span data-stu-id="8c597-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="8c597-150">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="8c597-150">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="8c597-151">转换摘要</span><span class="sxs-lookup"><span data-stu-id="8c597-151">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="8c597-152">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="8c597-152">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
