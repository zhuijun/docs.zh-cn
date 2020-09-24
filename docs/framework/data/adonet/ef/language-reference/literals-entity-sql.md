---
title: 文本 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 4402f4c6ee38432a0f606e39dd4a18639076ce04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161771"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="34380-102">文本 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="34380-102">Literals (Entity SQL)</span></span>

<span data-ttu-id="34380-103">本主题介绍 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 对于文字的支持。</span><span class="sxs-lookup"><span data-stu-id="34380-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="34380-104">Null</span><span class="sxs-lookup"><span data-stu-id="34380-104">Null</span></span>  

 <span data-ttu-id="34380-105">空文字用于表示对任何类型均为空的值。</span><span class="sxs-lookup"><span data-stu-id="34380-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="34380-106">空文字与任何类型兼容。</span><span class="sxs-lookup"><span data-stu-id="34380-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="34380-107">强制转换可以在空文字之上创建类型空值。</span><span class="sxs-lookup"><span data-stu-id="34380-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="34380-108">有关详细信息，请参阅 [CAST](cast-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="34380-108">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="34380-109">有关可以使用自由浮动 null 文本的规则，请参阅 [Null 文本和类型推理](null-literals-and-type-inference-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="34380-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="34380-110">Boolean</span><span class="sxs-lookup"><span data-stu-id="34380-110">Boolean</span></span>  

 <span data-ttu-id="34380-111">布尔值文字由关键字 `true` 和 `false` 表示。</span><span class="sxs-lookup"><span data-stu-id="34380-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="34380-112">Integer</span><span class="sxs-lookup"><span data-stu-id="34380-112">Integer</span></span>  

 <span data-ttu-id="34380-113">整型文字可以为类型 <xref:System.Int32> 或 <xref:System.Int64>。</span><span class="sxs-lookup"><span data-stu-id="34380-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="34380-114"><xref:System.Int32> 文字是一系列数字字符。</span><span class="sxs-lookup"><span data-stu-id="34380-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="34380-115"><xref:System.Int64> 文字是一系列数字字符，后跟一个大写 L。</span><span class="sxs-lookup"><span data-stu-id="34380-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="34380-116">小数</span><span class="sxs-lookup"><span data-stu-id="34380-116">Decimal</span></span>  

 <span data-ttu-id="34380-117">固定点数字（小数）是一系列数字字符、一个圆点 (.) 和另一系列数字字符，后跟一个大写“M”。</span><span class="sxs-lookup"><span data-stu-id="34380-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="34380-118">浮点，双精度</span><span class="sxs-lookup"><span data-stu-id="34380-118">Float, Double</span></span>  

 <span data-ttu-id="34380-119">双精度浮点数字是一系列数字字符、一个圆点 (.) 和另一系列数字字符，后面可能跟一个指数。</span><span class="sxs-lookup"><span data-stu-id="34380-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="34380-120">单精度浮点数字（或浮点数）是双精度浮点数字语法后跟小写 f。</span><span class="sxs-lookup"><span data-stu-id="34380-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="34380-121">字符串</span><span class="sxs-lookup"><span data-stu-id="34380-121">String</span></span>  

 <span data-ttu-id="34380-122">字符串是包含在引号内的一系列字符。</span><span class="sxs-lookup"><span data-stu-id="34380-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="34380-123">引号可以同时为单引号 (`'`) 或同时为双引号 (")。</span><span class="sxs-lookup"><span data-stu-id="34380-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="34380-124">字符串文字可以是 Unicode 或非 Unicode。</span><span class="sxs-lookup"><span data-stu-id="34380-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="34380-125">若要将字符串文字声明为 Unicode，请在文字之前加上大写“N”作为前缀。</span><span class="sxs-lookup"><span data-stu-id="34380-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="34380-126">默认值为非 Unicode 字符串文字。</span><span class="sxs-lookup"><span data-stu-id="34380-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="34380-127">在 N 与字符串文字负载之间不能存在空格，并且 N 必须为大写。</span><span class="sxs-lookup"><span data-stu-id="34380-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="34380-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="34380-128">DateTime</span></span>  

 <span data-ttu-id="34380-129">日期时间文字独立于区域设置并由日期部分和时间部分组成。</span><span class="sxs-lookup"><span data-stu-id="34380-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="34380-130">日期部分和时间部分都是必需的，并且没有默认值。</span><span class="sxs-lookup"><span data-stu-id="34380-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="34380-131">日期部分的格式必须为： `YYYY` - `MM` - `DD` ，其中 `YYYY` 是介于0001和9999之间的四位数年份值， `MM` 是介于1和12之间的月份， `DD` 是对给定月份有效的日期值 `MM` 。</span><span class="sxs-lookup"><span data-stu-id="34380-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="34380-132">时间部分的格式必须为：`HH`:`MM`[:`SS`[.fffffff]]，其中 `HH` 为介于 0 至 23 之间的小时值，`MM` 为介于 0 至 59 之间的分钟值，`SS` 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。</span><span class="sxs-lookup"><span data-stu-id="34380-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="34380-133">所有值范围都包含两端。</span><span class="sxs-lookup"><span data-stu-id="34380-133">All value ranges are inclusive.</span></span> <span data-ttu-id="34380-134">秒的小数部分是可选的。</span><span class="sxs-lookup"><span data-stu-id="34380-134">Fractional seconds are optional.</span></span> <span data-ttu-id="34380-135">除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。</span><span class="sxs-lookup"><span data-stu-id="34380-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="34380-136">在未指定秒或秒的小数部分时，将使用默认值零。</span><span class="sxs-lookup"><span data-stu-id="34380-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="34380-137">在 DATETIME 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="34380-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="34380-138">时间</span><span class="sxs-lookup"><span data-stu-id="34380-138">Time</span></span>  

 <span data-ttu-id="34380-139">时间文字独立于区域设置并仅由时间部分组成。</span><span class="sxs-lookup"><span data-stu-id="34380-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="34380-140">时间部分为必选项，且没有默认值。</span><span class="sxs-lookup"><span data-stu-id="34380-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="34380-141">其格式必须为 HH:MM[:SS[.fffffff]]，其中 HH 为介于 0 至 23 之间的小时值，MM 为介于 0 至 59 之间的分钟值，SS 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。</span><span class="sxs-lookup"><span data-stu-id="34380-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="34380-142">所有值范围都包含两端。</span><span class="sxs-lookup"><span data-stu-id="34380-142">All value ranges are inclusive.</span></span> <span data-ttu-id="34380-143">秒的小数部分是可选的。</span><span class="sxs-lookup"><span data-stu-id="34380-143">Fractional seconds are optional.</span></span> <span data-ttu-id="34380-144">除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。</span><span class="sxs-lookup"><span data-stu-id="34380-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="34380-145">在未指定秒或秒的小数部分时，将使用默认值零。</span><span class="sxs-lookup"><span data-stu-id="34380-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="34380-146">在 TIME 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="34380-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="34380-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="34380-147">DateTimeOffset</span></span>  

 <span data-ttu-id="34380-148">datetimeoffset 文字独立于区域设置并由日期部分、时间部分和偏移量部分组成。</span><span class="sxs-lookup"><span data-stu-id="34380-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="34380-149">所有日期、时间和偏移量部分都是必选项，并且没有默认值。</span><span class="sxs-lookup"><span data-stu-id="34380-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="34380-150">日期部分的格式必须为 YYYY-MM-DD，其中 YYYY 是介于 0001 与 9999 之间的四位年度值，MM 是介于 1 与 12 之间的月份，而 DD 是对给定月份有效的日期值。</span><span class="sxs-lookup"><span data-stu-id="34380-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="34380-151">时间部分的格式必须为 HH:MM[:SS[.fffffff]]，其中 HH 为介于 0 至 23 之间的小时值，MM 为介于 0 至 59 之间的分钟值，SS 为介于 0 至 59 之间的秒值，而 fffffff 为介于 0 至 9999999 之间的秒的小数部分值。</span><span class="sxs-lookup"><span data-stu-id="34380-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="34380-152">所有值范围都包含两端。</span><span class="sxs-lookup"><span data-stu-id="34380-152">All value ranges are inclusive.</span></span> <span data-ttu-id="34380-153">秒的小数部分是可选的。</span><span class="sxs-lookup"><span data-stu-id="34380-153">Fractional seconds are optional.</span></span> <span data-ttu-id="34380-154">除非指定了秒的小数部分，否则秒是可选的；在指定了秒的小数部分时秒是必需的。</span><span class="sxs-lookup"><span data-stu-id="34380-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="34380-155">在未指定秒或秒的小数部分时，将使用默认值零。</span><span class="sxs-lookup"><span data-stu-id="34380-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="34380-156">偏移量部分的格式必须为 {+&#124;-} HH： MM，其中 HH 和 MM 与时间部分具有相同的含义。</span><span class="sxs-lookup"><span data-stu-id="34380-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="34380-157">但是，偏移量的范围必须介于 -14:00 至 + 14:00 之间。</span><span class="sxs-lookup"><span data-stu-id="34380-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="34380-158">在 DATETIMEOFFSET 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="34380-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="34380-159">有效的 Entity SQL 文字值可能处于 CLR 或数据源所支持的范围之外。</span><span class="sxs-lookup"><span data-stu-id="34380-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="34380-160">这可能会导致异常。</span><span class="sxs-lookup"><span data-stu-id="34380-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="34380-161">二进制</span><span class="sxs-lookup"><span data-stu-id="34380-161">Binary</span></span>  

 <span data-ttu-id="34380-162">二进制字符串文字是由单引号分隔的一系列十六进制数字，后跟关键字“binary”或快捷方式符号 `X`/`x`。</span><span class="sxs-lookup"><span data-stu-id="34380-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="34380-163">快捷方式符号 `X` 是不区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="34380-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="34380-164">在关键字 `binary` 与二进制字符串值之间可以有零个或零个以上空格。</span><span class="sxs-lookup"><span data-stu-id="34380-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="34380-165">十六进制字符也不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="34380-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="34380-166">如果文字由奇数个十六进制数字组成，则将通过在文字之前附加十六进制数字零作为前缀，使文字与下一个偶数十六进制数字对齐。</span><span class="sxs-lookup"><span data-stu-id="34380-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="34380-167">对于二进制字符串的大小，不存在正式的限制。</span><span class="sxs-lookup"><span data-stu-id="34380-167">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="34380-168">Guid</span><span class="sxs-lookup"><span data-stu-id="34380-168">Guid</span></span>  

 <span data-ttu-id="34380-169">`GUID` 文本表示全局唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="34380-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="34380-170">它是由关键字构成的序列， `GUID` 后跟十六进制数字，格式为： 8-4-4-4-12 *registry*并用单引号括起来。</span><span class="sxs-lookup"><span data-stu-id="34380-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="34380-171">十六进制数字区分大小写。</span><span class="sxs-lookup"><span data-stu-id="34380-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="34380-172">在 GUID 符号与文字负载之间可以存在任意数目的空格，但是不能存在新行。</span><span class="sxs-lookup"><span data-stu-id="34380-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="34380-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="34380-173">See also</span></span>

- [<span data-ttu-id="34380-174">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="34380-174">Entity SQL Overview</span></span>](entity-sql-overview.md)
