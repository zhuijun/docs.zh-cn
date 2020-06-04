---
title: AddHandler 语句
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: de995a13b34678410e2af74b59f2d0c467982b75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408479"
---
# <a name="addhandler-statement"></a><span data-ttu-id="1d36b-102">AddHandler 语句</span><span class="sxs-lookup"><span data-stu-id="1d36b-102">AddHandler Statement</span></span>
<span data-ttu-id="1d36b-103">在运行时将事件与事件处理程序相关联。</span><span class="sxs-lookup"><span data-stu-id="1d36b-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d36b-104">语法</span><span class="sxs-lookup"><span data-stu-id="1d36b-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="1d36b-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="1d36b-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="1d36b-106">event</span><span class="sxs-lookup"><span data-stu-id="1d36b-106">event</span></span>|<span data-ttu-id="1d36b-107">要处理的事件的名称。</span><span class="sxs-lookup"><span data-stu-id="1d36b-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="1d36b-108">处理事件的过程的名称。</span><span class="sxs-lookup"><span data-stu-id="1d36b-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="1d36b-109">备注</span><span class="sxs-lookup"><span data-stu-id="1d36b-109">Remarks</span></span>  
 <span data-ttu-id="1d36b-110">`AddHandler`和 `RemoveHandler` 语句允许您在程序执行过程中随时启动和停止事件处理。</span><span class="sxs-lookup"><span data-stu-id="1d36b-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="1d36b-111">过程的签名 `eventhandler` 必须与事件的签名相匹配 `event` 。</span><span class="sxs-lookup"><span data-stu-id="1d36b-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="1d36b-112">`Handles` 关键字和 `AddHandler` 语句都允许你指定特定过程处理特定事件，但存在差异。</span><span class="sxs-lookup"><span data-stu-id="1d36b-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="1d36b-113">`AddHandler` 语句在运行时将过程连接到事件。</span><span class="sxs-lookup"><span data-stu-id="1d36b-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="1d36b-114">定义过程时使用 `Handles` 关键字，以指定它处理特定事件。</span><span class="sxs-lookup"><span data-stu-id="1d36b-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="1d36b-115">有关详细信息，请参阅[句柄](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="1d36b-115">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d36b-116">对于自定义事件，该 `AddHandler` 语句将调用事件的 `AddHandler` 访问器。</span><span class="sxs-lookup"><span data-stu-id="1d36b-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="1d36b-117">有关自定义事件的详细信息，请参阅[Event 语句](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1d36b-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d36b-118">示例</span><span class="sxs-lookup"><span data-stu-id="1d36b-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="1d36b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d36b-119">See also</span></span>

- [<span data-ttu-id="1d36b-120">RemoveHandler 语句</span><span class="sxs-lookup"><span data-stu-id="1d36b-120">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="1d36b-121">句柄数</span><span class="sxs-lookup"><span data-stu-id="1d36b-121">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="1d36b-122">Event 语句</span><span class="sxs-lookup"><span data-stu-id="1d36b-122">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="1d36b-123">事件</span><span class="sxs-lookup"><span data-stu-id="1d36b-123">Events</span></span>](../../programming-guide/language-features/events/index.md)
