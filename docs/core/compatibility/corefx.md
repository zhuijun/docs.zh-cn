---
title: 基类库的重大更改
description: 列出核心 .NET 库中的重大更改。
ms.date: 07/27/2020
ms.openlocfilehash: 558aa1d76831cd15e2028c17d2b0b2e82f64ef9a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517317"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="e9c32-103">核心 .NET 库重大更改</span><span class="sxs-lookup"><span data-stu-id="e9c32-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="e9c32-104">核心 .NET 库提供了 .NET Core 使用的基元和其他常规类型。</span><span class="sxs-lookup"><span data-stu-id="e9c32-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="e9c32-105">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="e9c32-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e9c32-106">重大更改</span><span class="sxs-lookup"><span data-stu-id="e9c32-106">Breaking change</span></span> | <span data-ttu-id="e9c32-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e9c32-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="e9c32-108">BinaryFormatter 序列化方法已过时，并且已在 ASP.NET 应用中禁用</span><span class="sxs-lookup"><span data-stu-id="e9c32-108">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="e9c32-109">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-109">5.0</span></span> |
| [<span data-ttu-id="e9c32-110">UTF-7 代码路径已过时</span><span class="sxs-lookup"><span data-stu-id="e9c32-110">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="e9c32-111">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-111">5.0</span></span> |
| [<span data-ttu-id="e9c32-112">对于不支持的类型，Vector\<T> 始终引发 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="e9c32-112">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="e9c32-113">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-113">5.0</span></span> |
| [<span data-ttu-id="e9c32-114">默认 ActivityIdFormat 为 W3C</span><span class="sxs-lookup"><span data-stu-id="e9c32-114">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="e9c32-115">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-115">5.0</span></span> |
| [<span data-ttu-id="e9c32-116">Vector2.Lerp 和 Vector4.Lerp 的行为变更</span><span class="sxs-lookup"><span data-stu-id="e9c32-116">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="e9c32-117">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-117">5.0</span></span> |
| [<span data-ttu-id="e9c32-118">SSE 和 SSE2 CompareGreaterThan 方法正确处理 NaN 输入</span><span class="sxs-lookup"><span data-stu-id="e9c32-118">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="e9c32-119">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-119">5.0</span></span> |
| [<span data-ttu-id="e9c32-120">如果实例已存在，CounterSet.CreateCounterSetInstance 现在将引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="e9c32-120">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="e9c32-121">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-121">5.0</span></span> |
| [<span data-ttu-id="e9c32-122">Microsoft.DotNet.PlatformAbstractions 包已删除</span><span class="sxs-lookup"><span data-stu-id="e9c32-122">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="e9c32-123">5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-123">5.0</span></span> |
| [<span data-ttu-id="e9c32-124">报告版本的 API 现在报告产品版本而不是文件版本</span><span class="sxs-lookup"><span data-stu-id="e9c32-124">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="e9c32-125">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-125">3.0</span></span> |
| [<span data-ttu-id="e9c32-126">自定义 EncoderFallbackBuffer 实例无法递归回退</span><span class="sxs-lookup"><span data-stu-id="e9c32-126">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="e9c32-127">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-127">3.0</span></span> |
| [<span data-ttu-id="e9c32-128">浮点格式设置和分析行为变更</span><span class="sxs-lookup"><span data-stu-id="e9c32-128">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="e9c32-129">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-129">3.0</span></span> |
| [<span data-ttu-id="e9c32-130">浮点分析操作不再失败或引发 OverflowException</span><span class="sxs-lookup"><span data-stu-id="e9c32-130">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="e9c32-131">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-131">3.0</span></span> |
| [<span data-ttu-id="e9c32-132">InvalidAsynchronousStateException 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="e9c32-132">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="e9c32-133">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-133">3.0</span></span> |
| [<span data-ttu-id="e9c32-134">替换格式错误的 UTF-8 字节序列将遵循 Unicode 准则</span><span class="sxs-lookup"><span data-stu-id="e9c32-134">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="e9c32-135">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-135">3.0</span></span> |
| [<span data-ttu-id="e9c32-136">TypeDescriptionProviderAttribute 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="e9c32-136">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="e9c32-137">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-137">3.0</span></span> |
| [<span data-ttu-id="e9c32-138">ZipArchiveEntry 不再处理条目大小不一致的存档</span><span class="sxs-lookup"><span data-stu-id="e9c32-138">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="e9c32-139">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-139">3.0</span></span> |
| [<span data-ttu-id="e9c32-140">Utf8JsonWriter 中的 (string)null 语义更改</span><span class="sxs-lookup"><span data-stu-id="e9c32-140">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="e9c32-141">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-141">3.0</span></span> |
| [<span data-ttu-id="e9c32-142">JsonEncodedText.Encode 方法具有附加的 JavaScriptEncoder 参数</span><span class="sxs-lookup"><span data-stu-id="e9c32-142">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="e9c32-143">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-143">3.0</span></span> |
| [<span data-ttu-id="e9c32-144">已更改 JsonFactoryConverter.CreateConverter 签名</span><span class="sxs-lookup"><span data-stu-id="e9c32-144">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="e9c32-145">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-145">3.0</span></span> |
| [<span data-ttu-id="e9c32-146">JsonElement API 更改</span><span class="sxs-lookup"><span data-stu-id="e9c32-146">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="e9c32-147">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-147">3.0</span></span> |
| [<span data-ttu-id="e9c32-148">FieldInfo.SetValue 将对静态、仅初始化字段引发异常</span><span class="sxs-lookup"><span data-stu-id="e9c32-148">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="e9c32-149">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-149">3.0</span></span> |
| [<span data-ttu-id="e9c32-150">添加到内置结构类型的私有字段</span><span class="sxs-lookup"><span data-stu-id="e9c32-150">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="e9c32-151">2.1</span><span class="sxs-lookup"><span data-stu-id="e9c32-151">2.1</span></span> |
| [<span data-ttu-id="e9c32-152">UseShellExecute 默认值更改</span><span class="sxs-lookup"><span data-stu-id="e9c32-152">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="e9c32-153">2.1</span><span class="sxs-lookup"><span data-stu-id="e9c32-153">2.1</span></span> |
| [<span data-ttu-id="e9c32-154">macOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="e9c32-154">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="e9c32-155">2.1</span><span class="sxs-lookup"><span data-stu-id="e9c32-155">2.1</span></span> |
| [<span data-ttu-id="e9c32-156">FileSystemInfo.Attributes 引发的 UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="e9c32-156">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="e9c32-157">1.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-157">1.0</span></span> |
| [<span data-ttu-id="e9c32-158">不支持处理损坏的进程状态异常</span><span class="sxs-lookup"><span data-stu-id="e9c32-158">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="e9c32-159">1.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-159">1.0</span></span> |
| [<span data-ttu-id="e9c32-160">UriBuilder 属性不再预置前导字符</span><span class="sxs-lookup"><span data-stu-id="e9c32-160">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="e9c32-161">1.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-161">1.0</span></span> |
| [<span data-ttu-id="e9c32-162">Process.StartInfo 对未启动的进程引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="e9c32-162">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="e9c32-163">1.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-163">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="e9c32-164">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-164">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="e9c32-165">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-165">.NET Core 3.0</span></span>

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

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="e9c32-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e9c32-166">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="e9c32-167">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="e9c32-167">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
