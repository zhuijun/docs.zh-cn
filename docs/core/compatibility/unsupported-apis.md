---
title: .NET Core 上不支持的 API
titleSuffix: ''
description: 了解 .NET Framework 中始终在 .NET Core 上引发异常的 API。
ms.date: 12/23/2019
ms.openlocfilehash: 94f334d7e4b7daf407f489ba274172ced9eefa81
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414430"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="2fb97-103">始终在 .NET Core 上引发异常的 API</span><span class="sxs-lookup"><span data-stu-id="2fb97-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="2fb97-104">以下 API 将始终在所有或部分平台上的 .NET Core 中引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="2fb97-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="2fb97-105">本文按命名空间组织受影响的 API 成员。</span><span class="sxs-lookup"><span data-stu-id="2fb97-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="2fb97-106">本文是当前正在进行的工作。</span><span class="sxs-lookup"><span data-stu-id="2fb97-106">This article is a work-in-progress.</span></span> <span data-ttu-id="2fb97-107">它不是在 .NET Core 上引发异常的 API 的完整列表。</span><span class="sxs-lookup"><span data-stu-id="2fb97-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="2fb97-108">本文不包括在 .NET Core 上引发的二进制序列化的显式接口实现。</span><span class="sxs-lookup"><span data-stu-id="2fb97-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="2fb97-109">有关详细信息，请参阅 [.NET Core 中的二进制序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="2fb97-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="2fb97-110">系统</span><span class="sxs-lookup"><span data-stu-id="2fb97-110">System</span></span>

| <span data-ttu-id="2fb97-111">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-111">Member</span></span> | <span data-ttu-id="2fb97-112">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-113">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-114">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="2fb97-115">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="2fb97-116">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-117">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="2fb97-118">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="2fb97-119">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="2fb97-120">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-121">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-122">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="2fb97-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="2fb97-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="2fb97-124">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-124">Member</span></span> | <span data-ttu-id="2fb97-125">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-126">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-127">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-128">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="2fb97-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="2fb97-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="2fb97-130">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-130">Member</span></span> | <span data-ttu-id="2fb97-131">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-132">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-133">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-134">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="2fb97-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="2fb97-135">System.Configuration</span></span>

| <span data-ttu-id="2fb97-136">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-136">Member</span></span> | <span data-ttu-id="2fb97-137">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2fb97-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>（所有成员）</span><span class="sxs-lookup"><span data-stu-id="2fb97-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="2fb97-139">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="2fb97-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="2fb97-140">System.Console</span></span>

| <span data-ttu-id="2fb97-141">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-141">Member</span></span> | <span data-ttu-id="2fb97-142">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="2fb97-143">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-143">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-145">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-145">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-147">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-147">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-149">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-149">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>（仅获取）</span><span class="sxs-lookup"><span data-stu-id="2fb97-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2fb97-151">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-152">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-153">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-154">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-154">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-155"><xref:System.Console.Title?displayProperty=nameWithType>（仅获取）</span><span class="sxs-lookup"><span data-stu-id="2fb97-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2fb97-156">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-156">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-158">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-158">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-160">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-160">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-162">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-162">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-164">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="2fb97-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="2fb97-165">System.Data.Common</span></span>

| <span data-ttu-id="2fb97-166">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-166">Member</span></span> | <span data-ttu-id="2fb97-167">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2fb97-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>（引发 <xref:System.NotSupportedException>）</span><span class="sxs-lookup"><span data-stu-id="2fb97-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="2fb97-169">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="2fb97-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="2fb97-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="2fb97-171">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-171">Member</span></span> | <span data-ttu-id="2fb97-172">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2fb97-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-174">Linux</span><span class="sxs-lookup"><span data-stu-id="2fb97-174">Linux</span></span> |
| <span data-ttu-id="2fb97-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-176">Linux</span><span class="sxs-lookup"><span data-stu-id="2fb97-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="2fb97-177">macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="2fb97-178">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-179">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="2fb97-180">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="2fb97-181">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="2fb97-182">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="2fb97-183">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-183">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-185">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-185">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>（仅获取）</span><span class="sxs-lookup"><span data-stu-id="2fb97-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2fb97-187">macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-187">macOS</span></span> |
| <span data-ttu-id="2fb97-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-189">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="2fb97-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="2fb97-190">System.IO</span></span>

| <span data-ttu-id="2fb97-191">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-191">Member</span></span> | <span data-ttu-id="2fb97-192">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-193">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-194">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="2fb97-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="2fb97-195">System.IO.Pipes</span></span>

| <span data-ttu-id="2fb97-196">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-196">Member</span></span> | <span data-ttu-id="2fb97-197">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="2fb97-198">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="2fb97-199">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="2fb97-200">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="2fb97-201">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-201">Linux and macOS</span></span> |
| <span data-ttu-id="2fb97-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-203">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="2fb97-204">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="2fb97-205">System.Media</span><span class="sxs-lookup"><span data-stu-id="2fb97-205">System.Media</span></span>

| <span data-ttu-id="2fb97-206">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-206">Member</span></span> | <span data-ttu-id="2fb97-207">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-208">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="2fb97-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="2fb97-209">System.Net</span></span>

| <span data-ttu-id="2fb97-210">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-210">Member</span></span> | <span data-ttu-id="2fb97-211">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-212">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-213">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-214">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-215">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-216">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-217">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-218">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-219">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-220">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-221">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-222">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="2fb97-223">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-224">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-225">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-226">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-227">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-228">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="2fb97-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="2fb97-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="2fb97-230">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-230">Member</span></span> | <span data-ttu-id="2fb97-231">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="2fb97-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="2fb97-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="2fb97-233">System.Net.Sockets</span></span>

| <span data-ttu-id="2fb97-234">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-234">Member</span></span> | <span data-ttu-id="2fb97-235">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="2fb97-236">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-237">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="2fb97-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="2fb97-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="2fb97-239">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-239">Member</span></span> | <span data-ttu-id="2fb97-240">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="2fb97-241">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="2fb97-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="2fb97-242">System.Reflection</span></span>

| <span data-ttu-id="2fb97-243">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-243">Member</span></span> | <span data-ttu-id="2fb97-244">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-245">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-246">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-247">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-248">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="2fb97-249">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-250">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="2fb97-251">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="2fb97-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="2fb97-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="2fb97-253">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-253">Member</span></span> | <span data-ttu-id="2fb97-254">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="2fb97-255">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="2fb97-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="2fb97-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="2fb97-257">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-257">Member</span></span> | <span data-ttu-id="2fb97-258">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-259">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="2fb97-260">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-261">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-262">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-263">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-264">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-265">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="2fb97-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="2fb97-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="2fb97-267">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-267">Member</span></span> | <span data-ttu-id="2fb97-268">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="2fb97-269">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="2fb97-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="2fb97-270">System.Security</span></span>

| <span data-ttu-id="2fb97-271">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-271">Member</span></span> | <span data-ttu-id="2fb97-272">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="2fb97-273">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="2fb97-274">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-275">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="2fb97-276">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="2fb97-277">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="2fb97-278">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="2fb97-279">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="2fb97-280">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="2fb97-281">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="2fb97-282">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="2fb97-283">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-284">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="2fb97-285">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="2fb97-286">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="2fb97-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="2fb97-287">System.Security.Claims</span></span>

| <span data-ttu-id="2fb97-288">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-288">Member</span></span> | <span data-ttu-id="2fb97-289">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="2fb97-290">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-291">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="2fb97-292">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-293">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-294">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="2fb97-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="2fb97-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="2fb97-296">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-296">Member</span></span> | <span data-ttu-id="2fb97-297">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-298">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="2fb97-299">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="2fb97-300">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="2fb97-301">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="2fb97-302">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="2fb97-303">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="2fb97-304">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="2fb97-305">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="2fb97-306">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="2fb97-307">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="2fb97-308">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="2fb97-309">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="2fb97-310">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="2fb97-311">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2fb97-312">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="2fb97-313">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-314">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-315">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-316">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-317">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2fb97-318">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-319">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-320">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-321">Linux 和 macOS</span><span class="sxs-lookup"><span data-stu-id="2fb97-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-322">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-323">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2fb97-324">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-325">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="2fb97-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="2fb97-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="2fb97-327">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-327">Member</span></span> | <span data-ttu-id="2fb97-328">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="2fb97-329">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="2fb97-330">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="2fb97-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="2fb97-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="2fb97-332">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-332">Member</span></span> | <span data-ttu-id="2fb97-333">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-334">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-335">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-336">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-336">All</span></span> |
| <span data-ttu-id="2fb97-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>（仅设置）</span><span class="sxs-lookup"><span data-stu-id="2fb97-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2fb97-338">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="2fb97-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="2fb97-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="2fb97-340">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-340">Member</span></span> | <span data-ttu-id="2fb97-341">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-342">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="2fb97-343">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="2fb97-343">System.Security.Policy</span></span>

| <span data-ttu-id="2fb97-344">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-344">Member</span></span> | <span data-ttu-id="2fb97-345">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-346">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="2fb97-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="2fb97-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="2fb97-348">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-348">Member</span></span> | <span data-ttu-id="2fb97-349">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2fb97-350">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="2fb97-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="2fb97-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="2fb97-352">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-352">Member</span></span> | <span data-ttu-id="2fb97-353">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-354">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="2fb97-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="2fb97-355">System.Threading</span></span>

| <span data-ttu-id="2fb97-356">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-356">Member</span></span> | <span data-ttu-id="2fb97-357">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-358">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-359">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="2fb97-360">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="2fb97-361">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="2fb97-362">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="2fb97-363">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="2fb97-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="2fb97-364">System.Xml</span></span>

| <span data-ttu-id="2fb97-365">成员</span><span class="sxs-lookup"><span data-stu-id="2fb97-365">Member</span></span> | <span data-ttu-id="2fb97-366">引发异常的平台</span><span class="sxs-lookup"><span data-stu-id="2fb97-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-367">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-368">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2fb97-369">All</span><span class="sxs-lookup"><span data-stu-id="2fb97-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="2fb97-370">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fb97-370">See also</span></span>

- [<span data-ttu-id="2fb97-371">从 .NET Framework 迁移到 .NET Core 的中断性变更</span><span class="sxs-lookup"><span data-stu-id="2fb97-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="2fb97-372">.NET Core 中的二进制序列化</span><span class="sxs-lookup"><span data-stu-id="2fb97-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="2fb97-373">.NET 可移植性分析器</span><span class="sxs-lookup"><span data-stu-id="2fb97-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
