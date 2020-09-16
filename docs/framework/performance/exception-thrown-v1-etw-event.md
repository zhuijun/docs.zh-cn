---
title: 异常 Thrown_V1 ETW 事件
description: 查看有关 ExceptionThrown_V1 ETW 事件的详细信息。 将为引发的异常提供事件数据（如字段名称、数据类型和说明）。
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f4ae277b5dfb09d2676755fec2208b63906ead84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554666"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="042db-104">异常 Thrown_V1 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="042db-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="042db-105">该事件捕获有关引发的异常的信息。</span><span class="sxs-lookup"><span data-stu-id="042db-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="042db-106">下表显示了引发事件的关键字以及事件的级别。</span><span class="sxs-lookup"><span data-stu-id="042db-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="042db-107">（有关详细信息，请参阅 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)。）</span><span class="sxs-lookup"><span data-stu-id="042db-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="042db-108">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="042db-108">Keyword for raising the event</span></span>|<span data-ttu-id="042db-109">级别</span><span class="sxs-lookup"><span data-stu-id="042db-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="042db-110">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="042db-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="042db-111">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="042db-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="042db-112">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="042db-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="042db-113">事件</span><span class="sxs-lookup"><span data-stu-id="042db-113">Event</span></span>|<span data-ttu-id="042db-114">事件 ID</span><span class="sxs-lookup"><span data-stu-id="042db-114">Event ID</span></span>|<span data-ttu-id="042db-115">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="042db-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="042db-116">80</span><span class="sxs-lookup"><span data-stu-id="042db-116">80</span></span>|<span data-ttu-id="042db-117">引发托管异常。</span><span class="sxs-lookup"><span data-stu-id="042db-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="042db-118">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="042db-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="042db-119">字段名称</span><span class="sxs-lookup"><span data-stu-id="042db-119">Field name</span></span>|<span data-ttu-id="042db-120">数据类型</span><span class="sxs-lookup"><span data-stu-id="042db-120">Data type</span></span>|<span data-ttu-id="042db-121">说明</span><span class="sxs-lookup"><span data-stu-id="042db-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="042db-122">异常类型</span><span class="sxs-lookup"><span data-stu-id="042db-122">Exception Type</span></span>|<span data-ttu-id="042db-123">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="042db-123">win:UnicodeString</span></span>|<span data-ttu-id="042db-124">异常的类型，例如，`System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="042db-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="042db-125">异常消息</span><span class="sxs-lookup"><span data-stu-id="042db-125">Exception Message</span></span>|<span data-ttu-id="042db-126">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="042db-126">win:UnicodeString</span></span>|<span data-ttu-id="042db-127">实际的异常消息。</span><span class="sxs-lookup"><span data-stu-id="042db-127">Actual exception message.</span></span>|  
|<span data-ttu-id="042db-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="042db-128">EIPCodeThrow</span></span>|<span data-ttu-id="042db-129">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="042db-129">win:Pointer</span></span>|<span data-ttu-id="042db-130">指向异常发生位置的指令指针。</span><span class="sxs-lookup"><span data-stu-id="042db-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="042db-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="042db-131">ExceptionHR</span></span>|<span data-ttu-id="042db-132">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="042db-132">win:UInt32</span></span>|<span data-ttu-id="042db-133">异常 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。</span><span class="sxs-lookup"><span data-stu-id="042db-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="042db-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="042db-134">ExceptionFlags</span></span>|<span data-ttu-id="042db-135">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="042db-135">win:UInt16</span></span>|<span data-ttu-id="042db-136">0x01: HasInnerException（参阅 Visual Basic 文档中的 [CLR ETW 事件](clr-etw-events.md)）。</span><span class="sxs-lookup"><span data-stu-id="042db-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="042db-137">0x02: IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="042db-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="042db-138">0x04: IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="042db-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="042db-139">0x08： IsCorruptedStateException (指示进程状态已损坏;请参阅 [处理损坏状态异常](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)) 。</span><span class="sxs-lookup"><span data-stu-id="042db-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="042db-140">0x10: IsCLSCompliant（从 <xref:System.Exception> 派生的异常符合 CLS，此外的其他异常均不符合 CLS）。</span><span class="sxs-lookup"><span data-stu-id="042db-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="042db-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="042db-141">ClrInstanceID</span></span>|<span data-ttu-id="042db-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="042db-142">win:UInt16</span></span>|<span data-ttu-id="042db-143">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="042db-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="042db-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="042db-144">See also</span></span>

- [<span data-ttu-id="042db-145">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="042db-145">CLR ETW Events</span></span>](clr-etw-events.md)
