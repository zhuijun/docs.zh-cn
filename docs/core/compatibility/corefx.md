---
title: 基类库的重大更改
description: 列出核心 .NET 库中的重大更改。
ms.date: 07/27/2020
ms.openlocfilehash: c73909514bc738387a21f5ea68defe49c6a2c839
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598167"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="b4ae6-103">核心 .NET 库重大更改</span><span class="sxs-lookup"><span data-stu-id="b4ae6-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="b4ae6-104">核心 .NET 库提供了 .NET Core 使用的基元和其他常规类型。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="b4ae6-105">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="b4ae6-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b4ae6-106">重大更改</span><span class="sxs-lookup"><span data-stu-id="b4ae6-106">Breaking change</span></span> | <span data-ttu-id="b4ae6-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="b4ae6-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="b4ae6-108">Thread.Abort 已过时</span><span class="sxs-lookup"><span data-stu-id="b4ae6-108">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="b4ae6-109">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-109">5.0</span></span> |
| [<span data-ttu-id="b4ae6-110">ConsoleLoggerOptions 上已过时的属性</span><span class="sxs-lookup"><span data-stu-id="b4ae6-110">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="b4ae6-111">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-111">5.0</span></span> |
| [<span data-ttu-id="b4ae6-112">嵌套类型的硬件内部 IsSupported 检查可能有所不同</span><span class="sxs-lookup"><span data-stu-id="b4ae6-112">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="b4ae6-113">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-113">5.0</span></span> |
| [<span data-ttu-id="b4ae6-114">引用程序集中的参数名称已更改</span><span class="sxs-lookup"><span data-stu-id="b4ae6-114">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="b4ae6-115">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-115">5.0</span></span> |
| [<span data-ttu-id="b4ae6-116">在 Unix 上正确分析包含非 ASCII 字符的 URI 路径</span><span class="sxs-lookup"><span data-stu-id="b4ae6-116">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="b4ae6-117">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-117">5.0</span></span> |
| [<span data-ttu-id="b4ae6-118">Unix 上 UNC 路径的 URI 识别</span><span class="sxs-lookup"><span data-stu-id="b4ae6-118">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="b4ae6-119">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-119">5.0</span></span> |
| [<span data-ttu-id="b4ae6-120">Environment.OSVersion 返回正确的操作系统版本</span><span class="sxs-lookup"><span data-stu-id="b4ae6-120">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="b4ae6-121">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-121">5.0</span></span> |
| [<span data-ttu-id="b4ae6-122">增加了 LINQ OrderBy.First{OrDefault} 的复杂度</span><span class="sxs-lookup"><span data-stu-id="b4ae6-122">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="b4ae6-123">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-123">5.0</span></span> |
| [<span data-ttu-id="b4ae6-124">IntPtr 和 UIntPtr 实现 IFormattable</span><span class="sxs-lookup"><span data-stu-id="b4ae6-124">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="b4ae6-125">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-125">5.0</span></span> |
| [<span data-ttu-id="b4ae6-126">PrincipalPermissionAttribute 已过时，报告为错误</span><span class="sxs-lookup"><span data-stu-id="b4ae6-126">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="b4ae6-127">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-127">5.0</span></span> |
| [<span data-ttu-id="b4ae6-128">BinaryFormatter 序列化方法已过时，并且已在 ASP.NET 应用中禁用</span><span class="sxs-lookup"><span data-stu-id="b4ae6-128">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="b4ae6-129">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-129">5.0</span></span> |
| [<span data-ttu-id="b4ae6-130">UTF-7 代码路径已过时</span><span class="sxs-lookup"><span data-stu-id="b4ae6-130">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="b4ae6-131">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-131">5.0</span></span> |
| [<span data-ttu-id="b4ae6-132">对于不支持的类型，Vector\<T> 始终引发 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="b4ae6-132">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="b4ae6-133">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-133">5.0</span></span> |
| [<span data-ttu-id="b4ae6-134">默认 ActivityIdFormat 为 W3C</span><span class="sxs-lookup"><span data-stu-id="b4ae6-134">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="b4ae6-135">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-135">5.0</span></span> |
| [<span data-ttu-id="b4ae6-136">Vector2.Lerp 和 Vector4.Lerp 的行为变更</span><span class="sxs-lookup"><span data-stu-id="b4ae6-136">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="b4ae6-137">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-137">5.0</span></span> |
| [<span data-ttu-id="b4ae6-138">SSE 和 SSE2 CompareGreaterThan 方法正确处理 NaN 输入</span><span class="sxs-lookup"><span data-stu-id="b4ae6-138">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="b4ae6-139">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-139">5.0</span></span> |
| [<span data-ttu-id="b4ae6-140">如果实例已存在，CounterSet.CreateCounterSetInstance 现在将引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="b4ae6-140">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="b4ae6-141">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-141">5.0</span></span> |
| [<span data-ttu-id="b4ae6-142">Microsoft.DotNet.PlatformAbstractions 包已删除</span><span class="sxs-lookup"><span data-stu-id="b4ae6-142">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="b4ae6-143">5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-143">5.0</span></span> |
| [<span data-ttu-id="b4ae6-144">报告版本的 API 现在报告产品版本而不是文件版本</span><span class="sxs-lookup"><span data-stu-id="b4ae6-144">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="b4ae6-145">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-145">3.0</span></span> |
| [<span data-ttu-id="b4ae6-146">自定义 EncoderFallbackBuffer 实例无法递归回退</span><span class="sxs-lookup"><span data-stu-id="b4ae6-146">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="b4ae6-147">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-147">3.0</span></span> |
| [<span data-ttu-id="b4ae6-148">浮点格式设置和分析行为变更</span><span class="sxs-lookup"><span data-stu-id="b4ae6-148">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="b4ae6-149">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-149">3.0</span></span> |
| [<span data-ttu-id="b4ae6-150">浮点分析操作不再失败或引发 OverflowException</span><span class="sxs-lookup"><span data-stu-id="b4ae6-150">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="b4ae6-151">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-151">3.0</span></span> |
| [<span data-ttu-id="b4ae6-152">InvalidAsynchronousStateException 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="b4ae6-152">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="b4ae6-153">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-153">3.0</span></span> |
| [<span data-ttu-id="b4ae6-154">替换格式错误的 UTF-8 字节序列将遵循 Unicode 准则</span><span class="sxs-lookup"><span data-stu-id="b4ae6-154">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="b4ae6-155">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-155">3.0</span></span> |
| [<span data-ttu-id="b4ae6-156">TypeDescriptionProviderAttribute 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="b4ae6-156">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="b4ae6-157">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-157">3.0</span></span> |
| [<span data-ttu-id="b4ae6-158">ZipArchiveEntry 不再处理条目大小不一致的存档</span><span class="sxs-lookup"><span data-stu-id="b4ae6-158">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="b4ae6-159">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-159">3.0</span></span> |
| [<span data-ttu-id="b4ae6-160">FieldInfo.SetValue 将对静态、仅初始化字段引发异常</span><span class="sxs-lookup"><span data-stu-id="b4ae6-160">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="b4ae6-161">3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-161">3.0</span></span> |
| [<span data-ttu-id="b4ae6-162">添加到内置结构类型的私有字段</span><span class="sxs-lookup"><span data-stu-id="b4ae6-162">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="b4ae6-163">2.1</span><span class="sxs-lookup"><span data-stu-id="b4ae6-163">2.1</span></span> |
| [<span data-ttu-id="b4ae6-164">UseShellExecute 默认值更改</span><span class="sxs-lookup"><span data-stu-id="b4ae6-164">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="b4ae6-165">2.1</span><span class="sxs-lookup"><span data-stu-id="b4ae6-165">2.1</span></span> |
| [<span data-ttu-id="b4ae6-166">macOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="b4ae6-166">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="b4ae6-167">2.1</span><span class="sxs-lookup"><span data-stu-id="b4ae6-167">2.1</span></span> |
| [<span data-ttu-id="b4ae6-168">FileSystemInfo.Attributes 引发的 UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="b4ae6-168">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="b4ae6-169">1.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-169">1.0</span></span> |
| [<span data-ttu-id="b4ae6-170">不支持处理损坏的进程状态异常</span><span class="sxs-lookup"><span data-stu-id="b4ae6-170">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="b4ae6-171">1.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-171">1.0</span></span> |
| [<span data-ttu-id="b4ae6-172">UriBuilder 属性不再预置前导字符</span><span class="sxs-lookup"><span data-stu-id="b4ae6-172">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="b4ae6-173">1.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-173">1.0</span></span> |
| [<span data-ttu-id="b4ae6-174">Process.StartInfo 对未启动的进程引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="b4ae6-174">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="b4ae6-175">1.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-175">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="b4ae6-176">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-176">.NET 5.0</span></span>

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

***

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

***

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

***

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

***

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

***

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

***

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

***

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

***

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="b4ae6-177">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-177">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="b4ae6-178">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b4ae6-178">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="b4ae6-179">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-179">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
