---
title: 文本
description: '了解 F # 编程语言中的文本类型。'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559149"
---
# <a name="literals"></a><span data-ttu-id="71311-103">文本</span><span class="sxs-lookup"><span data-stu-id="71311-103">Literals</span></span>

<span data-ttu-id="71311-104">本文提供了一个表，其中显示了如何指定 F # 中的文本类型。</span><span class="sxs-lookup"><span data-stu-id="71311-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="71311-105">文本类型</span><span class="sxs-lookup"><span data-stu-id="71311-105">Literal types</span></span>

<span data-ttu-id="71311-106">下表显示 F # 中的文本类型。</span><span class="sxs-lookup"><span data-stu-id="71311-106">The following table shows the literal types in F#.</span></span> <span data-ttu-id="71311-107">用十六进制表示法表示数字的字符不区分大小写;标识该类型的字符区分大小写。</span><span class="sxs-lookup"><span data-stu-id="71311-107">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="71311-108">类型</span><span class="sxs-lookup"><span data-stu-id="71311-108">Type</span></span>|<span data-ttu-id="71311-109">说明</span><span class="sxs-lookup"><span data-stu-id="71311-109">Description</span></span>|<span data-ttu-id="71311-110">后缀或前缀</span><span class="sxs-lookup"><span data-stu-id="71311-110">Suffix or prefix</span></span>|<span data-ttu-id="71311-111">示例</span><span class="sxs-lookup"><span data-stu-id="71311-111">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="71311-112">sbyte</span><span class="sxs-lookup"><span data-stu-id="71311-112">sbyte</span></span>|<span data-ttu-id="71311-113">8位有符号整数</span><span class="sxs-lookup"><span data-stu-id="71311-113">signed 8-bit integer</span></span>|<span data-ttu-id="71311-114">y</span><span class="sxs-lookup"><span data-stu-id="71311-114">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="71311-115">字节</span><span class="sxs-lookup"><span data-stu-id="71311-115">byte</span></span>|<span data-ttu-id="71311-116">无符号8位自然数</span><span class="sxs-lookup"><span data-stu-id="71311-116">unsigned 8-bit natural number</span></span>|<span data-ttu-id="71311-117">uy</span><span class="sxs-lookup"><span data-stu-id="71311-117">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="71311-118">int16</span><span class="sxs-lookup"><span data-stu-id="71311-118">int16</span></span>|<span data-ttu-id="71311-119">16位带符号整数</span><span class="sxs-lookup"><span data-stu-id="71311-119">signed 16-bit integer</span></span>|<span data-ttu-id="71311-120">s</span><span class="sxs-lookup"><span data-stu-id="71311-120">s</span></span>|`86s`|
|<span data-ttu-id="71311-121">uint16</span><span class="sxs-lookup"><span data-stu-id="71311-121">uint16</span></span>|<span data-ttu-id="71311-122">无符号16位自然数</span><span class="sxs-lookup"><span data-stu-id="71311-122">unsigned 16-bit natural number</span></span>|<span data-ttu-id="71311-123">us</span><span class="sxs-lookup"><span data-stu-id="71311-123">us</span></span>|`86us`|
|<span data-ttu-id="71311-124">int</span><span class="sxs-lookup"><span data-stu-id="71311-124">int</span></span><br /><br /><span data-ttu-id="71311-125">int32</span><span class="sxs-lookup"><span data-stu-id="71311-125">int32</span></span>|<span data-ttu-id="71311-126">已签名32位整数</span><span class="sxs-lookup"><span data-stu-id="71311-126">signed 32-bit integer</span></span>|<span data-ttu-id="71311-127">l 或无</span><span class="sxs-lookup"><span data-stu-id="71311-127">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="71311-128">uint</span><span class="sxs-lookup"><span data-stu-id="71311-128">uint</span></span><br /><br /><span data-ttu-id="71311-129">uint32</span><span class="sxs-lookup"><span data-stu-id="71311-129">uint32</span></span>|<span data-ttu-id="71311-130">无符号32位自然数</span><span class="sxs-lookup"><span data-stu-id="71311-130">unsigned 32-bit natural number</span></span>|<span data-ttu-id="71311-131">u 或 ul</span><span class="sxs-lookup"><span data-stu-id="71311-131">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="71311-132">nativeint</span><span class="sxs-lookup"><span data-stu-id="71311-132">nativeint</span></span>|<span data-ttu-id="71311-133">指向有符号自然数的本机指针</span><span class="sxs-lookup"><span data-stu-id="71311-133">native pointer to a signed natural number</span></span>|<span data-ttu-id="71311-134">n</span><span class="sxs-lookup"><span data-stu-id="71311-134">n</span></span>|`123n`|
|<span data-ttu-id="71311-135">unativeint</span><span class="sxs-lookup"><span data-stu-id="71311-135">unativeint</span></span>|<span data-ttu-id="71311-136">作为无符号自然数的本机指针</span><span class="sxs-lookup"><span data-stu-id="71311-136">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="71311-137">un</span><span class="sxs-lookup"><span data-stu-id="71311-137">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="71311-138">int64</span><span class="sxs-lookup"><span data-stu-id="71311-138">int64</span></span>|<span data-ttu-id="71311-139">已签名64位整数</span><span class="sxs-lookup"><span data-stu-id="71311-139">signed 64-bit integer</span></span>|<span data-ttu-id="71311-140">L</span><span class="sxs-lookup"><span data-stu-id="71311-140">L</span></span>|`86L`|
|<span data-ttu-id="71311-141">uint64</span><span class="sxs-lookup"><span data-stu-id="71311-141">uint64</span></span>|<span data-ttu-id="71311-142">无符号64位自然数</span><span class="sxs-lookup"><span data-stu-id="71311-142">unsigned 64-bit natural number</span></span>|<span data-ttu-id="71311-143">UL</span><span class="sxs-lookup"><span data-stu-id="71311-143">UL</span></span>|`86UL`|
|<span data-ttu-id="71311-144">单个，float32</span><span class="sxs-lookup"><span data-stu-id="71311-144">single, float32</span></span>|<span data-ttu-id="71311-145">32位浮点数</span><span class="sxs-lookup"><span data-stu-id="71311-145">32-bit floating point number</span></span>|<span data-ttu-id="71311-146">F 或 f</span><span class="sxs-lookup"><span data-stu-id="71311-146">F or f</span></span>|<span data-ttu-id="71311-147">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="71311-147">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="71311-148">换行符</span><span class="sxs-lookup"><span data-stu-id="71311-148">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="71311-149">float仔细</span><span class="sxs-lookup"><span data-stu-id="71311-149">float; double</span></span>|<span data-ttu-id="71311-150">64位浮点数</span><span class="sxs-lookup"><span data-stu-id="71311-150">64-bit floating point number</span></span>|<span data-ttu-id="71311-151">无</span><span class="sxs-lookup"><span data-stu-id="71311-151">none</span></span>|<span data-ttu-id="71311-152">`4.14` 或 `2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="71311-152">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="71311-153">换行符</span><span class="sxs-lookup"><span data-stu-id="71311-153">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="71311-154">bigint</span><span class="sxs-lookup"><span data-stu-id="71311-154">bigint</span></span>|<span data-ttu-id="71311-155">不限于64位表示形式的整数</span><span class="sxs-lookup"><span data-stu-id="71311-155">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="71311-156">I</span><span class="sxs-lookup"><span data-stu-id="71311-156">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="71311-157">Decimal</span><span class="sxs-lookup"><span data-stu-id="71311-157">decimal</span></span>|<span data-ttu-id="71311-158">表示为固定点或有理数的小数</span><span class="sxs-lookup"><span data-stu-id="71311-158">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="71311-159">M 或 m</span><span class="sxs-lookup"><span data-stu-id="71311-159">M or m</span></span>|<span data-ttu-id="71311-160">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="71311-160">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="71311-161">Char</span><span class="sxs-lookup"><span data-stu-id="71311-161">Char</span></span>|<span data-ttu-id="71311-162">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="71311-162">Unicode character</span></span>|<span data-ttu-id="71311-163">无</span><span class="sxs-lookup"><span data-stu-id="71311-163">none</span></span>|<span data-ttu-id="71311-164">`'a'` 或 `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="71311-164">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="71311-165">String</span><span class="sxs-lookup"><span data-stu-id="71311-165">String</span></span>|<span data-ttu-id="71311-166">Unicode 字符串</span><span class="sxs-lookup"><span data-stu-id="71311-166">Unicode string</span></span>|<span data-ttu-id="71311-167">无</span><span class="sxs-lookup"><span data-stu-id="71311-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="71311-168">或</span><span class="sxs-lookup"><span data-stu-id="71311-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="71311-169">或</span><span class="sxs-lookup"><span data-stu-id="71311-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="71311-170">或</span><span class="sxs-lookup"><span data-stu-id="71311-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="71311-171">另请参阅 [字符串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="71311-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="71311-172">字节</span><span class="sxs-lookup"><span data-stu-id="71311-172">byte</span></span>|<span data-ttu-id="71311-173">ASCII 字符</span><span class="sxs-lookup"><span data-stu-id="71311-173">ASCII character</span></span>|<span data-ttu-id="71311-174">B</span><span class="sxs-lookup"><span data-stu-id="71311-174">B</span></span>|`'a'B`|
|<span data-ttu-id="71311-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="71311-175">byte[]</span></span>|<span data-ttu-id="71311-176">ASCII 字符串</span><span class="sxs-lookup"><span data-stu-id="71311-176">ASCII string</span></span>|<span data-ttu-id="71311-177">B</span><span class="sxs-lookup"><span data-stu-id="71311-177">B</span></span>|`"text"B`|
|<span data-ttu-id="71311-178">String 或 byte []</span><span class="sxs-lookup"><span data-stu-id="71311-178">String or byte[]</span></span>|<span data-ttu-id="71311-179">原义字符串</span><span class="sxs-lookup"><span data-stu-id="71311-179">verbatim string</span></span>|<span data-ttu-id="71311-180">@ prefix</span><span class="sxs-lookup"><span data-stu-id="71311-180">@ prefix</span></span>|<span data-ttu-id="71311-181">`@"\\server\share"` (Unicode) </span><span class="sxs-lookup"><span data-stu-id="71311-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="71311-182">`@"\\server\share"B` (ASCII) </span><span class="sxs-lookup"><span data-stu-id="71311-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="71311-183">命名文本</span><span class="sxs-lookup"><span data-stu-id="71311-183">Named literals</span></span>

<span data-ttu-id="71311-184">应为常量的值可以用 [文本](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) 属性进行标记。</span><span class="sxs-lookup"><span data-stu-id="71311-184">Values that are intended to be constants can be marked with the [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) attribute.</span></span> <span data-ttu-id="71311-185">此属性的作用是使值编译为常量。</span><span class="sxs-lookup"><span data-stu-id="71311-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="71311-186">在模式匹配表达式中，以小写字符开头的标识符始终被视为要绑定的变量而不是文本，因此在定义文本时通常应使用首字母大写。</span><span class="sxs-lookup"><span data-stu-id="71311-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="71311-187">注解</span><span class="sxs-lookup"><span data-stu-id="71311-187">Remarks</span></span>

<span data-ttu-id="71311-188">Unicode 字符串可以包含可使用指定的显式编码， `\u` 后跟16位十六进制代码 (0000-FFFF) 或32编码，可以通过使用 `\U` 后跟表示任何 Unicode 码位的32位十六进制代码 (00000000-0010ffff 之间) 。</span><span class="sxs-lookup"><span data-stu-id="71311-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="71311-189">不允许使用以外的其他位运算符 `|||` 。</span><span class="sxs-lookup"><span data-stu-id="71311-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="71311-190">其他基中的整数</span><span class="sxs-lookup"><span data-stu-id="71311-190">Integers in other bases</span></span>

<span data-ttu-id="71311-191">使用 `0x` 、或前缀，还可以使用十六进制、八进制或二进制格式指定已签名的32位整数 `0o` `0b` 。</span><span class="sxs-lookup"><span data-stu-id="71311-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="71311-192">数值文本中的下划线</span><span class="sxs-lookup"><span data-stu-id="71311-192">Underscores in numeric literals</span></span>

<span data-ttu-id="71311-193">可以用下划线字符 () 分隔数字 `_` 。</span><span class="sxs-lookup"><span data-stu-id="71311-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
