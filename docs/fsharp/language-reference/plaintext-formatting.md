---
title: 纯文本格式
description: '了解如何在 F # 应用程序和脚本中使用 printf 和其他纯文本格式。'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063778"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="26abe-103">纯文本格式</span><span class="sxs-lookup"><span data-stu-id="26abe-103">Plain text formatting</span></span>

<span data-ttu-id="26abe-104">F # 支持使用 `printf` 、 `printfn` 、 `sprintf` 和相关函数的纯文本格式的类型检查格式。</span><span class="sxs-lookup"><span data-stu-id="26abe-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="26abe-105">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="26abe-106">提供输出</span><span class="sxs-lookup"><span data-stu-id="26abe-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="26abe-107">F # 还允许将结构化值设置为纯文本格式。</span><span class="sxs-lookup"><span data-stu-id="26abe-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="26abe-108">例如，请考虑以下示例，该示例将输出的格式设置为类似矩阵的元组显示形式。</span><span class="sxs-lookup"><span data-stu-id="26abe-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="26abe-109">在 `%A` 格式字符串中使用格式时，将激活结构化纯文本格式 `printf` 。</span><span class="sxs-lookup"><span data-stu-id="26abe-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="26abe-110">在 F # interactive 中格式化值的输出时，它也会被激活，其中的输出包含额外信息，还可自定义。</span><span class="sxs-lookup"><span data-stu-id="26abe-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="26abe-111">纯文本格式设置也可通过对 `x.ToString()` F # 联合和记录值（包括在调试、日志记录和其他工具中隐式执行的）的调用来观察。</span><span class="sxs-lookup"><span data-stu-id="26abe-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="26abe-112">检查 `printf` 格式字符串</span><span class="sxs-lookup"><span data-stu-id="26abe-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="26abe-113">如果将 `printf` 格式设置函数与格式字符串中的 printf 格式说明符不匹配的参数一起使用，则将报告编译时错误。</span><span class="sxs-lookup"><span data-stu-id="26abe-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="26abe-114">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="26abe-115">提供输出</span><span class="sxs-lookup"><span data-stu-id="26abe-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="26abe-116">从技术上讲，使用 `printf` 和其他相关函数时，F # 编译器中的特殊规则检查作为格式字符串传递的字符串文本，确保应用的后续参数是正确的类型，以匹配所使用的格式说明符。</span><span class="sxs-lookup"><span data-stu-id="26abe-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="26abe-117">的格式说明符`printf`</span><span class="sxs-lookup"><span data-stu-id="26abe-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="26abe-118">格式规范格式 `printf` 是带有 `%` 指示格式的标记的字符串。</span><span class="sxs-lookup"><span data-stu-id="26abe-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="26abe-119">格式占位符包含以下 `%[flags][width][.precision][type]` 内容：</span><span class="sxs-lookup"><span data-stu-id="26abe-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="26abe-120">格式说明符</span><span class="sxs-lookup"><span data-stu-id="26abe-120">Format specifier</span></span>   | <span data-ttu-id="26abe-121">键入 (s) </span><span class="sxs-lookup"><span data-stu-id="26abe-121">Type(s)</span></span>        | <span data-ttu-id="26abe-122">备注</span><span class="sxs-lookup"><span data-stu-id="26abe-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="26abe-123">bool</span><span class="sxs-lookup"><span data-stu-id="26abe-123">bool</span></span>      | <span data-ttu-id="26abe-124">格式为 `true` 或`false`</span><span class="sxs-lookup"><span data-stu-id="26abe-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="26abe-125">string</span><span class="sxs-lookup"><span data-stu-id="26abe-125">string</span></span>    | <span data-ttu-id="26abe-126">格式化为未转义的内容</span><span class="sxs-lookup"><span data-stu-id="26abe-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="26abe-127">char</span><span class="sxs-lookup"><span data-stu-id="26abe-127">char</span></span>      | <span data-ttu-id="26abe-128">格式化为字符文本</span><span class="sxs-lookup"><span data-stu-id="26abe-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="26abe-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="26abe-129">`%d`, `%i`</span></span>         | <span data-ttu-id="26abe-130">基本整数类型</span><span class="sxs-lookup"><span data-stu-id="26abe-130">a basic integer type</span></span> | <span data-ttu-id="26abe-131">格式化为十进制整数，如果基本整数类型已签名，则对其进行签名</span><span class="sxs-lookup"><span data-stu-id="26abe-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="26abe-132">基本整数类型</span><span class="sxs-lookup"><span data-stu-id="26abe-132">a basic integer type</span></span> | <span data-ttu-id="26abe-133">格式化为无符号的十进制整数</span><span class="sxs-lookup"><span data-stu-id="26abe-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="26abe-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="26abe-134">`%x`, `%X`</span></span>         | <span data-ttu-id="26abe-135">基本整数类型</span><span class="sxs-lookup"><span data-stu-id="26abe-135">a basic integer type</span></span> | <span data-ttu-id="26abe-136">格式化为一个无符号的十六进制数字，分别 (a-f 或 A-F) </span><span class="sxs-lookup"><span data-stu-id="26abe-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="26abe-137">基本整数类型</span><span class="sxs-lookup"><span data-stu-id="26abe-137">a basic integer type</span></span> | <span data-ttu-id="26abe-138">格式化为无符号的八进制数</span><span class="sxs-lookup"><span data-stu-id="26abe-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="26abe-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="26abe-139">`%e`, `%E`</span></span>         | <span data-ttu-id="26abe-140">基本浮点类型</span><span class="sxs-lookup"><span data-stu-id="26abe-140">a basic floating point type</span></span> | <span data-ttu-id="26abe-141">格式为有符号值 `[-]d.dddde[sign]ddd` ，其中 d 是单个十进制数字，dddd 是一个或多个十进制数字，ddd 只是三个十进制数字，而 sign 为 `+` 或`-`</span><span class="sxs-lookup"><span data-stu-id="26abe-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="26abe-142">基本浮点类型</span><span class="sxs-lookup"><span data-stu-id="26abe-142">a basic floating point type</span></span> | <span data-ttu-id="26abe-143">格式化为具有形式的带符号值 `[-]dddd.dddd` ，其中 `dddd` 是一个或多个十进制数字。</span><span class="sxs-lookup"><span data-stu-id="26abe-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="26abe-144">小数点前的数字位数取决于数字的度量值，小数点后的数字位数取决于所需精度。</span><span class="sxs-lookup"><span data-stu-id="26abe-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="26abe-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="26abe-145">`%g`, `%G`</span></span> | <span data-ttu-id="26abe-146">基本浮点类型</span><span class="sxs-lookup"><span data-stu-id="26abe-146">a basic floating point type</span></span> |  <span data-ttu-id="26abe-147">使用作为或格式打印的带符号值进行格式化 `%f` `%e` ，以更紧凑的给定值和精度为准。</span><span class="sxs-lookup"><span data-stu-id="26abe-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="26abe-148">一个 `System.Decimal` 值</span><span class="sxs-lookup"><span data-stu-id="26abe-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="26abe-149">使用 `"G"` 格式说明符的格式设置`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="26abe-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="26abe-150">任何值</span><span class="sxs-lookup"><span data-stu-id="26abe-150">any value</span></span>  |   <span data-ttu-id="26abe-151">通过装箱对象并调用其方法设置格式 `System.Object.ToString()`</span><span class="sxs-lookup"><span data-stu-id="26abe-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="26abe-152">任何值</span><span class="sxs-lookup"><span data-stu-id="26abe-152">any value</span></span>  |   <span data-ttu-id="26abe-153">使用默认布局设置以[结构化纯文本格式](plaintext-formatting.md)设置格式</span><span class="sxs-lookup"><span data-stu-id="26abe-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="26abe-154">任何值</span><span class="sxs-lookup"><span data-stu-id="26abe-154">any value</span></span>  |   <span data-ttu-id="26abe-155">需要两个参数：一个格式设置函数，接受上下文参数和值以及要打印的特定值</span><span class="sxs-lookup"><span data-stu-id="26abe-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="26abe-156">任何值</span><span class="sxs-lookup"><span data-stu-id="26abe-156">any value</span></span>  |   <span data-ttu-id="26abe-157">需要一个参数：一个格式设置函数，它接受输出或返回适当文本的上下文参数</span><span class="sxs-lookup"><span data-stu-id="26abe-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |
| `%%` | <span data-ttu-id="26abe-158">（无）</span><span class="sxs-lookup"><span data-stu-id="26abe-158">(none)</span></span>  |   <span data-ttu-id="26abe-159">不需要任何参数，也不需要打印普通百分号：`%`</span><span class="sxs-lookup"><span data-stu-id="26abe-159">Requires no arguments and prints a plain percent sign: `%`</span></span> |

<span data-ttu-id="26abe-160">基本整数类型 `byte` (`System.Byte`) ， `sbyte` (`System.SByte`)  () `int16` () `System.Int16` `uint16` `System.UInt16` () `int32` `System.Int32` `uint32` `System.UInt32` `int64` `System.Int64` `uint64` `System.UInt64` `nativeint` `System.IntPtr` `unativeint` `System.UIntPtr` ()  ()  ()  ()  () 。</span><span class="sxs-lookup"><span data-stu-id="26abe-160">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="26abe-161">基本浮点类型 `float` (`System.Double`) 并 `float32` (`System.Single`) 。</span><span class="sxs-lookup"><span data-stu-id="26abe-161">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="26abe-162">可选宽度是指示结果的最小宽度的整数。</span><span class="sxs-lookup"><span data-stu-id="26abe-162">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="26abe-163">例如， `%6d` 打印一个整数，用空格作为前缀，以至少填写六个字符。</span><span class="sxs-lookup"><span data-stu-id="26abe-163">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="26abe-164">如果 width 为 `*` ，则使用额外的整数参数来指定相应的宽度。</span><span class="sxs-lookup"><span data-stu-id="26abe-164">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="26abe-165">有效标志为：</span><span class="sxs-lookup"><span data-stu-id="26abe-165">Valid flags are:</span></span>

| <span data-ttu-id="26abe-166">Flag</span><span class="sxs-lookup"><span data-stu-id="26abe-166">Flag</span></span>   | <span data-ttu-id="26abe-167">效果</span><span class="sxs-lookup"><span data-stu-id="26abe-167">Effect</span></span>        | <span data-ttu-id="26abe-168">备注</span><span class="sxs-lookup"><span data-stu-id="26abe-168">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="26abe-169">添加零而不是空格以构成所需宽度</span><span class="sxs-lookup"><span data-stu-id="26abe-169">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="26abe-170">将结果左对齐指定的宽度</span><span class="sxs-lookup"><span data-stu-id="26abe-170">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="26abe-171">`+`如果数字为正，则添加一个字符， (以匹配 `-` 负号) </span><span class="sxs-lookup"><span data-stu-id="26abe-171">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="26abe-172">空格字符</span><span class="sxs-lookup"><span data-stu-id="26abe-172">space character</span></span> | <span data-ttu-id="26abe-173">如果数字为正，则添加一个额外的空格 (以匹配负的 "-" 符号) </span><span class="sxs-lookup"><span data-stu-id="26abe-173">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="26abe-174">Printf `#` 标志无效，如果使用，将报告编译时错误。</span><span class="sxs-lookup"><span data-stu-id="26abe-174">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="26abe-175">使用固定区域性设置值的格式。</span><span class="sxs-lookup"><span data-stu-id="26abe-175">Values are formatted using invariant culture.</span></span> <span data-ttu-id="26abe-176">区域性设置与格式无关， `printf` 除非它们影响和格式的结果 `%O` `%A` 。</span><span class="sxs-lookup"><span data-stu-id="26abe-176">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="26abe-177">有关详细信息，请参阅[结构化纯文本格式](plaintext-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="26abe-177">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="26abe-178">`%A`样式</span><span class="sxs-lookup"><span data-stu-id="26abe-178">`%A` formatting</span></span>

<span data-ttu-id="26abe-179">`%A`格式说明符用于以用户可读的方式设置值的格式，并且还可用于报告诊断信息。</span><span class="sxs-lookup"><span data-stu-id="26abe-179">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="26abe-180">基元值</span><span class="sxs-lookup"><span data-stu-id="26abe-180">Primitive values</span></span>

<span data-ttu-id="26abe-181">使用说明符设置纯文本格式时 `%A` ，F # 数值使用其后缀和固定区域性进行格式设置。</span><span class="sxs-lookup"><span data-stu-id="26abe-181">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="26abe-182">使用浮点精度的10个位置设置浮点值的格式。</span><span class="sxs-lookup"><span data-stu-id="26abe-182">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="26abe-183">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-183">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="26abe-184">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-184">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="26abe-185">使用此 `%A` 说明符时，使用引号设置字符串的格式。</span><span class="sxs-lookup"><span data-stu-id="26abe-185">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="26abe-186">不会添加转义码，而是输出原始字符。</span><span class="sxs-lookup"><span data-stu-id="26abe-186">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="26abe-187">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-187">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="26abe-188">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-188">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="26abe-189">.NET 值</span><span class="sxs-lookup"><span data-stu-id="26abe-189">.NET values</span></span>

<span data-ttu-id="26abe-190">使用说明符设置纯文本格式时 `%A` ，非 F # .net 对象将使用 `x.ToString()` 和提供的 .net 默认设置进行格式化 `System.Globalization.CultureInfo.CurrentCulture` `System.Globalization.CultureInfo.CurrentUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="26abe-190">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="26abe-191">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-191">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="26abe-192">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-192">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="26abe-193">结构化值</span><span class="sxs-lookup"><span data-stu-id="26abe-193">Structured values</span></span>

<span data-ttu-id="26abe-194">使用说明符设置纯文本格式时 `%A` ，块缩进用于 F # 列表和元组。</span><span class="sxs-lookup"><span data-stu-id="26abe-194">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="26abe-195">如上一示例中所示。</span><span class="sxs-lookup"><span data-stu-id="26abe-195">This shown in the previous example.</span></span>
<span data-ttu-id="26abe-196">还使用数组的结构，包括多维数组。</span><span class="sxs-lookup"><span data-stu-id="26abe-196">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="26abe-197">用语法显示一维数组 `[| ... |]` 。</span><span class="sxs-lookup"><span data-stu-id="26abe-197">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="26abe-198">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-198">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="26abe-199">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-199">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="26abe-200">默认打印宽度为80。</span><span class="sxs-lookup"><span data-stu-id="26abe-200">The default print width is 80.</span></span>  <span data-ttu-id="26abe-201">可以通过在格式说明符中使用打印宽度自定义此宽度。</span><span class="sxs-lookup"><span data-stu-id="26abe-201">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="26abe-202">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-202">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="26abe-203">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-203">produces</span></span>

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

<span data-ttu-id="26abe-204">如果将打印宽度指定为0，则不会使用打印宽度。</span><span class="sxs-lookup"><span data-stu-id="26abe-204">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="26abe-205">将产生单行文本，只不过输出中嵌入的字符串包含分行符。</span><span class="sxs-lookup"><span data-stu-id="26abe-205">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="26abe-206">例如</span><span class="sxs-lookup"><span data-stu-id="26abe-206">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="26abe-207">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-207">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="26abe-208">深度限制为4，用于序列 (`IEnumerable`) 值，这些值显示为 `seq { ...}` 。</span><span class="sxs-lookup"><span data-stu-id="26abe-208">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="26abe-209">对于列表和数组值，深度限制为100。</span><span class="sxs-lookup"><span data-stu-id="26abe-209">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="26abe-210">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-210">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="26abe-211">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-211">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="26abe-212">块缩进还用于公共记录和联合值的结构。</span><span class="sxs-lookup"><span data-stu-id="26abe-212">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="26abe-213">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-213">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="26abe-214">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-214">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="26abe-215">如果 `%+A` 使用了，则也可以使用反射来显示记录和联合的专用结构。</span><span class="sxs-lookup"><span data-stu-id="26abe-215">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="26abe-216">例如</span><span class="sxs-lookup"><span data-stu-id="26abe-216">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="26abe-217">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-217">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="26abe-218">大、循环或深度嵌套的值</span><span class="sxs-lookup"><span data-stu-id="26abe-218">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="26abe-219">大型结构化值的格式设置为最大总体对象节点计数10000。</span><span class="sxs-lookup"><span data-stu-id="26abe-219">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="26abe-220">深度嵌套的值的格式为100。</span><span class="sxs-lookup"><span data-stu-id="26abe-220">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="26abe-221">在这两种情况下，都 `...` 用于 elide 一些输出。</span><span class="sxs-lookup"><span data-stu-id="26abe-221">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="26abe-222">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-222">For example,</span></span>

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

<span data-ttu-id="26abe-223">生成包含部分省略的大型输出：</span><span class="sxs-lookup"><span data-stu-id="26abe-223">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="26abe-224">在对象图中检测到循环，并在 `...` 检测到循环的位置使用。</span><span class="sxs-lookup"><span data-stu-id="26abe-224">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="26abe-225">例如</span><span class="sxs-lookup"><span data-stu-id="26abe-225">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="26abe-226">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-226">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="26abe-227">迟缓、null 和函数值</span><span class="sxs-lookup"><span data-stu-id="26abe-227">Lazy, null, and function values</span></span>

<span data-ttu-id="26abe-228">如果尚未计算该值，则迟缓值将打印为 `Value is not created` 或等效文本。</span><span class="sxs-lookup"><span data-stu-id="26abe-228">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="26abe-229">空值将输出为， `null` 除非将值的静态类型确定为联合类型，其中 `null` 是允许的表示形式。</span><span class="sxs-lookup"><span data-stu-id="26abe-229">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="26abe-230">F # 函数值打印为其内部生成的结束名称，例如 `<fun:it@43-7>` 。</span><span class="sxs-lookup"><span data-stu-id="26abe-230">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="26abe-231">自定义纯文本格式`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="26abe-231">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="26abe-232">使用说明符时 `%A` ，将遵循 `StructuredFormatDisplay` 类型声明的属性。</span><span class="sxs-lookup"><span data-stu-id="26abe-232">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="26abe-233">这可用于指定代理项文本和属性以显示值。</span><span class="sxs-lookup"><span data-stu-id="26abe-233">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="26abe-234">例如：</span><span class="sxs-lookup"><span data-stu-id="26abe-234">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="26abe-235">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-235">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="26abe-236">通过重写自定义纯文本格式`ToString`</span><span class="sxs-lookup"><span data-stu-id="26abe-236">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="26abe-237">`ToString`在 F # 编程中可观察到的默认实现。</span><span class="sxs-lookup"><span data-stu-id="26abe-237">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="26abe-238">通常，默认结果不适合在面向程序员的信息显示或用户输出中使用，因此，通常会替代默认实现。</span><span class="sxs-lookup"><span data-stu-id="26abe-238">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="26abe-239">默认情况下，F # 记录和联合类型使用的实现重写的实现 `ToString` `sprintf "%+A"` 。</span><span class="sxs-lookup"><span data-stu-id="26abe-239">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="26abe-240">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-240">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="26abe-241">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-241">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="26abe-242">对于类类型，不提供的默认实现， `ToString` 并且使用 .net 默认值，该默认值报告类型的名称。</span><span class="sxs-lookup"><span data-stu-id="26abe-242">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="26abe-243">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="26abe-243">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="26abe-244">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-244">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="26abe-245">为添加替代 `ToString` 可以提供更好的格式设置。</span><span class="sxs-lookup"><span data-stu-id="26abe-245">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="26abe-246">得到</span><span class="sxs-lookup"><span data-stu-id="26abe-246">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="26abe-247">F# 交互窗口结构化打印</span><span class="sxs-lookup"><span data-stu-id="26abe-247">F# Interactive structured printing</span></span>

<span data-ttu-id="26abe-248">F# 交互窗口 (`dotnet fsi`) 使用结构化纯文本格式的扩展版本来报告值并允许附加可定制性。</span><span class="sxs-lookup"><span data-stu-id="26abe-248">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="26abe-249">有关详细信息，请参阅[F# 交互窗口](fsharp-interactive-options.md)。</span><span class="sxs-lookup"><span data-stu-id="26abe-249">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="26abe-250">自定义调试显示</span><span class="sxs-lookup"><span data-stu-id="26abe-250">Customize debug displays</span></span>

<span data-ttu-id="26abe-251">适用于 .NET 的调试器考虑使用和等属性 `DebuggerDisplay` `DebuggerTypeProxy` ，这些属性会影响调试器检查窗口中的对象的结构化显示。</span><span class="sxs-lookup"><span data-stu-id="26abe-251">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="26abe-252">F # 编译器自动为可区分的联合和记录类型生成这些属性，但不自动生成类、接口或结构类型。</span><span class="sxs-lookup"><span data-stu-id="26abe-252">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="26abe-253">F # 纯文本格式中会忽略这些属性，但在调试 F # 类型时，实现这些方法以改进显示会很有用。</span><span class="sxs-lookup"><span data-stu-id="26abe-253">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="26abe-254">请参阅</span><span class="sxs-lookup"><span data-stu-id="26abe-254">See also</span></span>

- [<span data-ttu-id="26abe-255">字符串</span><span class="sxs-lookup"><span data-stu-id="26abe-255">Strings</span></span>](strings.md)
- [<span data-ttu-id="26abe-256">记录</span><span class="sxs-lookup"><span data-stu-id="26abe-256">Records</span></span>](records.md)
- [<span data-ttu-id="26abe-257">可区分联合</span><span class="sxs-lookup"><span data-stu-id="26abe-257">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="26abe-258">F# Interactive</span><span class="sxs-lookup"><span data-stu-id="26abe-258">F# Interactive</span></span>](fsharp-interactive-options.md)
