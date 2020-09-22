---
title: RemoveHandler 语句
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: a815241f20be12b3b7b4f2b87d50a8965021bbf0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871935"
---
# <a name="removehandler-statement"></a><span data-ttu-id="f0fc7-102">RemoveHandler 语句</span><span class="sxs-lookup"><span data-stu-id="f0fc7-102">RemoveHandler Statement</span></span>

<span data-ttu-id="f0fc7-103">删除事件和事件处理程序之间的关联。</span><span class="sxs-lookup"><span data-stu-id="f0fc7-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0fc7-104">语法</span><span class="sxs-lookup"><span data-stu-id="f0fc7-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="f0fc7-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="f0fc7-105">Parts</span></span>  
  
|<span data-ttu-id="f0fc7-106">术语</span><span class="sxs-lookup"><span data-stu-id="f0fc7-106">Term</span></span>|<span data-ttu-id="f0fc7-107">定义</span><span class="sxs-lookup"><span data-stu-id="f0fc7-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="f0fc7-108">正在处理的事件的名称。</span><span class="sxs-lookup"><span data-stu-id="f0fc7-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="f0fc7-109">当前处理事件的过程的名称。</span><span class="sxs-lookup"><span data-stu-id="f0fc7-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0fc7-110">备注</span><span class="sxs-lookup"><span data-stu-id="f0fc7-110">Remarks</span></span>  

 <span data-ttu-id="f0fc7-111">使用 `AddHandler` 和 `RemoveHandler` 语句，可以在程序执行过程中随时启动和停止特定事件的事件处理。</span><span class="sxs-lookup"><span data-stu-id="f0fc7-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0fc7-112">对于自定义事件，该 `RemoveHandler` 语句将调用事件的 `RemoveHandler` 访问器。</span><span class="sxs-lookup"><span data-stu-id="f0fc7-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="f0fc7-113">有关自定义事件的详细信息，请参阅 [Event 语句](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f0fc7-113">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0fc7-114">示例</span><span class="sxs-lookup"><span data-stu-id="f0fc7-114">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="f0fc7-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0fc7-115">See also</span></span>

- [<span data-ttu-id="f0fc7-116">AddHandler 语句</span><span class="sxs-lookup"><span data-stu-id="f0fc7-116">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="f0fc7-117">句柄数</span><span class="sxs-lookup"><span data-stu-id="f0fc7-117">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="f0fc7-118">Event 语句</span><span class="sxs-lookup"><span data-stu-id="f0fc7-118">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="f0fc7-119">事件</span><span class="sxs-lookup"><span data-stu-id="f0fc7-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
