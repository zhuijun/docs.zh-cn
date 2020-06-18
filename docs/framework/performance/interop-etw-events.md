---
title: 互操作 ETW 事件
description: 查看互操作 ETW （Windows 事件跟踪）事件，这些事件在 .NET 中捕获有关 Microsoft 中间语言（MSIL）存根生成 & 缓存的信息。
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
ms.openlocfilehash: 9dac9bc70cd070eb3e94969ce47ce24325a6f89d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904242"
---
# <a name="interop-etw-events"></a><span data-ttu-id="5dc3c-103">互操作 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5dc3c-103">Interop ETW Events</span></span>
<span data-ttu-id="5dc3c-104">互操作事件捕获有关 Microsoft 中间语言 (MSIL) 存根生成和缓存的信息。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-104">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  

## <a name="ilstubgenerated-event"></a><span data-ttu-id="5dc3c-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="5dc3c-105">ILStubGenerated Event</span></span>

<span data-ttu-id="5dc3c-106">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="5dc3c-107">（有关详细信息，请参阅 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)。）</span><span class="sxs-lookup"><span data-stu-id="5dc3c-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5dc3c-108">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="5dc3c-108">Keyword for raising the event</span></span>|<span data-ttu-id="5dc3c-109">级别</span><span class="sxs-lookup"><span data-stu-id="5dc3c-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5dc3c-110">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="5dc3c-110">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="5dc3c-111">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="5dc3c-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="5dc3c-112">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5dc3c-113">事件</span><span class="sxs-lookup"><span data-stu-id="5dc3c-113">Event</span></span>|<span data-ttu-id="5dc3c-114">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-114">Event ID</span></span>|<span data-ttu-id="5dc3c-115">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="5dc3c-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="5dc3c-116">88</span><span class="sxs-lookup"><span data-stu-id="5dc3c-116">88</span></span>|<span data-ttu-id="5dc3c-117">已生成 MSIL 存根。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-117">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="5dc3c-118">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-118">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5dc3c-119">字段名称</span><span class="sxs-lookup"><span data-stu-id="5dc3c-119">Field name</span></span>|<span data-ttu-id="5dc3c-120">数据类型</span><span class="sxs-lookup"><span data-stu-id="5dc3c-120">Data type</span></span>|<span data-ttu-id="5dc3c-121">说明</span><span class="sxs-lookup"><span data-stu-id="5dc3c-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5dc3c-122">ModuleID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-122">ModuleID</span></span>|<span data-ttu-id="5dc3c-123">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5dc3c-123">win:UInt16</span></span>|<span data-ttu-id="5dc3c-124">模块标识符。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-124">The module identifier.</span></span>|  
|<span data-ttu-id="5dc3c-125">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-125">StubMethodID</span></span>|<span data-ttu-id="5dc3c-126">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5dc3c-126">win:UInt64</span></span>|<span data-ttu-id="5dc3c-127">存根方法标识符。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-127">The stub method identifier.</span></span>|  
|<span data-ttu-id="5dc3c-128">StubFlags</span><span class="sxs-lookup"><span data-stu-id="5dc3c-128">StubFlags</span></span>|<span data-ttu-id="5dc3c-129">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5dc3c-129">win:UInt64</span></span>|<span data-ttu-id="5dc3c-130">存根标志：</span><span class="sxs-lookup"><span data-stu-id="5dc3c-130">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="5dc3c-131">0x1 - 反向互操作。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-131">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="5dc3c-132">0x2 - COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-132">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="5dc3c-133">0x4 - 由 NGen.exe 生成的存根。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-133">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="5dc3c-134">0x8 - 委托。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-134">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="5dc3c-135">0x10-可变参数。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-135">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="5dc3c-136">0x20 - 非托管被调用方。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-136">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="5dc3c-137">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="5dc3c-137">ManagedInteropMethodToken</span></span>|<span data-ttu-id="5dc3c-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5dc3c-138">win:UInt32</span></span>|<span data-ttu-id="5dc3c-139">托管互操作方法的标记。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-139">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-140">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="5dc3c-140">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="5dc3c-141">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-141">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-142">托管互操作方法的命名空间。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-142">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-143">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="5dc3c-143">ManagedInteropMethodName</span></span>|<span data-ttu-id="5dc3c-144">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-144">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-145">托管互操作方法的名称。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-145">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-146">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="5dc3c-146">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="5dc3c-147">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-147">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-148">托管互操作方法的签名。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-148">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-149">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="5dc3c-149">NativeMethodSignature</span></span>|<span data-ttu-id="5dc3c-150">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-150">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-151">本机方法签名。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-151">The native method signature.</span></span>|  
|<span data-ttu-id="5dc3c-152">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="5dc3c-152">StubMethodSignature</span></span>|<span data-ttu-id="5dc3c-153">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-153">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-154">存根方法签名。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-154">The stub method signature.</span></span>|  
|<span data-ttu-id="5dc3c-155">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="5dc3c-155">StubMethodILCode</span></span>|<span data-ttu-id="5dc3c-156">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-156">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-157">存根方法的 MSIL 代码。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-157">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="5dc3c-158">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-158">ClrInstanceID</span></span>|<span data-ttu-id="5dc3c-159">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5dc3c-159">win:UInt16</span></span>|<span data-ttu-id="5dc3c-160">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-160">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="ilstubcachehit-event"></a><span data-ttu-id="5dc3c-161">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="5dc3c-161">ILStubCacheHit Event</span></span>  

<span data-ttu-id="5dc3c-162">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-162">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="5dc3c-163">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="5dc3c-163">Keyword for raising the event</span></span>|<span data-ttu-id="5dc3c-164">级别</span><span class="sxs-lookup"><span data-stu-id="5dc3c-164">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5dc3c-165">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="5dc3c-165">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="5dc3c-166">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="5dc3c-166">Informational(4)</span></span>|  
  
 <span data-ttu-id="5dc3c-167">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-167">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5dc3c-168">事件</span><span class="sxs-lookup"><span data-stu-id="5dc3c-168">Event</span></span>|<span data-ttu-id="5dc3c-169">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-169">Event ID</span></span>|<span data-ttu-id="5dc3c-170">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="5dc3c-170">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="5dc3c-171">89</span><span class="sxs-lookup"><span data-stu-id="5dc3c-171">89</span></span>|<span data-ttu-id="5dc3c-172">已访问 MSIL 缓存。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-172">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="5dc3c-173">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-173">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5dc3c-174">字段名称</span><span class="sxs-lookup"><span data-stu-id="5dc3c-174">Field name</span></span>|<span data-ttu-id="5dc3c-175">数据类型</span><span class="sxs-lookup"><span data-stu-id="5dc3c-175">Data type</span></span>|<span data-ttu-id="5dc3c-176">说明</span><span class="sxs-lookup"><span data-stu-id="5dc3c-176">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5dc3c-177">ModuleID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-177">ModuleID</span></span>|<span data-ttu-id="5dc3c-178">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5dc3c-178">win:UInt16</span></span>|<span data-ttu-id="5dc3c-179">模块标识符。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-179">The module identifier.</span></span>|  
|<span data-ttu-id="5dc3c-180">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-180">StubMethodID</span></span>|<span data-ttu-id="5dc3c-181">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5dc3c-181">win:UInt64</span></span>|<span data-ttu-id="5dc3c-182">存根方法标识符。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-182">The stub method identifier.</span></span>|  
|<span data-ttu-id="5dc3c-183">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="5dc3c-183">ManagedInteropMethodToken</span></span>|<span data-ttu-id="5dc3c-184">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5dc3c-184">win:UInt32</span></span>|<span data-ttu-id="5dc3c-185">托管互操作方法的标记。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-185">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-186">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="5dc3c-186">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="5dc3c-187">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-187">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-188">托管互操作方法的命名空间。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-188">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-189">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="5dc3c-189">ManagedInteropMethodName</span></span>|<span data-ttu-id="5dc3c-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-190">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-191">托管互操作方法的名称。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-191">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="5dc3c-192">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="5dc3c-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5dc3c-193">win:UnicodeString</span></span>|<span data-ttu-id="5dc3c-194">托管互操作方法的签名。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-194">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="5dc3c-195">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5dc3c-195">ClrInstanceID</span></span>|<span data-ttu-id="5dc3c-196">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5dc3c-196">win:UInt16</span></span>|<span data-ttu-id="5dc3c-197">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5dc3c-197">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5dc3c-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5dc3c-198">See also</span></span>

- [<span data-ttu-id="5dc3c-199">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5dc3c-199">CLR ETW Events</span></span>](clr-etw-events.md)
