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
ms.openlocfilehash: 79dbe174209e91f13f5b43e8cdeb0b42edc4d163
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866709"
---
# <a name="addhandler-statement"></a><span data-ttu-id="4b206-102">AddHandler 语句</span><span class="sxs-lookup"><span data-stu-id="4b206-102">AddHandler Statement</span></span>

<span data-ttu-id="4b206-103">在运行时将事件与事件处理程序相关联。</span><span class="sxs-lookup"><span data-stu-id="4b206-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b206-104">语法</span><span class="sxs-lookup"><span data-stu-id="4b206-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4b206-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="4b206-105">Parts</span></span>  

|||
|---|---|
|<span data-ttu-id="4b206-106">event</span><span class="sxs-lookup"><span data-stu-id="4b206-106">event</span></span>|<span data-ttu-id="4b206-107">要处理的事件的名称。</span><span class="sxs-lookup"><span data-stu-id="4b206-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="4b206-108">处理事件的过程的名称。</span><span class="sxs-lookup"><span data-stu-id="4b206-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="4b206-109">备注</span><span class="sxs-lookup"><span data-stu-id="4b206-109">Remarks</span></span>  

 <span data-ttu-id="4b206-110">`AddHandler`和 `RemoveHandler` 语句允许您在程序执行过程中随时启动和停止事件处理。</span><span class="sxs-lookup"><span data-stu-id="4b206-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="4b206-111">过程的签名 `eventhandler` 必须与事件的签名相匹配 `event` 。</span><span class="sxs-lookup"><span data-stu-id="4b206-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="4b206-112">`Handles` 关键字和 `AddHandler` 语句都允许你指定特定过程处理特定事件，但存在差异。</span><span class="sxs-lookup"><span data-stu-id="4b206-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="4b206-113">`AddHandler` 语句在运行时将过程连接到事件。</span><span class="sxs-lookup"><span data-stu-id="4b206-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="4b206-114">定义过程时使用 `Handles` 关键字，以指定它处理特定事件。</span><span class="sxs-lookup"><span data-stu-id="4b206-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="4b206-115">有关详细信息，请参阅 [句柄](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="4b206-115">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b206-116">对于自定义事件，该 `AddHandler` 语句将调用事件的 `AddHandler` 访问器。</span><span class="sxs-lookup"><span data-stu-id="4b206-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="4b206-117">有关自定义事件的详细信息，请参阅 [Event 语句](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4b206-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b206-118">示例</span><span class="sxs-lookup"><span data-stu-id="4b206-118">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="4b206-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b206-119">See also</span></span>

- [<span data-ttu-id="4b206-120">RemoveHandler 语句</span><span class="sxs-lookup"><span data-stu-id="4b206-120">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="4b206-121">句柄数</span><span class="sxs-lookup"><span data-stu-id="4b206-121">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="4b206-122">Event 语句</span><span class="sxs-lookup"><span data-stu-id="4b206-122">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="4b206-123">事件</span><span class="sxs-lookup"><span data-stu-id="4b206-123">Events</span></span>](../../programming-guide/language-features/events/index.md)
