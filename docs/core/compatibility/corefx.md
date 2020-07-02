---
title: 基类库的重大更改
description: 列出核心 .NET 库中的重大更改。
ms.date: 09/20/2019
ms.openlocfilehash: 1c56358e69d0dd6e8572a41229c1b9edbcdad795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365606"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="cd0b8-103">核心 .NET 库重大更改</span><span class="sxs-lookup"><span data-stu-id="cd0b8-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="cd0b8-104">核心 .NET 库提供了 .NET Core 使用的基元和其他常规类型。</span><span class="sxs-lookup"><span data-stu-id="cd0b8-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="cd0b8-105">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="cd0b8-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="cd0b8-106">重大更改</span><span class="sxs-lookup"><span data-stu-id="cd0b8-106">Breaking change</span></span> | <span data-ttu-id="cd0b8-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="cd0b8-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="cd0b8-108">SSE 和 SSE2 CompareGreaterThan 方法正确处理 NaN 输入</span><span class="sxs-lookup"><span data-stu-id="cd0b8-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="cd0b8-109">5.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-109">5.0</span></span> |
| [<span data-ttu-id="cd0b8-110">如果实例已存在，CounterSet.CreateCounterSetInstance 现在将引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="cd0b8-110">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="cd0b8-111">5.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-111">5.0</span></span> |
| [<span data-ttu-id="cd0b8-112">Microsoft.DotNet.PlatformAbstractions 包已删除</span><span class="sxs-lookup"><span data-stu-id="cd0b8-112">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="cd0b8-113">5.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-113">5.0</span></span> |
| [<span data-ttu-id="cd0b8-114">报告版本的 API 现在报告产品版本而不是文件版本</span><span class="sxs-lookup"><span data-stu-id="cd0b8-114">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="cd0b8-115">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-115">3.0</span></span> |
| [<span data-ttu-id="cd0b8-116">自定义 EncoderFallbackBuffer 实例无法递归回退</span><span class="sxs-lookup"><span data-stu-id="cd0b8-116">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="cd0b8-117">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-117">3.0</span></span> |
| [<span data-ttu-id="cd0b8-118">浮点格式设置和分析行为变更</span><span class="sxs-lookup"><span data-stu-id="cd0b8-118">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="cd0b8-119">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-119">3.0</span></span> |
| [<span data-ttu-id="cd0b8-120">浮点分析操作不再失败或引发 OverflowException</span><span class="sxs-lookup"><span data-stu-id="cd0b8-120">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="cd0b8-121">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-121">3.0</span></span> |
| [<span data-ttu-id="cd0b8-122">InvalidAsynchronousStateException 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="cd0b8-122">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="cd0b8-123">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-123">3.0</span></span> |
| [<span data-ttu-id="cd0b8-124">替换格式错误的 UTF-8 字节序列将遵循 Unicode 准则</span><span class="sxs-lookup"><span data-stu-id="cd0b8-124">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="cd0b8-125">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-125">3.0</span></span> |
| [<span data-ttu-id="cd0b8-126">TypeDescriptionProviderAttribute 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="cd0b8-126">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="cd0b8-127">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-127">3.0</span></span> |
| [<span data-ttu-id="cd0b8-128">ZipArchiveEntry 不再处理条目大小不一致的存档</span><span class="sxs-lookup"><span data-stu-id="cd0b8-128">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="cd0b8-129">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-129">3.0</span></span> |
| [<span data-ttu-id="cd0b8-130">JSON 序列化程序异常类型已从 JsonException 更改为 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="cd0b8-130">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="cd0b8-131">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-131">3.0</span></span> |
| [<span data-ttu-id="cd0b8-132">Utf8JsonWriter 中的 (string)null 语义更改</span><span class="sxs-lookup"><span data-stu-id="cd0b8-132">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="cd0b8-133">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-133">3.0</span></span> |
| [<span data-ttu-id="cd0b8-134">JsonEncodedText.Encode 方法具有附加的 JavaScriptEncoder 参数</span><span class="sxs-lookup"><span data-stu-id="cd0b8-134">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="cd0b8-135">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-135">3.0</span></span> |
| [<span data-ttu-id="cd0b8-136">已更改 JsonFactoryConverter.CreateConverter 签名</span><span class="sxs-lookup"><span data-stu-id="cd0b8-136">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="cd0b8-137">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-137">3.0</span></span> |
| [<span data-ttu-id="cd0b8-138">JsonElement API 更改</span><span class="sxs-lookup"><span data-stu-id="cd0b8-138">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="cd0b8-139">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-139">3.0</span></span> |
| [<span data-ttu-id="cd0b8-140">FieldInfo.SetValue 将对静态、仅初始化字段引发异常</span><span class="sxs-lookup"><span data-stu-id="cd0b8-140">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="cd0b8-141">3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-141">3.0</span></span> |
| [<span data-ttu-id="cd0b8-142">添加到内置结构类型的私有字段</span><span class="sxs-lookup"><span data-stu-id="cd0b8-142">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="cd0b8-143">2.1</span><span class="sxs-lookup"><span data-stu-id="cd0b8-143">2.1</span></span> |
| [<span data-ttu-id="cd0b8-144">UseShellExecute 默认值更改</span><span class="sxs-lookup"><span data-stu-id="cd0b8-144">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="cd0b8-145">2.1</span><span class="sxs-lookup"><span data-stu-id="cd0b8-145">2.1</span></span> |
| [<span data-ttu-id="cd0b8-146">macOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="cd0b8-146">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="cd0b8-147">2.1</span><span class="sxs-lookup"><span data-stu-id="cd0b8-147">2.1</span></span> |
| [<span data-ttu-id="cd0b8-148">FileSystemInfo.Attributes 引发的 UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="cd0b8-148">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="cd0b8-149">1.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-149">1.0</span></span> |
| [<span data-ttu-id="cd0b8-150">不支持处理损坏的进程状态异常</span><span class="sxs-lookup"><span data-stu-id="cd0b8-150">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="cd0b8-151">1.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-151">1.0</span></span> |
| [<span data-ttu-id="cd0b8-152">UriBuilder 属性不再预置前导字符</span><span class="sxs-lookup"><span data-stu-id="cd0b8-152">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="cd0b8-153">1.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-153">1.0</span></span> |
| [<span data-ttu-id="cd0b8-154">Process.StartInfo 对未启动的进程引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="cd0b8-154">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="cd0b8-155">1.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-155">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="cd0b8-156">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-156">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="cd0b8-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-157">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="cd0b8-158">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd0b8-158">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="cd0b8-159">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="cd0b8-159">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
