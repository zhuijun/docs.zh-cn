---
title: “<eventname>”是事件，不能直接调用
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 510fff5370e63a31ee271421c0ab6f154518899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409590"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="a6fb0-102">“\<eventname>”是事件，不能直接调用</span><span class="sxs-lookup"><span data-stu-id="a6fb0-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="a6fb0-103">"<`eventname`>" 是一个事件，因此不能直接调用。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="a6fb0-104">使用 `RaiseEvent` 语句引发事件。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="a6fb0-105">过程调用指定过程名称的事件。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="a6fb0-106">事件处理程序是一个过程，但事件本身就是信号设备，必须引发并处理。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="a6fb0-107">**错误 ID：** BC32022</span><span class="sxs-lookup"><span data-stu-id="a6fb0-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6fb0-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="a6fb0-108">To correct this error</span></span>  
  
1. <span data-ttu-id="a6fb0-109">使用 `RaiseEvent` 语句对事件发出信号并调用处理该事件的过程。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fb0-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6fb0-110">See also</span></span>

- [<span data-ttu-id="a6fb0-111">RaiseEvent 语句</span><span class="sxs-lookup"><span data-stu-id="a6fb0-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
