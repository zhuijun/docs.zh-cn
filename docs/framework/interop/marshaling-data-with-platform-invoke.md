---
title: 用平台调用封送数据
description: 在 .NET 中通过平台调用封送数据。 查看 Windows API 和 C 样式函数中使用的数据类型的列表，并查找其 .NET 托管类型等效项。
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
ms.openlocfilehash: 27045790780c1eef9537bdf7e52deb579e2b467c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904099"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="9f8a1-104">用平台调用封送数据</span><span class="sxs-lookup"><span data-stu-id="9f8a1-104">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="9f8a1-105">若要调用从非托管库中导出的函数，.NET Framework 应用程序需要托管代码中表示非托管函数的函数原型。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-105">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="9f8a1-106">若要创建使平台调用能正确封送数据的原型，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9f8a1-106">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="9f8a1-107">将 <xref:System.Runtime.InteropServices.DllImportAttribute> 特性应用于托管代码中的静态函数或方法。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-107">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="9f8a1-108">用托管数据类型替换非托管数据类型。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-108">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="9f8a1-109">通过应用具有可选字段的特性以及用托管数据类型替换非托管数据类型，可用附有非托管函数的文档来构造等效的托管原型。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-109">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="9f8a1-110">有关如何应用 <xref:System.Runtime.InteropServices.DllImportAttribute> 的说明，请参阅[使用非托管 DLL 函数](consuming-unmanaged-dll-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-110">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="9f8a1-111">本节提供一些示例，演示如何创建托管函数原型，以便将参数传递到由非托管库导出的函数或接收来自这些函数的返回值。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-111">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="9f8a1-112">该示例还演示了何时使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性和 <xref:System.Runtime.InteropServices.Marshal> 类来显式封送数据。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-112">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="9f8a1-113">平台调用数据类型</span><span class="sxs-lookup"><span data-stu-id="9f8a1-113">Platform invoke data types</span></span>

<span data-ttu-id="9f8a1-114">下表列出了 Windows API 和 C 样式函数中使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-114">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="9f8a1-115">许多非托管库包含将这些数据类型作为参数和返回值传递的函数。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-115">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="9f8a1-116">第三列列出了相应的 .NET Framework 内置值类型或可在托管代码中使用的类。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-116">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="9f8a1-117">在某些情况下，你用相同大小的类型替代表中列出的类型。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-117">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="9f8a1-118">Windows API 中的非托管类型</span><span class="sxs-lookup"><span data-stu-id="9f8a1-118">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="9f8a1-119">非托管 C 语言类型</span><span class="sxs-lookup"><span data-stu-id="9f8a1-119">Unmanaged C language type</span></span>|<span data-ttu-id="9f8a1-120">托管类型</span><span class="sxs-lookup"><span data-stu-id="9f8a1-120">Managed type</span></span>|<span data-ttu-id="9f8a1-121">描述</span><span class="sxs-lookup"><span data-stu-id="9f8a1-121">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-122">应用于不返回值的函数。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-122">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="9f8a1-123"><xref:System.IntPtr?displayProperty=nameWithType> 或 <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f8a1-123"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="9f8a1-124">在 32 位 Windows 操作系统上为 32 位、在 64 位 Windows 操作系统上为 64 位。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-124">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-125">8 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-125">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-126">16 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-126">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-127">16 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-127">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-128">32 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-128">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-129">32 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-129">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-130">32 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-130">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="9f8a1-131"><xref:System.Boolean?displayProperty=nameWithType> 或 <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f8a1-131"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="9f8a1-132">32 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-132">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-133">32 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-133">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-134">32 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-134">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-135">使用 ANSI 修饰。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-135">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-136">使用 Unicode 修饰。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-136">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="9f8a1-137"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f8a1-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="9f8a1-138">使用 ANSI 修饰。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-138">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="9f8a1-139"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f8a1-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="9f8a1-140">使用 ANSI 修饰。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-140">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="9f8a1-141"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f8a1-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="9f8a1-142">使用 Unicode 修饰。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-142">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="9f8a1-143"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f8a1-143"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="9f8a1-144">使用 Unicode 修饰。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-144">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-145">32 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-145">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="9f8a1-146">64 位</span><span class="sxs-lookup"><span data-stu-id="9f8a1-146">64 bits</span></span>|

<span data-ttu-id="9f8a1-147">有关 Visual Basic、C# 和 C++ 中的相应类型，请参阅 [.NET Framework 类库简介](../../standard/class-library-overview.md#system-namespace)。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-147">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="9f8a1-148">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="9f8a1-148">PinvokeLib.dll</span></span>

<span data-ttu-id="9f8a1-149">下面的代码定义由 Pinvoke.dll 提供的库函数。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-149">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="9f8a1-150">本节中介绍的许多示例都调用此库。</span><span class="sxs-lookup"><span data-stu-id="9f8a1-150">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="9f8a1-151">示例</span><span class="sxs-lookup"><span data-stu-id="9f8a1-151">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
