---
title: 文字
description: '了解 F # 编程语言中的文本类型。'
ms.date: 06/28/2019
ms.openlocfilehash: 98d609a1cf0beb00c0dd4d45ea343aaa2280b62e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855018"
---
# <a name="literals"></a><span data-ttu-id="33060-103">文字</span><span class="sxs-lookup"><span data-stu-id="33060-103">Literals</span></span>

<span data-ttu-id="33060-104">本文提供了一个表，其中显示了如何指定 F # 中的文本类型。</span><span class="sxs-lookup"><span data-stu-id="33060-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

> [!NOTE]
> <span data-ttu-id="33060-105">F # 的 docs.microsoft.com API 参考未完成。</span><span class="sxs-lookup"><span data-stu-id="33060-105">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="33060-106">如果遇到任何断开的链接，请参阅[F # 核心库文档](https://fsharp.github.io/fsharp-core-docs/)。</span><span class="sxs-lookup"><span data-stu-id="33060-106">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="literal-types"></a><span data-ttu-id="33060-107">文本类型</span><span class="sxs-lookup"><span data-stu-id="33060-107">Literal types</span></span>

<span data-ttu-id="33060-108">下表显示 F # 中的文本类型。</span><span class="sxs-lookup"><span data-stu-id="33060-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="33060-109">用十六进制表示法表示数字的字符不区分大小写;标识该类型的字符区分大小写。</span><span class="sxs-lookup"><span data-stu-id="33060-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="33060-110">类型</span><span class="sxs-lookup"><span data-stu-id="33060-110">Type</span></span>|<span data-ttu-id="33060-111">描述</span><span class="sxs-lookup"><span data-stu-id="33060-111">Description</span></span>|<span data-ttu-id="33060-112">后缀或前缀</span><span class="sxs-lookup"><span data-stu-id="33060-112">Suffix or prefix</span></span>|<span data-ttu-id="33060-113">示例</span><span class="sxs-lookup"><span data-stu-id="33060-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="33060-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="33060-114">sbyte</span></span>|<span data-ttu-id="33060-115">8位有符号整数</span><span class="sxs-lookup"><span data-stu-id="33060-115">signed 8-bit integer</span></span>|<span data-ttu-id="33060-116">y</span><span class="sxs-lookup"><span data-stu-id="33060-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="33060-117">字节</span><span class="sxs-lookup"><span data-stu-id="33060-117">byte</span></span>|<span data-ttu-id="33060-118">无符号8位自然数</span><span class="sxs-lookup"><span data-stu-id="33060-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="33060-119">uy</span><span class="sxs-lookup"><span data-stu-id="33060-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="33060-120">int16</span><span class="sxs-lookup"><span data-stu-id="33060-120">int16</span></span>|<span data-ttu-id="33060-121">16位带符号整数</span><span class="sxs-lookup"><span data-stu-id="33060-121">signed 16-bit integer</span></span>|<span data-ttu-id="33060-122">s</span><span class="sxs-lookup"><span data-stu-id="33060-122">s</span></span>|`86s`|
|<span data-ttu-id="33060-123">uint16</span><span class="sxs-lookup"><span data-stu-id="33060-123">uint16</span></span>|<span data-ttu-id="33060-124">无符号16位自然数</span><span class="sxs-lookup"><span data-stu-id="33060-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="33060-125">us</span><span class="sxs-lookup"><span data-stu-id="33060-125">us</span></span>|`86us`|
|<span data-ttu-id="33060-126">int</span><span class="sxs-lookup"><span data-stu-id="33060-126">int</span></span><br /><br /><span data-ttu-id="33060-127">int32</span><span class="sxs-lookup"><span data-stu-id="33060-127">int32</span></span>|<span data-ttu-id="33060-128">已签名32位整数</span><span class="sxs-lookup"><span data-stu-id="33060-128">signed 32-bit integer</span></span>|<span data-ttu-id="33060-129">l 或无</span><span class="sxs-lookup"><span data-stu-id="33060-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="33060-130">uint</span><span class="sxs-lookup"><span data-stu-id="33060-130">uint</span></span><br /><br /><span data-ttu-id="33060-131">uint32</span><span class="sxs-lookup"><span data-stu-id="33060-131">uint32</span></span>|<span data-ttu-id="33060-132">无符号32位自然数</span><span class="sxs-lookup"><span data-stu-id="33060-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="33060-133">u 或 ul</span><span class="sxs-lookup"><span data-stu-id="33060-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="33060-134">nativeint</span><span class="sxs-lookup"><span data-stu-id="33060-134">nativeint</span></span>|<span data-ttu-id="33060-135">指向有符号自然数的本机指针</span><span class="sxs-lookup"><span data-stu-id="33060-135">native pointer to a signed natural number</span></span>|<span data-ttu-id="33060-136">n</span><span class="sxs-lookup"><span data-stu-id="33060-136">n</span></span>|`123n`|
|<span data-ttu-id="33060-137">unativeint</span><span class="sxs-lookup"><span data-stu-id="33060-137">unativeint</span></span>|<span data-ttu-id="33060-138">作为无符号自然数的本机指针</span><span class="sxs-lookup"><span data-stu-id="33060-138">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="33060-139">un</span><span class="sxs-lookup"><span data-stu-id="33060-139">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="33060-140">int64</span><span class="sxs-lookup"><span data-stu-id="33060-140">int64</span></span>|<span data-ttu-id="33060-141">已签名64位整数</span><span class="sxs-lookup"><span data-stu-id="33060-141">signed 64-bit integer</span></span>|<span data-ttu-id="33060-142">L</span><span class="sxs-lookup"><span data-stu-id="33060-142">L</span></span>|`86L`|
|<span data-ttu-id="33060-143">uint64</span><span class="sxs-lookup"><span data-stu-id="33060-143">uint64</span></span>|<span data-ttu-id="33060-144">无符号64位自然数</span><span class="sxs-lookup"><span data-stu-id="33060-144">unsigned 64-bit natural number</span></span>|<span data-ttu-id="33060-145">UL</span><span class="sxs-lookup"><span data-stu-id="33060-145">UL</span></span>|`86UL`|
|<span data-ttu-id="33060-146">单个，float32</span><span class="sxs-lookup"><span data-stu-id="33060-146">single, float32</span></span>|<span data-ttu-id="33060-147">32位浮点数</span><span class="sxs-lookup"><span data-stu-id="33060-147">32-bit floating point number</span></span>|<span data-ttu-id="33060-148">F 或 f</span><span class="sxs-lookup"><span data-stu-id="33060-148">F or f</span></span>|<span data-ttu-id="33060-149">`4.14F` 或 `4.14f`</span><span class="sxs-lookup"><span data-stu-id="33060-149">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="33060-150">换行符</span><span class="sxs-lookup"><span data-stu-id="33060-150">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="33060-151">float仔细</span><span class="sxs-lookup"><span data-stu-id="33060-151">float; double</span></span>|<span data-ttu-id="33060-152">64位浮点数</span><span class="sxs-lookup"><span data-stu-id="33060-152">64-bit floating point number</span></span>|<span data-ttu-id="33060-153">无</span><span class="sxs-lookup"><span data-stu-id="33060-153">none</span></span>|<span data-ttu-id="33060-154">`4.14` 或 `2.3E+32` 或 `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="33060-154">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="33060-155">换行符</span><span class="sxs-lookup"><span data-stu-id="33060-155">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="33060-156">bigint</span><span class="sxs-lookup"><span data-stu-id="33060-156">bigint</span></span>|<span data-ttu-id="33060-157">不限于64位表示形式的整数</span><span class="sxs-lookup"><span data-stu-id="33060-157">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="33060-158">I</span><span class="sxs-lookup"><span data-stu-id="33060-158">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="33060-159">Decimal</span><span class="sxs-lookup"><span data-stu-id="33060-159">decimal</span></span>|<span data-ttu-id="33060-160">表示为固定点或有理数的小数</span><span class="sxs-lookup"><span data-stu-id="33060-160">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="33060-161">M 或 m</span><span class="sxs-lookup"><span data-stu-id="33060-161">M or m</span></span>|<span data-ttu-id="33060-162">`0.7833M` 或 `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="33060-162">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="33060-163">Char</span><span class="sxs-lookup"><span data-stu-id="33060-163">Char</span></span>|<span data-ttu-id="33060-164">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="33060-164">Unicode character</span></span>|<span data-ttu-id="33060-165">无</span><span class="sxs-lookup"><span data-stu-id="33060-165">none</span></span>|<span data-ttu-id="33060-166">`'a'` 或 `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="33060-166">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="33060-167">String</span><span class="sxs-lookup"><span data-stu-id="33060-167">String</span></span>|<span data-ttu-id="33060-168">Unicode 字符串</span><span class="sxs-lookup"><span data-stu-id="33060-168">Unicode string</span></span>|<span data-ttu-id="33060-169">无</span><span class="sxs-lookup"><span data-stu-id="33060-169">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="33060-170">或</span><span class="sxs-lookup"><span data-stu-id="33060-170">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="33060-171">或</span><span class="sxs-lookup"><span data-stu-id="33060-171">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="33060-172">或</span><span class="sxs-lookup"><span data-stu-id="33060-172">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="33060-173">另请参阅[字符串](Strings.md)。</span><span class="sxs-lookup"><span data-stu-id="33060-173">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="33060-174">字节</span><span class="sxs-lookup"><span data-stu-id="33060-174">byte</span></span>|<span data-ttu-id="33060-175">ASCII 字符</span><span class="sxs-lookup"><span data-stu-id="33060-175">ASCII character</span></span>|<span data-ttu-id="33060-176">B</span><span class="sxs-lookup"><span data-stu-id="33060-176">B</span></span>|`'a'B`|
|<span data-ttu-id="33060-177">byte[]</span><span class="sxs-lookup"><span data-stu-id="33060-177">byte[]</span></span>|<span data-ttu-id="33060-178">ASCII 字符串</span><span class="sxs-lookup"><span data-stu-id="33060-178">ASCII string</span></span>|<span data-ttu-id="33060-179">B</span><span class="sxs-lookup"><span data-stu-id="33060-179">B</span></span>|`"text"B`|
|<span data-ttu-id="33060-180">String 或 byte []</span><span class="sxs-lookup"><span data-stu-id="33060-180">String or byte[]</span></span>|<span data-ttu-id="33060-181">原义字符串</span><span class="sxs-lookup"><span data-stu-id="33060-181">verbatim string</span></span>|<span data-ttu-id="33060-182">@ prefix</span><span class="sxs-lookup"><span data-stu-id="33060-182">@ prefix</span></span>|<span data-ttu-id="33060-183">`@"\\server\share"` (Unicode) </span><span class="sxs-lookup"><span data-stu-id="33060-183">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="33060-184">`@"\\server\share"B` (ASCII) </span><span class="sxs-lookup"><span data-stu-id="33060-184">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="33060-185">命名文本</span><span class="sxs-lookup"><span data-stu-id="33060-185">Named literals</span></span>

<span data-ttu-id="33060-186">应为常量的值可以用[文本](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)属性进行标记。</span><span class="sxs-lookup"><span data-stu-id="33060-186">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="33060-187">此属性的作用是使值编译为常量。</span><span class="sxs-lookup"><span data-stu-id="33060-187">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="33060-188">在模式匹配表达式中，以小写字符开头的标识符始终被视为要绑定的变量而不是文本，因此在定义文本时通常应使用首字母大写。</span><span class="sxs-lookup"><span data-stu-id="33060-188">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="33060-189">备注</span><span class="sxs-lookup"><span data-stu-id="33060-189">Remarks</span></span>

<span data-ttu-id="33060-190">Unicode 字符串可以包含可使用指定的显式编码， `\u` 后跟16位十六进制代码 (0000-FFFF) 或32编码，可以通过使用 `\U` 后跟表示任何 Unicode 码位的32位十六进制代码 (00000000-0010ffff 之间) 。</span><span class="sxs-lookup"><span data-stu-id="33060-190">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="33060-191">不允许使用以外的其他位运算符 `|||` 。</span><span class="sxs-lookup"><span data-stu-id="33060-191">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="33060-192">其他基中的整数</span><span class="sxs-lookup"><span data-stu-id="33060-192">Integers in other bases</span></span>

<span data-ttu-id="33060-193">使用 `0x` 、或前缀，还可以使用十六进制、八进制或二进制格式指定已签名的32位整数 `0o` `0b` 。</span><span class="sxs-lookup"><span data-stu-id="33060-193">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="33060-194">数值文本中的下划线</span><span class="sxs-lookup"><span data-stu-id="33060-194">Underscores in numeric literals</span></span>

<span data-ttu-id="33060-195">可以用下划线字符 () 分隔数字 `_` 。</span><span class="sxs-lookup"><span data-stu-id="33060-195">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="33060-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33060-196">See also</span></span>

- [<span data-ttu-id="33060-197">LiteralAttribute 类</span><span class="sxs-lookup"><span data-stu-id="33060-197">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
