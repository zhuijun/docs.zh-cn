---
title: 基类库的重大更改
description: 列出核心 .NET 库中的重大更改。
ms.date: 09/20/2019
ms.openlocfilehash: 64510809a1cf69ea0e4c4816eb2df54233e8eceb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281289"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="55fc2-103">核心 .NET 库重大更改</span><span class="sxs-lookup"><span data-stu-id="55fc2-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="55fc2-104">核心 .NET 库提供了 .NET Core 使用的基元和其他常规类型。</span><span class="sxs-lookup"><span data-stu-id="55fc2-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="55fc2-105">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="55fc2-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="55fc2-106">重大更改</span><span class="sxs-lookup"><span data-stu-id="55fc2-106">Breaking change</span></span> | <span data-ttu-id="55fc2-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="55fc2-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="55fc2-108">默认 ActivityIdFormat 为 W3C</span><span class="sxs-lookup"><span data-stu-id="55fc2-108">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="55fc2-109">5.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-109">5.0</span></span> |
| [<span data-ttu-id="55fc2-110">Vector2.Lerp 和 Vector4.Lerp 的行为变更</span><span class="sxs-lookup"><span data-stu-id="55fc2-110">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="55fc2-111">5.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-111">5.0</span></span> |
| [<span data-ttu-id="55fc2-112">SSE 和 SSE2 CompareGreaterThan 方法正确处理 NaN 输入</span><span class="sxs-lookup"><span data-stu-id="55fc2-112">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="55fc2-113">5.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-113">5.0</span></span> |
| [<span data-ttu-id="55fc2-114">如果实例已存在，CounterSet.CreateCounterSetInstance 现在将引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="55fc2-114">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="55fc2-115">5.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-115">5.0</span></span> |
| [<span data-ttu-id="55fc2-116">Microsoft.DotNet.PlatformAbstractions 包已删除</span><span class="sxs-lookup"><span data-stu-id="55fc2-116">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="55fc2-117">5.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-117">5.0</span></span> |
| [<span data-ttu-id="55fc2-118">报告版本的 API 现在报告产品版本而不是文件版本</span><span class="sxs-lookup"><span data-stu-id="55fc2-118">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="55fc2-119">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-119">3.0</span></span> |
| [<span data-ttu-id="55fc2-120">自定义 EncoderFallbackBuffer 实例无法递归回退</span><span class="sxs-lookup"><span data-stu-id="55fc2-120">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="55fc2-121">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-121">3.0</span></span> |
| [<span data-ttu-id="55fc2-122">浮点格式设置和分析行为变更</span><span class="sxs-lookup"><span data-stu-id="55fc2-122">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="55fc2-123">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-123">3.0</span></span> |
| [<span data-ttu-id="55fc2-124">浮点分析操作不再失败或引发 OverflowException</span><span class="sxs-lookup"><span data-stu-id="55fc2-124">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="55fc2-125">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-125">3.0</span></span> |
| [<span data-ttu-id="55fc2-126">InvalidAsynchronousStateException 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="55fc2-126">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="55fc2-127">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-127">3.0</span></span> |
| [<span data-ttu-id="55fc2-128">替换格式错误的 UTF-8 字节序列将遵循 Unicode 准则</span><span class="sxs-lookup"><span data-stu-id="55fc2-128">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="55fc2-129">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-129">3.0</span></span> |
| [<span data-ttu-id="55fc2-130">TypeDescriptionProviderAttribute 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="55fc2-130">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="55fc2-131">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-131">3.0</span></span> |
| [<span data-ttu-id="55fc2-132">ZipArchiveEntry 不再处理条目大小不一致的存档</span><span class="sxs-lookup"><span data-stu-id="55fc2-132">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="55fc2-133">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-133">3.0</span></span> |
| [<span data-ttu-id="55fc2-134">JSON 序列化程序异常类型已从 JsonException 更改为 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="55fc2-134">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="55fc2-135">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-135">3.0</span></span> |
| [<span data-ttu-id="55fc2-136">Utf8JsonWriter 中的 (string)null 语义更改</span><span class="sxs-lookup"><span data-stu-id="55fc2-136">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="55fc2-137">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-137">3.0</span></span> |
| [<span data-ttu-id="55fc2-138">JsonEncodedText.Encode 方法具有附加的 JavaScriptEncoder 参数</span><span class="sxs-lookup"><span data-stu-id="55fc2-138">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="55fc2-139">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-139">3.0</span></span> |
| [<span data-ttu-id="55fc2-140">已更改 JsonFactoryConverter.CreateConverter 签名</span><span class="sxs-lookup"><span data-stu-id="55fc2-140">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="55fc2-141">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-141">3.0</span></span> |
| [<span data-ttu-id="55fc2-142">JsonElement API 更改</span><span class="sxs-lookup"><span data-stu-id="55fc2-142">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="55fc2-143">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-143">3.0</span></span> |
| [<span data-ttu-id="55fc2-144">FieldInfo.SetValue 将对静态、仅初始化字段引发异常</span><span class="sxs-lookup"><span data-stu-id="55fc2-144">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="55fc2-145">3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-145">3.0</span></span> |
| [<span data-ttu-id="55fc2-146">添加到内置结构类型的私有字段</span><span class="sxs-lookup"><span data-stu-id="55fc2-146">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="55fc2-147">2.1</span><span class="sxs-lookup"><span data-stu-id="55fc2-147">2.1</span></span> |
| [<span data-ttu-id="55fc2-148">UseShellExecute 默认值更改</span><span class="sxs-lookup"><span data-stu-id="55fc2-148">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="55fc2-149">2.1</span><span class="sxs-lookup"><span data-stu-id="55fc2-149">2.1</span></span> |
| [<span data-ttu-id="55fc2-150">macOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="55fc2-150">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="55fc2-151">2.1</span><span class="sxs-lookup"><span data-stu-id="55fc2-151">2.1</span></span> |
| [<span data-ttu-id="55fc2-152">FileSystemInfo.Attributes 引发的 UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="55fc2-152">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="55fc2-153">1.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-153">1.0</span></span> |
| [<span data-ttu-id="55fc2-154">不支持处理损坏的进程状态异常</span><span class="sxs-lookup"><span data-stu-id="55fc2-154">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="55fc2-155">1.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-155">1.0</span></span> |
| [<span data-ttu-id="55fc2-156">UriBuilder 属性不再预置前导字符</span><span class="sxs-lookup"><span data-stu-id="55fc2-156">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="55fc2-157">1.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-157">1.0</span></span> |
| [<span data-ttu-id="55fc2-158">Process.StartInfo 对未启动的进程引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="55fc2-158">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="55fc2-159">1.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-159">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="55fc2-160">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-160">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="55fc2-161">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-161">.NET Core 3.0</span></span>

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

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

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

## <a name="net-core-21"></a><span data-ttu-id="55fc2-162">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="55fc2-162">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="55fc2-163">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="55fc2-163">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
