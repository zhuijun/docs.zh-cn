---
title: 通用命名约定
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: c90987fd28d5157cfb7f7eea4680b5ab4be1a200
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290949"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="1e2b8-102">通用命名约定</span><span class="sxs-lookup"><span data-stu-id="1e2b8-102">General Naming Conventions</span></span>

<span data-ttu-id="1e2b8-103">本部分介绍与 word 选项相关的常规命名约定、有关使用缩写和首字母缩写词的准则，以及如何避免使用特定于语言的名称的建议。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>

## <a name="word-choice"></a><span data-ttu-id="1e2b8-104">Word 选项</span><span class="sxs-lookup"><span data-stu-id="1e2b8-104">Word Choice</span></span>
 <span data-ttu-id="1e2b8-105">✔️选择易于阅读的标识符名称。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-105">✔️ DO choose easily readable identifier names.</span></span>

 <span data-ttu-id="1e2b8-106">例如，名为的属性的 `HorizontalAlignment` 可读性比更强 `AlignmentHorizontal` 。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>

 <span data-ttu-id="1e2b8-107">✔️提高可读性比简洁。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-107">✔️ DO favor readability over brevity.</span></span>

 <span data-ttu-id="1e2b8-108">属性名称 `CanScrollHorizontally` 比 `ScrollableX` （对 X 轴的模糊引用）更好。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>

 <span data-ttu-id="1e2b8-109">❌不要使用下划线、连字符或任何其他非字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-109">❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.</span></span>

 <span data-ttu-id="1e2b8-110">❌不要使用匈牙利表示法。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-110">❌ DO NOT use Hungarian notation.</span></span>

 <span data-ttu-id="1e2b8-111">❌避免使用与广泛使用的编程语言的关键字冲突的标识符。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-111">❌ AVOID using identifiers that conflict with keywords of widely used programming languages.</span></span>

 <span data-ttu-id="1e2b8-112">根据公共语言规范（CLS）的规则4，所有符合语言都必须提供一种机制，以允许访问使用该语言的关键字作为标识符的已命名项。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="1e2b8-113">例如，在这种情况下，c # 使用 @ 符号作为转义机制。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="1e2b8-114">不过，最好是避免使用常见关键字，因为使用转义序列的方法比没有它的方法更难。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>

## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="1e2b8-115">使用缩写和首字母缩写</span><span class="sxs-lookup"><span data-stu-id="1e2b8-115">Using Abbreviations and Acronyms</span></span>
 <span data-ttu-id="1e2b8-116">❌不要使用缩写或缩写作为标识符名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-116">❌ DO NOT use abbreviations or contractions as part of identifier names.</span></span>

 <span data-ttu-id="1e2b8-117">例如，使用 `GetWindow` 而不是 `GetWin` 。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-117">For example, use `GetWindow` rather than `GetWin`.</span></span>

 <span data-ttu-id="1e2b8-118">❌不要使用未被广泛接受的任何首字母缩写，甚至在必要时才使用。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-118">❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>

## <a name="avoiding-language-specific-names"></a><span data-ttu-id="1e2b8-119">避免特定于语言的名称</span><span class="sxs-lookup"><span data-stu-id="1e2b8-119">Avoiding Language-Specific Names</span></span>
 <span data-ttu-id="1e2b8-120">✔️确实使用有语义的名称，而不是类型名称的特定于语言的关键字。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-120">✔️ DO use semantically interesting names rather than language-specific keywords for type names.</span></span>

 <span data-ttu-id="1e2b8-121">例如， `GetLength` 是比更好的名称 `GetInt` 。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-121">For example, `GetLength` is a better name than `GetInt`.</span></span>

 <span data-ttu-id="1e2b8-122">在极少数情况下，如果标识符没有超出其类型的语义含义，则✔️使用泛型 CLR 类型名称，而不是特定于语言的名称。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-122">✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>

 <span data-ttu-id="1e2b8-123">例如，转换为的方法 <xref:System.Int64> 应命名为 `ToInt64` ，而不是 `ToLong` （因为 <xref:System.Int64> 是特定于 c # 的别名的 CLR 名称 `long` ）。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="1e2b8-124">下表显示了几种使用 CLR 类型名称的基本数据类型（以及 c #、Visual Basic 和 c + + 的相应类型名称）。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>

|<span data-ttu-id="1e2b8-125">C#</span><span class="sxs-lookup"><span data-stu-id="1e2b8-125">C#</span></span>|<span data-ttu-id="1e2b8-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e2b8-126">Visual Basic</span></span>|<span data-ttu-id="1e2b8-127">C++</span><span class="sxs-lookup"><span data-stu-id="1e2b8-127">C++</span></span>|<span data-ttu-id="1e2b8-128">CLR</span><span class="sxs-lookup"><span data-stu-id="1e2b8-128">CLR</span></span>|
|---------|------------------|-----------|---------|
|<span data-ttu-id="1e2b8-129">sbyte</span><span class="sxs-lookup"><span data-stu-id="1e2b8-129">**sbyte**</span></span>|<span data-ttu-id="1e2b8-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-130">**SByte**</span></span>|<span data-ttu-id="1e2b8-131">**char**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-131">**char**</span></span>|<span data-ttu-id="1e2b8-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-132">**SByte**</span></span>|
|<span data-ttu-id="1e2b8-133">byte</span><span class="sxs-lookup"><span data-stu-id="1e2b8-133">**byte**</span></span>|<span data-ttu-id="1e2b8-134">**Byte**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-134">**Byte**</span></span>|<span data-ttu-id="1e2b8-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-135">**unsigned char**</span></span>|<span data-ttu-id="1e2b8-136">**Byte**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-136">**Byte**</span></span>|
|<span data-ttu-id="1e2b8-137">**short**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-137">**short**</span></span>|<span data-ttu-id="1e2b8-138">**短暂**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-138">**Short**</span></span>|<span data-ttu-id="1e2b8-139">**short**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-139">**short**</span></span>|<span data-ttu-id="1e2b8-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-140">**Int16**</span></span>|
|<span data-ttu-id="1e2b8-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-141">**ushort**</span></span>|<span data-ttu-id="1e2b8-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-142">**UInt16**</span></span>|<span data-ttu-id="1e2b8-143">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-143">**unsigned short**</span></span>|<span data-ttu-id="1e2b8-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-144">**UInt16**</span></span>|
|<span data-ttu-id="1e2b8-145">**int**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-145">**int**</span></span>|<span data-ttu-id="1e2b8-146">**整数**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-146">**Integer**</span></span>|<span data-ttu-id="1e2b8-147">**int**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-147">**int**</span></span>|<span data-ttu-id="1e2b8-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-148">**Int32**</span></span>|
|<span data-ttu-id="1e2b8-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-149">**uint**</span></span>|<span data-ttu-id="1e2b8-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-150">**UInt32**</span></span>|<span data-ttu-id="1e2b8-151">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-151">**unsigned int**</span></span>|<span data-ttu-id="1e2b8-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-152">**UInt32**</span></span>|
|<span data-ttu-id="1e2b8-153">**long**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-153">**long**</span></span>|<span data-ttu-id="1e2b8-154">**Long**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-154">**Long**</span></span>|<span data-ttu-id="1e2b8-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-155">**__int64**</span></span>|<span data-ttu-id="1e2b8-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-156">**Int64**</span></span>|
|<span data-ttu-id="1e2b8-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-157">**ulong**</span></span>|<span data-ttu-id="1e2b8-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-158">**UInt64**</span></span>|<span data-ttu-id="1e2b8-159">unsigned __int64 </span><span class="sxs-lookup"><span data-stu-id="1e2b8-159">**unsigned __int64**</span></span>|<span data-ttu-id="1e2b8-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-160">**UInt64**</span></span>|
|<span data-ttu-id="1e2b8-161">**float**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-161">**float**</span></span>|<span data-ttu-id="1e2b8-162">**单精度**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-162">**Single**</span></span>|<span data-ttu-id="1e2b8-163">**float**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-163">**float**</span></span>|<span data-ttu-id="1e2b8-164">**单精度**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-164">**Single**</span></span>|
|<span data-ttu-id="1e2b8-165">**double**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-165">**double**</span></span>|<span data-ttu-id="1e2b8-166">**双精度**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-166">**Double**</span></span>|<span data-ttu-id="1e2b8-167">**double**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-167">**double**</span></span>|<span data-ttu-id="1e2b8-168">**双精度**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-168">**Double**</span></span>|
|<span data-ttu-id="1e2b8-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-169">**bool**</span></span>|<span data-ttu-id="1e2b8-170">**布尔值**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-170">**Boolean**</span></span>|<span data-ttu-id="1e2b8-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-171">**bool**</span></span>|<span data-ttu-id="1e2b8-172">**布尔值**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-172">**Boolean**</span></span>|
|<span data-ttu-id="1e2b8-173">**char**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-173">**char**</span></span>|<span data-ttu-id="1e2b8-174">**Char**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-174">**Char**</span></span>|<span data-ttu-id="1e2b8-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-175">**wchar_t**</span></span>|<span data-ttu-id="1e2b8-176">**Char**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-176">**Char**</span></span>|
|<span data-ttu-id="1e2b8-177">**string**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-177">**string**</span></span>|<span data-ttu-id="1e2b8-178">**字符串**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-178">**String**</span></span>|<span data-ttu-id="1e2b8-179">**字符串**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-179">**String**</span></span>|<span data-ttu-id="1e2b8-180">**字符串**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-180">**String**</span></span>|
|<span data-ttu-id="1e2b8-181">对象</span><span class="sxs-lookup"><span data-stu-id="1e2b8-181">**object**</span></span>|<span data-ttu-id="1e2b8-182">**Object**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-182">**Object**</span></span>|<span data-ttu-id="1e2b8-183">**Object**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-183">**Object**</span></span>|<span data-ttu-id="1e2b8-184">**Object**</span><span class="sxs-lookup"><span data-stu-id="1e2b8-184">**Object**</span></span>|

 <span data-ttu-id="1e2b8-185">✔️使用公用名（如 `value` 或 `item` ），而不是重复类型名称，在极少数情况下，标识符没有语义含义，并且参数的类型并不重要。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-185">✔️ DO  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>

## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="1e2b8-186">命名现有 Api 的新版本</span><span class="sxs-lookup"><span data-stu-id="1e2b8-186">Naming New Versions of Existing APIs</span></span>
 <span data-ttu-id="1e2b8-187">创建现有 API 的新版本时，✔️使用类似于旧 API 的名称。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-187">✔️ DO use a name similar to the old API when creating new versions of an existing API.</span></span>

 <span data-ttu-id="1e2b8-188">这有助于突出显示 Api 之间的关系。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-188">This helps to highlight the relationship between the APIs.</span></span>

 <span data-ttu-id="1e2b8-189">✔️确实更喜欢添加后缀（而非前缀）来指示现有 API 的新版本。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-189">✔️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>

 <span data-ttu-id="1e2b8-190">这将有助于在浏览文档或使用 IntelliSense 时发现。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-190">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="1e2b8-191">旧版本的 API 将被组织到新的 Api 附近，因为大多数浏览器和 IntelliSense 都按字母顺序显示标识符。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-191">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>

 <span data-ttu-id="1e2b8-192">✔️考虑使用全新但有意义的标识符，而不是添加后缀或前缀。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-192">✔️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>

 <span data-ttu-id="1e2b8-193">✔️使用数字后缀来指示现有 API 的新版本，尤其当 API 的现有名称是有意义的唯一名称（即，如果它是行业标准），并且如果添加任何有意义的后缀（或更改名称）不是合适的选项。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-193">✔️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>

 <span data-ttu-id="1e2b8-194">❌不要使用标识符的 "Ex" （或类似的）后缀来区分它与早期版本的同一 API。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-194">❌ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>

 <span data-ttu-id="1e2b8-195">当引入对64位整数（长整数）而不是32位整数运行的 Api 版本时，✔️确实使用 "64" 后缀。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-195">✔️ DO use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="1e2b8-196">仅当存在现有的32位 API 时，才需要采用此方法;请勿使用只有64位版本的新 Api。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-196">You only need to take this approach when the existing 32-bit API exists; don't do it for brand new APIs with only a 64-bit version.</span></span>

 <span data-ttu-id="1e2b8-197">*部分 &copy; 2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="1e2b8-197">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1e2b8-198">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="1e2b8-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1e2b8-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e2b8-199">See also</span></span>

- [<span data-ttu-id="1e2b8-200">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="1e2b8-200">Framework design guidelines</span></span>](index.md)
- [<span data-ttu-id="1e2b8-201">命名准则</span><span class="sxs-lookup"><span data-stu-id="1e2b8-201">Naming guidelines</span></span>](naming-guidelines.md)
- [<span data-ttu-id="1e2b8-202">EditorConfig 适用的 .NET 命名约定</span><span class="sxs-lookup"><span data-stu-id="1e2b8-202">.NET naming conventions for EditorConfig</span></span>](/visualstudio/ide/editorconfig-naming-conventions)
