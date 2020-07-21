---
title: 安全 ETW 事件
description: 了解在 .NET 中强名称验证和验证码验证期间引发的安全 ETW 事件。
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474210"
---
# <a name="security-etw-events"></a><span data-ttu-id="5313b-103">安全 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5313b-103">Security ETW Events</span></span>

<span data-ttu-id="5313b-104">在强名称验证和验证码验证期间会引发安全事件。</span><span class="sxs-lookup"><span data-stu-id="5313b-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="5313b-105">StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="5313b-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5313b-106">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="5313b-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="5313b-107">（有关详细信息，请参阅 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)。）</span><span class="sxs-lookup"><span data-stu-id="5313b-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5313b-108">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="5313b-108">Keyword for raising the event</span></span>|<span data-ttu-id="5313b-109">级别</span><span class="sxs-lookup"><span data-stu-id="5313b-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5313b-110">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5313b-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5313b-111">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="5313b-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="5313b-112">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="5313b-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5313b-113">事件</span><span class="sxs-lookup"><span data-stu-id="5313b-113">Event</span></span>|<span data-ttu-id="5313b-114">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5313b-114">Event ID</span></span>|<span data-ttu-id="5313b-115">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="5313b-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="5313b-116">181</span><span class="sxs-lookup"><span data-stu-id="5313b-116">181</span></span>|<span data-ttu-id="5313b-117">强名称验证开始。</span><span class="sxs-lookup"><span data-stu-id="5313b-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="5313b-118">182</span><span class="sxs-lookup"><span data-stu-id="5313b-118">182</span></span>|<span data-ttu-id="5313b-119">强名称验证结束。</span><span class="sxs-lookup"><span data-stu-id="5313b-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="5313b-120">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="5313b-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5313b-121">字段名称</span><span class="sxs-lookup"><span data-stu-id="5313b-121">Field name</span></span>|<span data-ttu-id="5313b-122">数据类型</span><span class="sxs-lookup"><span data-stu-id="5313b-122">Data type</span></span>|<span data-ttu-id="5313b-123">说明</span><span class="sxs-lookup"><span data-stu-id="5313b-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5313b-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5313b-124">VerificationFlags</span></span>|<span data-ttu-id="5313b-125">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5313b-125">win:UInt32</span></span>|<span data-ttu-id="5313b-126">验证标志。</span><span class="sxs-lookup"><span data-stu-id="5313b-126">The verification flags.</span></span>|  
|<span data-ttu-id="5313b-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5313b-127">ErrorCode</span></span>|<span data-ttu-id="5313b-128">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5313b-128">win:UInt32</span></span>|<span data-ttu-id="5313b-129">HResult 错误代码。</span><span class="sxs-lookup"><span data-stu-id="5313b-129">The HResult error code.</span></span>|  
|<span data-ttu-id="5313b-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="5313b-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="5313b-131">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5313b-131">win:UnicodeString</span></span>|<span data-ttu-id="5313b-132">完全限定程序集名称。</span><span class="sxs-lookup"><span data-stu-id="5313b-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="5313b-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5313b-133">ClrInstanceID</span></span>|<span data-ttu-id="5313b-134">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5313b-134">win:UInt16</span></span>|<span data-ttu-id="5313b-135">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5313b-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="5313b-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="5313b-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5313b-137">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="5313b-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="5313b-138">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="5313b-138">Keyword for raising the event</span></span>|<span data-ttu-id="5313b-139">级别</span><span class="sxs-lookup"><span data-stu-id="5313b-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5313b-140">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5313b-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5313b-141">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="5313b-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="5313b-142">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="5313b-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5313b-143">事件</span><span class="sxs-lookup"><span data-stu-id="5313b-143">Event</span></span>|<span data-ttu-id="5313b-144">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5313b-144">Event ID</span></span>|<span data-ttu-id="5313b-145">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="5313b-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="5313b-146">183</span><span class="sxs-lookup"><span data-stu-id="5313b-146">183</span></span>|<span data-ttu-id="5313b-147">验证码验证开始。</span><span class="sxs-lookup"><span data-stu-id="5313b-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="5313b-148">184</span><span class="sxs-lookup"><span data-stu-id="5313b-148">184</span></span>|<span data-ttu-id="5313b-149">验证码验证结束。</span><span class="sxs-lookup"><span data-stu-id="5313b-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="5313b-150">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="5313b-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5313b-151">字段名称</span><span class="sxs-lookup"><span data-stu-id="5313b-151">Field name</span></span>|<span data-ttu-id="5313b-152">数据类型</span><span class="sxs-lookup"><span data-stu-id="5313b-152">Data type</span></span>|<span data-ttu-id="5313b-153">说明</span><span class="sxs-lookup"><span data-stu-id="5313b-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5313b-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5313b-154">VerificationFlags</span></span>|<span data-ttu-id="5313b-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5313b-155">win:UInt32</span></span>|<span data-ttu-id="5313b-156">验证标志。</span><span class="sxs-lookup"><span data-stu-id="5313b-156">The verification flags.</span></span>|  
|<span data-ttu-id="5313b-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5313b-157">ErrorCode</span></span>|<span data-ttu-id="5313b-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5313b-158">win:UInt32</span></span>|<span data-ttu-id="5313b-159">HResult 错误代码。</span><span class="sxs-lookup"><span data-stu-id="5313b-159">The HResult error code.</span></span>|  
|<span data-ttu-id="5313b-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="5313b-160">ModulePath</span></span>|<span data-ttu-id="5313b-161">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5313b-161">win:UnicodeString</span></span>|<span data-ttu-id="5313b-162">模块路径。</span><span class="sxs-lookup"><span data-stu-id="5313b-162">The module path.</span></span>|  
|<span data-ttu-id="5313b-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5313b-163">ClrInstanceID</span></span>|<span data-ttu-id="5313b-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5313b-164">win:UInt16</span></span>|<span data-ttu-id="5313b-165">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5313b-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5313b-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5313b-166">See also</span></span>

- [<span data-ttu-id="5313b-167">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5313b-167">CLR ETW Events</span></span>](clr-etw-events.md)
