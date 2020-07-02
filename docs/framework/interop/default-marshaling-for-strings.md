---
title: 字符串的默认封送处理
description: 查看 .NET 中接口、平台调用、结构和定长字符串缓冲区中的字符串的默认封送行为。
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
ms.openlocfilehash: 440a49730f351b820cd68a741e79f94434f585c8
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904112"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="bbb22-103">字符串的默认封送处理</span><span class="sxs-lookup"><span data-stu-id="bbb22-103">Default Marshaling for Strings</span></span>

<span data-ttu-id="bbb22-104"><xref:System.String?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 类均具有类似的封送处理行为。</span><span class="sxs-lookup"><span data-stu-id="bbb22-104">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="bbb22-105">字符串以 COM 样式 `BSTR` 类型或以 null 结尾的字符串（以 null 字符结尾的字符数组）进行封送。</span><span class="sxs-lookup"><span data-stu-id="bbb22-105">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="bbb22-106">字符串中的字符可以采用 Unicode（Windows 系统上的默认值）或 ANSI 进行封送。</span><span class="sxs-lookup"><span data-stu-id="bbb22-106">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="bbb22-107">在接口中使用的字符串</span><span class="sxs-lookup"><span data-stu-id="bbb22-107">Strings Used in Interfaces</span></span>

<span data-ttu-id="bbb22-108">下表显示以非托管代码的方法自变量封送字符串数据类型时的封送处理选项。</span><span class="sxs-lookup"><span data-stu-id="bbb22-108">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="bbb22-109"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性向 COM 接口的封送字符串提供若干个 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举值。</span><span class="sxs-lookup"><span data-stu-id="bbb22-109">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="bbb22-110">枚举类型</span><span class="sxs-lookup"><span data-stu-id="bbb22-110">Enumeration type</span></span>|<span data-ttu-id="bbb22-111">非托管格式说明</span><span class="sxs-lookup"><span data-stu-id="bbb22-111">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="bbb22-112">`UnmanagedType.BStr`（默认值）</span><span class="sxs-lookup"><span data-stu-id="bbb22-112">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="bbb22-113">具有预先固定长度和 Unicode 字符的 COM 样式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="bbb22-113">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="bbb22-114">指向以 null 终止的 ANSI 字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-114">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="bbb22-115">指向以 null 终止的 Unicode 字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-115">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="bbb22-116">此表适用于 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="bbb22-116">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="bbb22-117">对于 <xref:System.Text.StringBuilder>，仅允许使用 `UnmanagedType.LPStr` 和`UnmanagedType.LPWStr` 两个选项。</span><span class="sxs-lookup"><span data-stu-id="bbb22-117">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="bbb22-118">以下示例演示在 `IStringWorker` 接口中声明的字符串。</span><span class="sxs-lookup"><span data-stu-id="bbb22-118">The following example shows strings declared in the `IStringWorker` interface.</span></span>

```csharp
public interface IStringWorker
{
    void PassString1(string s);
    void PassString2([MarshalAs(UnmanagedType.BStr)] string s);
    void PassString3([MarshalAs(UnmanagedType.LPStr)] string s);
    void PassString4([MarshalAs(UnmanagedType.LPWStr)] string s);
    void PassStringRef1(ref string s);
    void PassStringRef2([MarshalAs(UnmanagedType.BStr)] ref string s);
    void PassStringRef3([MarshalAs(UnmanagedType.LPStr)] ref string s);
    void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)] ref string s);
}
```

```vb
Public Interface IStringWorker
    Sub PassString1(s As String)
    Sub PassString2(<MarshalAs(UnmanagedType.BStr)> s As String)
    Sub PassString3(<MarshalAs(UnmanagedType.LPStr)> s As String)
    Sub PassString4(<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Sub PassStringRef1(ByRef s As String)
    Sub PassStringRef2(<MarshalAs(UnmanagedType.BStr)> ByRef s As String)
    Sub PassStringRef3(<MarshalAs(UnmanagedType.LPStr)> ByRef s As String)
    Sub PassStringRef4(<MarshalAs(UnmanagedType.LPWStr)> ByRef s As String)
End Interface
```

<span data-ttu-id="bbb22-119">以下示例演示类型库中描述的相应接口。</span><span class="sxs-lookup"><span data-stu-id="bbb22-119">The following example shows the corresponding interface described in a type library.</span></span>

```cpp
interface IStringWorker : IDispatch
{
    HRESULT PassString1([in] BSTR s);
    HRESULT PassString2([in] BSTR s);
    HRESULT PassString3([in] LPStr s);
    HRESULT PassString4([in] LPWStr s);
    HRESULT PassStringRef1([in, out] BSTR *s);
    HRESULT PassStringRef2([in, out] BSTR *s);
    HRESULT PassStringRef3([in, out] LPStr *s);
    HRESULT PassStringRef4([in, out] LPWStr *s);
};
```

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="bbb22-120">在平台调用中使用的字符串</span><span class="sxs-lookup"><span data-stu-id="bbb22-120">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="bbb22-121">平台调用复制字符串参数，将其从.NET Framework 格式 (Unicode) 转换为平台非托管格式。</span><span class="sxs-lookup"><span data-stu-id="bbb22-121">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="bbb22-122">当调用返回时，字符串固定不变，且不会从非托管内存复制回托管内存。</span><span class="sxs-lookup"><span data-stu-id="bbb22-122">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="bbb22-123">下表列出以平台调用的方法参数封送字符串时的封送处理选项。</span><span class="sxs-lookup"><span data-stu-id="bbb22-123">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="bbb22-124"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性向封送字符串提供若干个 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举值。</span><span class="sxs-lookup"><span data-stu-id="bbb22-124">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="bbb22-125">枚举类型</span><span class="sxs-lookup"><span data-stu-id="bbb22-125">Enumeration type</span></span>|<span data-ttu-id="bbb22-126">非托管格式说明</span><span class="sxs-lookup"><span data-stu-id="bbb22-126">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="bbb22-127">具有预先固定长度和 ANSI 字符的 COM 样式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="bbb22-127">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="bbb22-128">具有预先固定长度和 Unicode 字符的 COM 样式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="bbb22-128">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="bbb22-129">`UnmanagedType.LPStr`（默认值）</span><span class="sxs-lookup"><span data-stu-id="bbb22-129">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="bbb22-130">指向以 null 终止的 ANSI 字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-130">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="bbb22-131">指向以 null 终止的平台相关字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-131">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="bbb22-132">指向以 null 终止的 UTF-8 编码字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-132">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="bbb22-133">指向以 null 终止的 Unicode 字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-133">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="bbb22-134">具有预先固定长度和平台相关字符的 COM 样式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="bbb22-134">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="bbb22-135">使 Visual Basic .NET 能够在非托管代码中更改字符串，并在托管代码中反映出结果的值。</span><span class="sxs-lookup"><span data-stu-id="bbb22-135">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="bbb22-136">此值仅支持用于平台调用。</span><span class="sxs-lookup"><span data-stu-id="bbb22-136">This value is supported only for platform invoke.</span></span> <span data-ttu-id="bbb22-137">这是 `ByVal` 字符串在 Visual Basic 中的默认值。</span><span class="sxs-lookup"><span data-stu-id="bbb22-137">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="bbb22-138">此表适用于 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="bbb22-138">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="bbb22-139">对于 <xref:System.Text.StringBuilder>，仅允许使用 `LPStr`、`LPTStr` 和 `LPWStr` 三个选项。</span><span class="sxs-lookup"><span data-stu-id="bbb22-139">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="bbb22-140">以下类型定义演示 `MarshalAsAttribute` 平台调用的正确用法。</span><span class="sxs-lookup"><span data-stu-id="bbb22-140">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

```csharp
class StringLibAPI
{
    [DllImport("StringLib.dll")]
    public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPWStr([MarshalAs(UnmanagedType.LPWStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPTStr([MarshalAs(UnmanagedType.LPTStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPUTF8Str([MarshalAs(UnmanagedType.LPUTF8Str)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)] string s);
}
```

```vb
Class StringLibAPI
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassLPUTF8Str Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPUTF8Str)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a><span data-ttu-id="bbb22-141">在结构中使用的字符串</span><span class="sxs-lookup"><span data-stu-id="bbb22-141">Strings Used in Structures</span></span>

<span data-ttu-id="bbb22-142">字符串是结构的有效成员，但是 <xref:System.Text.StringBuilder> 缓冲区在结构中无效。</span><span class="sxs-lookup"><span data-stu-id="bbb22-142">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="bbb22-143">下表显示以字段形式封送 <xref:System.String> 数据类型时的封送选项。</span><span class="sxs-lookup"><span data-stu-id="bbb22-143">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="bbb22-144"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性向字段的封送字符串提供若干个 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举值。</span><span class="sxs-lookup"><span data-stu-id="bbb22-144">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="bbb22-145">枚举类型</span><span class="sxs-lookup"><span data-stu-id="bbb22-145">Enumeration type</span></span>|<span data-ttu-id="bbb22-146">非托管格式说明</span><span class="sxs-lookup"><span data-stu-id="bbb22-146">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="bbb22-147">具有预先固定长度和 Unicode 字符的 COM 样式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="bbb22-147">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="bbb22-148">`UnmanagedType.LPStr`（默认值）</span><span class="sxs-lookup"><span data-stu-id="bbb22-148">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="bbb22-149">指向以 null 终止的 ANSI 字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-149">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="bbb22-150">指向以 null 终止的平台相关字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-150">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="bbb22-151">指向以 null 终止的 UTF-8 编码字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-151">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="bbb22-152">指向以 null 终止的 Unicode 字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="bbb22-152">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="bbb22-153">定长字符数组；数组的类型由包含结构的字符集确定。</span><span class="sxs-lookup"><span data-stu-id="bbb22-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="bbb22-154">`ByValTStr` 类型用于结构中出现的内联定长字符数组。</span><span class="sxs-lookup"><span data-stu-id="bbb22-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="bbb22-155">其他类型适用于包含指向字符串的指针的结构中包含的字符串引用。</span><span class="sxs-lookup"><span data-stu-id="bbb22-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="bbb22-156">应用于包含结构的 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 的 `CharSet` 参数确定结构中字符串的字符格式。</span><span class="sxs-lookup"><span data-stu-id="bbb22-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="bbb22-157">以下示例结构包含字符串引用和内联字符串，以及 ANSI、Unicode 和平台相关字符。</span><span class="sxs-lookup"><span data-stu-id="bbb22-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="bbb22-158">这些结构在类型库中的表示形式如下面的 C++ 代码所示：</span><span class="sxs-lookup"><span data-stu-id="bbb22-158">The representation of these structures in a type library is shown in the following C++ code:</span></span>

```cpp
struct StringInfoA
{
    char *  f1;
    char    f2[256];
};

struct StringInfoW
{
    WCHAR * f1;
    WCHAR   f2[256];
    BSTR    f3;
};

struct StringInfoT
{
    TCHAR * f1;
    TCHAR   f2[256];
};
```

<span data-ttu-id="bbb22-159">以下示例演示如何使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 以不同的格式定义相同的结构。</span><span class="sxs-lookup"><span data-stu-id="bbb22-159">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
struct StringInfoA
{
    [MarshalAs(UnmanagedType.LPStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
struct StringInfoW
{
    [MarshalAs(UnmanagedType.LPWStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
    [MarshalAs(UnmanagedType.BStr)] public string f3;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Auto)]
struct StringInfoT
{
    [MarshalAs(UnmanagedType.LPTStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}
```

```vb
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _
Structure StringInfoA
    <MarshalAs(UnmanagedType.LPStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
End Structure

<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _
Structure StringInfoW
    <MarshalAs(UnmanagedType.LPWStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
<MarshalAs(UnmanagedType.BStr)> Public f3 As String
End Structure

<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _
Structure StringInfoT
    <MarshalAs(UnmanagedType.LPTStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
End Structure
```

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="bbb22-160">定长字符串缓冲区</span><span class="sxs-lookup"><span data-stu-id="bbb22-160">Fixed-Length String Buffers</span></span>

<span data-ttu-id="bbb22-161">在某些情况下，必须将定长字符缓冲区传递到要操作的非托管代码中。</span><span class="sxs-lookup"><span data-stu-id="bbb22-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="bbb22-162">在这种情况下，只传递字符串将不起作用，因为被调用方不能修改所传递缓冲区的内容。</span><span class="sxs-lookup"><span data-stu-id="bbb22-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="bbb22-163">即使通过引用传递字符串，仍无法将缓冲区初始化为给定大小。</span><span class="sxs-lookup"><span data-stu-id="bbb22-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="bbb22-164">解决方法是将 <xref:System.Text.StringBuilder> 缓冲区作为参数（而不是 <xref:System.String>）传递。</span><span class="sxs-lookup"><span data-stu-id="bbb22-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="bbb22-165">被调用方可以取消引用和修改 `StringBuilder`，前提是不超过 `StringBuilder` 的容量。</span><span class="sxs-lookup"><span data-stu-id="bbb22-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="bbb22-166">还可以初始化为固定长度。</span><span class="sxs-lookup"><span data-stu-id="bbb22-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="bbb22-167">例如，如果将 `StringBuilder` 缓冲区初始化为 `N` 容量，则封送处理程序提供大小为 (`N`+ 1) 个字符的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="bbb22-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="bbb22-168">+1 解释了非托管字符串具有 null 终止符而帐户 `StringBuilder` 却不具有这一事实。</span><span class="sxs-lookup"><span data-stu-id="bbb22-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="bbb22-169">例如，Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API 函数（在 *winuser.h* 中定义）要求调用方传递函数向其中写入窗口文本的固定长度字符缓冲区。</span><span class="sxs-lookup"><span data-stu-id="bbb22-169">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="bbb22-170">`LpString` 指向调用方分配的大小为 `nMaxCount` 的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="bbb22-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="bbb22-171">调用方应分配缓冲区，并将 `nMaxCount` 自变量设置为已分配缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="bbb22-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="bbb22-172">以下示例显示 `GetWindowText` 函数声明，如 *winuser.h* 中所定义。</span><span class="sxs-lookup"><span data-stu-id="bbb22-172">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="bbb22-173">被调用方可以取消引用和修改 `StringBuilder`，前提是不超过 `StringBuilder` 的容量。</span><span class="sxs-lookup"><span data-stu-id="bbb22-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="bbb22-174">下面的代码示例演示如何将 `StringBuilder` 初始化为固定长度。</span><span class="sxs-lookup"><span data-stu-id="bbb22-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;
using System.Text;

internal static class NativeMethods
{
    [DllImport("User32.dll")]
    internal static extern void GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount);
}

public class Window
{
    internal IntPtr h;        // Internal handle to Window.
    public String GetText()
    {
        StringBuilder sb = new StringBuilder(256);
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Imports System.Text

Friend Class NativeMethods
    Friend Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="bbb22-175">请参阅</span><span class="sxs-lookup"><span data-stu-id="bbb22-175">See also</span></span>

- [<span data-ttu-id="bbb22-176">默认封送处理行为</span><span class="sxs-lookup"><span data-stu-id="bbb22-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="bbb22-177">封送处理字符串</span><span class="sxs-lookup"><span data-stu-id="bbb22-177">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="bbb22-178">可直接复制到本机结构中的类型和非直接复制到本机结构中的类型</span><span class="sxs-lookup"><span data-stu-id="bbb22-178">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="bbb22-179">[方向特性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bbb22-179">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="bbb22-180">复制和锁定</span><span class="sxs-lookup"><span data-stu-id="bbb22-180">Copying and Pinning</span></span>](copying-and-pinning.md)
