---
title: 指定完全限定的类型名称
description: 对于反射操作的有效输入，请使用完全限定的类型名称，其中包含程序集名称规范、命名空间规范和类型名称。
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
ms.openlocfilehash: ff33b6abd31a82c6b80aa794564c5c48648cde63
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865224"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="45605-103">指定完全限定的类型名称</span><span class="sxs-lookup"><span data-stu-id="45605-103">Specifying fully qualified type names</span></span>

<span data-ttu-id="45605-104">必须指定类型名称才能为各种反射操作提供有效输入。</span><span class="sxs-lookup"><span data-stu-id="45605-104">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="45605-105">完全限定的类型名称包含程序集名称规范、命名空间规范和类型名称。</span><span class="sxs-lookup"><span data-stu-id="45605-105">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="45605-106">类型名称规范由 <xref:System.Type.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> 等方法使用。</span><span class="sxs-lookup"><span data-stu-id="45605-106">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="45605-107">类型名称的语法</span><span class="sxs-lookup"><span data-stu-id="45605-107">Grammar for type names</span></span>

 <span data-ttu-id="45605-108">语法定义正式语言的语法。</span><span class="sxs-lookup"><span data-stu-id="45605-108">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="45605-109">下表列出了词法规则，说明如何识别有效输入。</span><span class="sxs-lookup"><span data-stu-id="45605-109">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="45605-110">最终元素（无法再减小的元素）全部以大写字母显示。</span><span class="sxs-lookup"><span data-stu-id="45605-110">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="45605-111">非最终元素（可以再减小的元素）则显示为大小写混合或带单引号的字符串，但单引号 (') 不是语法本身的一部分。</span><span class="sxs-lookup"><span data-stu-id="45605-111">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="45605-112">竖线 (|) 表示具有子规则的规则。</span><span class="sxs-lookup"><span data-stu-id="45605-112">The pipe character (&#124;) denotes rules that have subrules.</span></span>

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a><span data-ttu-id="45605-113">指定特殊字符</span><span class="sxs-lookup"><span data-stu-id="45605-113">Specifying special characters</span></span>

<span data-ttu-id="45605-114">在类型名称中，IDENTIFIER 是语言规则确定的任何有效名称。</span><span class="sxs-lookup"><span data-stu-id="45605-114">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="45605-115">反斜杠 (\\) 可用作转义符来分隔以下用作 IDENTIFIER 一部分的标记。</span><span class="sxs-lookup"><span data-stu-id="45605-115">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="45605-116">标记</span><span class="sxs-lookup"><span data-stu-id="45605-116">Token</span></span>|<span data-ttu-id="45605-117">含义</span><span class="sxs-lookup"><span data-stu-id="45605-117">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="45605-118">\\,</span><span class="sxs-lookup"><span data-stu-id="45605-118">\\,</span></span>|<span data-ttu-id="45605-119">程序集分隔符。</span><span class="sxs-lookup"><span data-stu-id="45605-119">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="45605-120">嵌套类型分隔符。</span><span class="sxs-lookup"><span data-stu-id="45605-120">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="45605-121">引用类型。</span><span class="sxs-lookup"><span data-stu-id="45605-121">Reference type.</span></span>|
|\\*|<span data-ttu-id="45605-122">指针类型。</span><span class="sxs-lookup"><span data-stu-id="45605-122">Pointer type.</span></span>|
|<span data-ttu-id="45605-123">\\[</span><span class="sxs-lookup"><span data-stu-id="45605-123">\\[</span></span>|<span data-ttu-id="45605-124">数组维度分隔符。</span><span class="sxs-lookup"><span data-stu-id="45605-124">Array dimension delimiter.</span></span>|
|<span data-ttu-id="45605-125">\\]</span><span class="sxs-lookup"><span data-stu-id="45605-125">\\]</span></span>|<span data-ttu-id="45605-126">数组维度分隔符。</span><span class="sxs-lookup"><span data-stu-id="45605-126">Array dimension delimiter.</span></span>|
|<span data-ttu-id="45605-127">\\.</span><span class="sxs-lookup"><span data-stu-id="45605-127">\\.</span></span>|<span data-ttu-id="45605-128">只有在数组规范中使用句点时，才应在句点前使用反斜杠。</span><span class="sxs-lookup"><span data-stu-id="45605-128">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="45605-129">NamespaceSpec 中的句点不使用反斜杠。</span><span class="sxs-lookup"><span data-stu-id="45605-129">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="45605-130">\\\|必要时将反斜杠用作字符串文本。</span><span class="sxs-lookup"><span data-stu-id="45605-130">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="45605-131">请注意，除 AssemblyNameSpec 外，所有 TypeSpec 组件中的空格都是相关的。</span><span class="sxs-lookup"><span data-stu-id="45605-131">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="45605-132">在 AssemblyNameSpec 中，“,”分隔符之前的空格相关，但“,”分隔符之后的空格将被忽略。</span><span class="sxs-lookup"><span data-stu-id="45605-132">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="45605-133">反射类（如 <xref:System.Type.FullName%2A?displayProperty=nameWithType>）返回改变后的名称，以便使返回的名称可以用在对 <xref:System.Type.GetType%2A> 的调用中（如同用在 `MyType.GetType(myType.FullName)` 中）。</span><span class="sxs-lookup"><span data-stu-id="45605-133">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="45605-134">例如，某个类型的完全限定名称可能是 `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`。</span><span class="sxs-lookup"><span data-stu-id="45605-134">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="45605-135">如果命名空间为 `Ozzy.Out+Back`，则必须在加号前加反斜杠。</span><span class="sxs-lookup"><span data-stu-id="45605-135">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="45605-136">否则，分析器会将其解释为嵌套分隔符。</span><span class="sxs-lookup"><span data-stu-id="45605-136">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="45605-137">反射会将该字符串当作 `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly` 发出。</span><span class="sxs-lookup"><span data-stu-id="45605-137">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="45605-138">指定程序集名称</span><span class="sxs-lookup"><span data-stu-id="45605-138">Specifying assembly names</span></span>

<span data-ttu-id="45605-139">程序集名称规范中至少需要具有程序集的文本名称 (IDENTIFIER)。</span><span class="sxs-lookup"><span data-stu-id="45605-139">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="45605-140">可以在 IDENTIFIER 后添加下表所述的以逗号分隔的属性/值对列表。</span><span class="sxs-lookup"><span data-stu-id="45605-140">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="45605-141">IDENTIFIER 命名应遵循文件命名的规则。</span><span class="sxs-lookup"><span data-stu-id="45605-141">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="45605-142">IDENTIFIER 不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="45605-142">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="45605-143">属性名称</span><span class="sxs-lookup"><span data-stu-id="45605-143">Property name</span></span>|<span data-ttu-id="45605-144">描述</span><span class="sxs-lookup"><span data-stu-id="45605-144">Description</span></span>|<span data-ttu-id="45605-145">允许的值</span><span class="sxs-lookup"><span data-stu-id="45605-145">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="45605-146">**Version**</span><span class="sxs-lookup"><span data-stu-id="45605-146">**Version**</span></span>|<span data-ttu-id="45605-147">程序集版本号</span><span class="sxs-lookup"><span data-stu-id="45605-147">Assembly version number</span></span>|<span data-ttu-id="45605-148">Major.Minor.Build.Revision，其中 Major、Minor、Build 和 Revision 是 0 和 65535 之间（含 0 和 65535）的整数      。</span><span class="sxs-lookup"><span data-stu-id="45605-148">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="45605-149">PublicKey</span><span class="sxs-lookup"><span data-stu-id="45605-149">**PublicKey**</span></span>|<span data-ttu-id="45605-150">完整公钥</span><span class="sxs-lookup"><span data-stu-id="45605-150">Full public key</span></span>|<span data-ttu-id="45605-151">完整公钥十六进制格式的字符串值。</span><span class="sxs-lookup"><span data-stu-id="45605-151">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="45605-152">指定 null 引用（在 Visual Basic 中为 Nothing）以显式指示私有程序集。</span><span class="sxs-lookup"><span data-stu-id="45605-152">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="45605-153">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="45605-153">**PublicKeyToken**</span></span>|<span data-ttu-id="45605-154">公钥标记（完整公钥的 8 字节哈希）</span><span class="sxs-lookup"><span data-stu-id="45605-154">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="45605-155">公钥标记十六进制格式的字符串值。</span><span class="sxs-lookup"><span data-stu-id="45605-155">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="45605-156">指定 null 引用（在 Visual Basic 中为 Nothing）以显式指示私有程序集  。</span><span class="sxs-lookup"><span data-stu-id="45605-156">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="45605-157">**区域性**</span><span class="sxs-lookup"><span data-stu-id="45605-157">**Culture**</span></span>|<span data-ttu-id="45605-158">程序集区域性</span><span class="sxs-lookup"><span data-stu-id="45605-158">Assembly culture</span></span>|<span data-ttu-id="45605-159">RFC-1766 格式的程序集区域性，对于独立于语言（非附属）的程序集则为“非特定”。</span><span class="sxs-lookup"><span data-stu-id="45605-159">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="45605-160">**自定义**</span><span class="sxs-lookup"><span data-stu-id="45605-160">**Custom**</span></span>|<span data-ttu-id="45605-161">自定义二进制大对象 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="45605-161">Custom binary large object (BLOB).</span></span> <span data-ttu-id="45605-162">它当前仅用于由[本机图像生成器 (Ngen)](../tools/ngen-exe-native-image-generator.md) 生成的程序集。</span><span class="sxs-lookup"><span data-stu-id="45605-162">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="45605-163">本机图像生成器工具用以向程序集缓存通知所安装程序集为本机图像的自定义字符串，因此该自定义字符串安装在本机图像缓存中。</span><span class="sxs-lookup"><span data-stu-id="45605-163">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="45605-164">也称作 zap 字符串。</span><span class="sxs-lookup"><span data-stu-id="45605-164">Also called a zap string.</span></span>|

<span data-ttu-id="45605-165">下面的示例演示具有默认区域性的简单命名程序集的 AssemblyName  。</span><span class="sxs-lookup"><span data-stu-id="45605-165">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="45605-166">下面的示例演示区域性为“en”的强名称程序集的完全指定的引用。</span><span class="sxs-lookup"><span data-stu-id="45605-166">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="45605-167">下面的示例演示部分指定的 AssemblyName，它可以由具有强名称或简单名称的程序集来满足  。</span><span class="sxs-lookup"><span data-stu-id="45605-167">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="45605-168">下面的示例分别演示一个部分指定的 AssemblyName，它必须由具有简单名称的程序集来满足  。</span><span class="sxs-lookup"><span data-stu-id="45605-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="45605-169">下面的示例分别演示一个部分指定的 AssemblyName，它必须由具有强名称的程序集来满足  。</span><span class="sxs-lookup"><span data-stu-id="45605-169">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="45605-170">指定泛型类型</span><span class="sxs-lookup"><span data-stu-id="45605-170">Specifying generic types</span></span>

<span data-ttu-id="45605-171">SimpleTypeSpec\`NUMBER 表示具有从 1 到 n  泛型类型参数的开放式泛型类型。</span><span class="sxs-lookup"><span data-stu-id="45605-171">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="45605-172">例如，若要获取对开放式泛型类型 List\<T> 或封闭式泛型类型 List\<String> 的引用，请使用 ``Type.GetType("System.Collections.Generic.List`1")``；若要获取对泛型类型 Dictionary\<TKey,TValue> 的引用，请使用 ``Type.GetType("System.Collections.Generic.Dictionary`2")``。</span><span class="sxs-lookup"><span data-stu-id="45605-172">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="45605-173">指定指针</span><span class="sxs-lookup"><span data-stu-id="45605-173">Specifying pointers</span></span>

<span data-ttu-id="45605-174">SimpleTypeSpec\* 表示未托管的指针。</span><span class="sxs-lookup"><span data-stu-id="45605-174">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="45605-175">例如，要获取指向 MyType 类型的指针，请使用 `Type.GetType("MyType*")`。</span><span class="sxs-lookup"><span data-stu-id="45605-175">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="45605-176">要获取指向 MyType 类型指针的指针，请使用 `Type.GetType("MyType**")`。</span><span class="sxs-lookup"><span data-stu-id="45605-176">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="45605-177">指定引用</span><span class="sxs-lookup"><span data-stu-id="45605-177">Specifying references</span></span>

<span data-ttu-id="45605-178">SimpleTypeSpec & 表示托管指针或引用。</span><span class="sxs-lookup"><span data-stu-id="45605-178">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="45605-179">例如，要获取对 MyType 类型的引用，请使用 `Type.GetType("MyType &")`。</span><span class="sxs-lookup"><span data-stu-id="45605-179">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="45605-180">请注意，与指针不同，引用仅限于一个级别。</span><span class="sxs-lookup"><span data-stu-id="45605-180">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="45605-181">指定数组</span><span class="sxs-lookup"><span data-stu-id="45605-181">Specifying arrays</span></span>

<span data-ttu-id="45605-182">在 BNF 语法中，ReflectionEmitDimension 仅适用于使用 <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> 检索的不完整类型定义。</span><span class="sxs-lookup"><span data-stu-id="45605-182">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="45605-183">不完整类型定义是使用 <xref:System.Reflection.Emit?displayProperty=nameWithType> 构造但没有对其调用 <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> 的 <xref:System.Reflection.Emit.TypeBuilder> 对象。</span><span class="sxs-lookup"><span data-stu-id="45605-183">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="45605-184">ReflectionDimension 可用于检索任何已完成的类型定义，即已加载的类型。</span><span class="sxs-lookup"><span data-stu-id="45605-184">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="45605-185">通过指定数组的级别，可以访问反射中的数组：</span><span class="sxs-lookup"><span data-stu-id="45605-185">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="45605-186">`Type.GetType("MyArray[]")` 获取下限为 0 的单维数组。</span><span class="sxs-lookup"><span data-stu-id="45605-186">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="45605-187">`Type.GetType("MyArray[*]")` 获取下限未知的单维数组。</span><span class="sxs-lookup"><span data-stu-id="45605-187">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="45605-188">`Type.GetType("MyArray[][]")` 获取二维数组的数组。</span><span class="sxs-lookup"><span data-stu-id="45605-188">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="45605-189">`Type.GetType("MyArray[*,*]")` 和 `Type.GetType("MyArray[,]")` 获取下限未知的矩形二维数组。</span><span class="sxs-lookup"><span data-stu-id="45605-189">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="45605-190">请注意，从运行时的角度来看，`MyArray[] != MyArray[*]`，但对于多维数组，这两种表示是等效的。</span><span class="sxs-lookup"><span data-stu-id="45605-190">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="45605-191">也就是说，`Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` 的计算结果为 true  。</span><span class="sxs-lookup"><span data-stu-id="45605-191">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="45605-192">对于 ModuleBuilder.GetType，`MyArray[0..5]` 指示大小为 6、下限为 0 的单维数组  。</span><span class="sxs-lookup"><span data-stu-id="45605-192">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="45605-193">`MyArray[4…]` 指示大小未知、下限为 4 的单维数组。</span><span class="sxs-lookup"><span data-stu-id="45605-193">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="45605-194">请参阅</span><span class="sxs-lookup"><span data-stu-id="45605-194">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="45605-195">查看类型信息</span><span class="sxs-lookup"><span data-stu-id="45605-195">Viewing Type Information</span></span>](viewing-type-information.md)
