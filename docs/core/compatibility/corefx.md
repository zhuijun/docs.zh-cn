---
title: 基类库的重大更改
description: 列出核心 .NET 库中的重大更改。
ms.date: 09/20/2019
ms.openlocfilehash: 45de0f0d418437cf1677c9a8c7cfc9b6c33a24ef
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144470"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="953dc-103">核心 .NET 库重大更改</span><span class="sxs-lookup"><span data-stu-id="953dc-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="953dc-104">核心 .NET 库提供了 .NET Core 使用的基元和其他常规类型。</span><span class="sxs-lookup"><span data-stu-id="953dc-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="953dc-105">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="953dc-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="953dc-106">重大更改</span><span class="sxs-lookup"><span data-stu-id="953dc-106">Breaking change</span></span> | <span data-ttu-id="953dc-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="953dc-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="953dc-108">SSE 和 SSE2 CompareGreaterThan 方法正确处理 NaN 输入</span><span class="sxs-lookup"><span data-stu-id="953dc-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="953dc-109">5.0</span><span class="sxs-lookup"><span data-stu-id="953dc-109">5.0</span></span> |
| [<span data-ttu-id="953dc-110">如果实例已存在，CounterSet.CreateCounterSetInstance 现在将引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="953dc-110">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="953dc-111">5.0</span><span class="sxs-lookup"><span data-stu-id="953dc-111">5.0</span></span> |
| [<span data-ttu-id="953dc-112">报告版本的 API 现在报告产品版本而不是文件版本</span><span class="sxs-lookup"><span data-stu-id="953dc-112">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="953dc-113">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-113">3.0</span></span> |
| [<span data-ttu-id="953dc-114">自定义 EncoderFallbackBuffer 实例无法递归回退</span><span class="sxs-lookup"><span data-stu-id="953dc-114">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="953dc-115">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-115">3.0</span></span> |
| [<span data-ttu-id="953dc-116">浮点格式设置和分析行为变更</span><span class="sxs-lookup"><span data-stu-id="953dc-116">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="953dc-117">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-117">3.0</span></span> |
| [<span data-ttu-id="953dc-118">浮点分析操作不再失败或引发 OverflowException</span><span class="sxs-lookup"><span data-stu-id="953dc-118">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="953dc-119">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-119">3.0</span></span> |
| [<span data-ttu-id="953dc-120">InvalidAsynchronousStateException 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="953dc-120">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="953dc-121">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-121">3.0</span></span> |
| [<span data-ttu-id="953dc-122">替换格式错误的 UTF-8 字节序列将遵循 Unicode 准则</span><span class="sxs-lookup"><span data-stu-id="953dc-122">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="953dc-123">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-123">3.0</span></span> |
| [<span data-ttu-id="953dc-124">TypeDescriptionProviderAttribute 已移到另一个程序集</span><span class="sxs-lookup"><span data-stu-id="953dc-124">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="953dc-125">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-125">3.0</span></span> |
| [<span data-ttu-id="953dc-126">ZipArchiveEntry 不再处理条目大小不一致的存档</span><span class="sxs-lookup"><span data-stu-id="953dc-126">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="953dc-127">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-127">3.0</span></span> |
| [<span data-ttu-id="953dc-128">JSON 序列化程序异常类型已从 JsonException 更改为 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="953dc-128">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="953dc-129">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-129">3.0</span></span> |
| [<span data-ttu-id="953dc-130">Utf8JsonWriter 中的 (string)null 语义更改</span><span class="sxs-lookup"><span data-stu-id="953dc-130">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="953dc-131">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-131">3.0</span></span> |
| [<span data-ttu-id="953dc-132">JsonEncodedText.Encode 方法具有附加的 JavaScriptEncoder 参数</span><span class="sxs-lookup"><span data-stu-id="953dc-132">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="953dc-133">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-133">3.0</span></span> |
| [<span data-ttu-id="953dc-134">已更改 JsonFactoryConverter.CreateConverter 签名</span><span class="sxs-lookup"><span data-stu-id="953dc-134">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="953dc-135">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-135">3.0</span></span> |
| [<span data-ttu-id="953dc-136">JsonElement API 更改</span><span class="sxs-lookup"><span data-stu-id="953dc-136">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="953dc-137">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-137">3.0</span></span> |
| [<span data-ttu-id="953dc-138">FieldInfo.SetValue 将对静态、仅初始化字段引发异常</span><span class="sxs-lookup"><span data-stu-id="953dc-138">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="953dc-139">3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-139">3.0</span></span> |
| [<span data-ttu-id="953dc-140">添加到内置结构类型的私有字段</span><span class="sxs-lookup"><span data-stu-id="953dc-140">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="953dc-141">2.1</span><span class="sxs-lookup"><span data-stu-id="953dc-141">2.1</span></span> |
| [<span data-ttu-id="953dc-142">UseShellExecute 默认值更改</span><span class="sxs-lookup"><span data-stu-id="953dc-142">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="953dc-143">2.1</span><span class="sxs-lookup"><span data-stu-id="953dc-143">2.1</span></span> |
| [<span data-ttu-id="953dc-144">macOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="953dc-144">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="953dc-145">2.1</span><span class="sxs-lookup"><span data-stu-id="953dc-145">2.1</span></span> |
| [<span data-ttu-id="953dc-146">FileSystemInfo.Attributes 引发的 UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="953dc-146">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="953dc-147">1.0</span><span class="sxs-lookup"><span data-stu-id="953dc-147">1.0</span></span> |
| [<span data-ttu-id="953dc-148">不支持处理损坏的进程状态异常</span><span class="sxs-lookup"><span data-stu-id="953dc-148">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="953dc-149">1.0</span><span class="sxs-lookup"><span data-stu-id="953dc-149">1.0</span></span> |
| [<span data-ttu-id="953dc-150">UriBuilder 属性不再预置前导字符</span><span class="sxs-lookup"><span data-stu-id="953dc-150">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="953dc-151">1.0</span><span class="sxs-lookup"><span data-stu-id="953dc-151">1.0</span></span> |
| [<span data-ttu-id="953dc-152">Process.StartInfo 对未启动的进程引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="953dc-152">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="953dc-153">1.0</span><span class="sxs-lookup"><span data-stu-id="953dc-153">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="953dc-154">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="953dc-154">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="953dc-155">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="953dc-155">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="953dc-156">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="953dc-156">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="953dc-157">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="953dc-157">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
