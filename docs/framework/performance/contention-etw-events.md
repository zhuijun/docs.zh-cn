---
title: 争用 ETW 事件-.NET
description: 获取有关争用 ETW 事件的详细信息，每当存在争用的争用时，就会引发这些事件。
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309594"
---
# <a name="contention-etw-events"></a><span data-ttu-id="5d4b3-103">争用 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5d4b3-103">Contention ETW events</span></span>

<span data-ttu-id="5d4b3-104">只要运行时使用的 <xref:System.Threading.Monitor?displayProperty=nameWithType> 锁或本机锁出现争用情况，就会引发争用事件。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-104">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="5d4b3-105">一个线程等待的锁被另一线程占有时将发生争用。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-105">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="5d4b3-106">下表显示了引发争用事件的关键字以及事件的级别。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-106">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="5d4b3-107">有关详细信息，请参阅[CLR ETW 关键字和级别](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-107">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="5d4b3-108">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="5d4b3-108">Keyword for raising the event</span></span>|<span data-ttu-id="5d4b3-109">级别</span><span class="sxs-lookup"><span data-stu-id="5d4b3-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5d4b3-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="5d4b3-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="5d4b3-111">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="5d4b3-111">Informational (4)</span></span>|

<span data-ttu-id="5d4b3-112">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="5d4b3-112">The following table shows event information:</span></span>

|<span data-ttu-id="5d4b3-113">事件</span><span class="sxs-lookup"><span data-stu-id="5d4b3-113">Event</span></span>|<span data-ttu-id="5d4b3-114">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5d4b3-114">Event ID</span></span>|<span data-ttu-id="5d4b3-115">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="5d4b3-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="5d4b3-116">81</span><span class="sxs-lookup"><span data-stu-id="5d4b3-116">81</span></span>|<span data-ttu-id="5d4b3-117">争用开始。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-117">Contention starts.</span></span> <span data-ttu-id="5d4b3-118">此事件不包括线程等待获取锁之前的旋转时间；仅在线程等待获取锁时引发此事件。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-118">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="5d4b3-119">91</span><span class="sxs-lookup"><span data-stu-id="5d4b3-119">91</span></span>|<span data-ttu-id="5d4b3-120">争用结束。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-120">Contention ends.</span></span>|

<span data-ttu-id="5d4b3-121">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="5d4b3-121">The following table shows event data:</span></span>

|<span data-ttu-id="5d4b3-122">字段名</span><span class="sxs-lookup"><span data-stu-id="5d4b3-122">Field name</span></span>|<span data-ttu-id="5d4b3-123">数据类型</span><span class="sxs-lookup"><span data-stu-id="5d4b3-123">Data type</span></span>|<span data-ttu-id="5d4b3-124">说明</span><span class="sxs-lookup"><span data-stu-id="5d4b3-124">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5d4b3-125">Flags</span><span class="sxs-lookup"><span data-stu-id="5d4b3-125">Flags</span></span>|<span data-ttu-id="5d4b3-126">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="5d4b3-126">win:UInt8</span></span>|<span data-ttu-id="5d4b3-127">0 表示托管；1 表示本机。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-127">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="5d4b3-128">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5d4b3-128">ClrInstanceID</span></span>|<span data-ttu-id="5d4b3-129">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5d4b3-129">win:UInt16</span></span>|<span data-ttu-id="5d4b3-130">CLR 实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="5d4b3-130">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5d4b3-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d4b3-131">See also</span></span>

- [<span data-ttu-id="5d4b3-132">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="5d4b3-132">CLR ETW Events</span></span>](clr-etw-events.md)
