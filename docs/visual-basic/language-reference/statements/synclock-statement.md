---
title: SyncLock 语句
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404156"
---
# <a name="synclock-statement"></a><span data-ttu-id="6f408-102">SyncLock 语句</span><span class="sxs-lookup"><span data-stu-id="6f408-102">SyncLock Statement</span></span>
<span data-ttu-id="6f408-103">在执行块之前获取语句块的排他锁。</span><span class="sxs-lookup"><span data-stu-id="6f408-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f408-104">语法</span><span class="sxs-lookup"><span data-stu-id="6f408-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="6f408-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="6f408-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="6f408-106">必需。</span><span class="sxs-lookup"><span data-stu-id="6f408-106">Required.</span></span> <span data-ttu-id="6f408-107">计算结果为对象引用的表达式。</span><span class="sxs-lookup"><span data-stu-id="6f408-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="6f408-108">可选。</span><span class="sxs-lookup"><span data-stu-id="6f408-108">Optional.</span></span> <span data-ttu-id="6f408-109">获取锁时要执行的语句块。</span><span class="sxs-lookup"><span data-stu-id="6f408-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="6f408-110">终止 `SyncLock` 块。</span><span class="sxs-lookup"><span data-stu-id="6f408-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f408-111">备注</span><span class="sxs-lookup"><span data-stu-id="6f408-111">Remarks</span></span>  
 <span data-ttu-id="6f408-112">`SyncLock`语句可确保多个线程不会同时执行语句块。</span><span class="sxs-lookup"><span data-stu-id="6f408-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="6f408-113">`SyncLock`阻止每个线程进入块，直到没有其他线程执行它。</span><span class="sxs-lookup"><span data-stu-id="6f408-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="6f408-114">最常见的用途 `SyncLock` 是防止多个线程同时更新数据。</span><span class="sxs-lookup"><span data-stu-id="6f408-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="6f408-115">如果操作数据的语句必须在不中断的情况下完成，请将它们放在 `SyncLock` 块内。</span><span class="sxs-lookup"><span data-stu-id="6f408-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="6f408-116">受排他锁保护的语句块有时称为*临界区*。</span><span class="sxs-lookup"><span data-stu-id="6f408-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6f408-117">规则</span><span class="sxs-lookup"><span data-stu-id="6f408-117">Rules</span></span>  
  
- <span data-ttu-id="6f408-118">产生.</span><span class="sxs-lookup"><span data-stu-id="6f408-118">Branching.</span></span> <span data-ttu-id="6f408-119">不能 `SyncLock` 从块外分支到块。</span><span class="sxs-lookup"><span data-stu-id="6f408-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="6f408-120">锁定对象值。</span><span class="sxs-lookup"><span data-stu-id="6f408-120">Lock Object Value.</span></span> <span data-ttu-id="6f408-121">的值 `lockobject` 不能为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="6f408-122">在语句中使用该锁对象之前，必须先创建它 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="6f408-123">执行块时无法更改的值 `lockobject` `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="6f408-124">机制要求锁定对象保持不变。</span><span class="sxs-lookup"><span data-stu-id="6f408-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="6f408-125">不能在块中使用[Await](../operators/await-operator.md)运算符 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-125">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6f408-126">行为</span><span class="sxs-lookup"><span data-stu-id="6f408-126">Behavior</span></span>  
  
- <span data-ttu-id="6f408-127">机制.</span><span class="sxs-lookup"><span data-stu-id="6f408-127">Mechanism.</span></span> <span data-ttu-id="6f408-128">当线程到达语句时 `SyncLock` ，它将计算 `lockobject` 表达式并挂起执行，直到它获取表达式返回的对象上的排他锁。</span><span class="sxs-lookup"><span data-stu-id="6f408-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="6f408-129">当另一个线程到达 `SyncLock` 语句时，它不会获取锁定，直到第一个线程执行该 `End SyncLock` 语句。</span><span class="sxs-lookup"><span data-stu-id="6f408-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="6f408-130">受保护的数据。</span><span class="sxs-lookup"><span data-stu-id="6f408-130">Protected Data.</span></span> <span data-ttu-id="6f408-131">如果 `lockobject` 是一个 `Shared` 变量，则排他锁会阻止在 `SyncLock` 任何其他线程执行块时，类的任何实例中的线程执行此块。</span><span class="sxs-lookup"><span data-stu-id="6f408-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="6f408-132">这会保护在所有实例之间共享的数据。</span><span class="sxs-lookup"><span data-stu-id="6f408-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="6f408-133">如果 `lockobject` 是实例变量（而不是 `Shared` ），则锁定会阻止在当前实例中运行的线程与 `SyncLock` 同一实例中的另一个线程同时执行块。</span><span class="sxs-lookup"><span data-stu-id="6f408-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="6f408-134">这将保护由单个实例维护的数据。</span><span class="sxs-lookup"><span data-stu-id="6f408-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="6f408-135">获取和发布。</span><span class="sxs-lookup"><span data-stu-id="6f408-135">Acquisition and Release.</span></span> <span data-ttu-id="6f408-136">`SyncLock`块的行为类似于 `Try...Finally` 构造 `Try` ，其中块在上获取排他锁 `lockobject` ，而 `Finally` 块释放它。</span><span class="sxs-lookup"><span data-stu-id="6f408-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="6f408-137">因此，无论 `SyncLock` 退出块的方式如何，块都将保证锁的版本。</span><span class="sxs-lookup"><span data-stu-id="6f408-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="6f408-138">即使在发生未经处理的异常时也是如此。</span><span class="sxs-lookup"><span data-stu-id="6f408-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="6f408-139">框架调用。</span><span class="sxs-lookup"><span data-stu-id="6f408-139">Framework Calls.</span></span> <span data-ttu-id="6f408-140">`SyncLock`块通过调用 `Enter` `Exit` `Monitor` 命名空间中类的和方法来获取和释放排他锁 <xref:System.Threading> 。</span><span class="sxs-lookup"><span data-stu-id="6f408-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="6f408-141">编程做法</span><span class="sxs-lookup"><span data-stu-id="6f408-141">Programming Practices</span></span>  
 <span data-ttu-id="6f408-142">`lockobject`表达式应始终计算为仅属于您的类的对象。</span><span class="sxs-lookup"><span data-stu-id="6f408-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="6f408-143">你应声明一个 `Private` 对象变量来保护属于当前实例的数据，或声明一个 `Private Shared` 对象变量来保护所有实例通用的数据。</span><span class="sxs-lookup"><span data-stu-id="6f408-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="6f408-144">不应使用 `Me` 关键字为实例数据提供锁定对象。</span><span class="sxs-lookup"><span data-stu-id="6f408-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="6f408-145">如果类的外部代码具有对类的实例的引用，它可以将该引用用作 `SyncLock` 完全不同于你的块的锁对象，从而保护不同的数据。</span><span class="sxs-lookup"><span data-stu-id="6f408-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="6f408-146">通过这种方式，你的类和其他类可以相互阻止执行它们的无关 `SyncLock` 块。</span><span class="sxs-lookup"><span data-stu-id="6f408-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="6f408-147">类似地锁定字符串可能会产生问题，因为使用相同字符串的进程中的任何其他代码都将共享同一个锁。</span><span class="sxs-lookup"><span data-stu-id="6f408-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="6f408-148">您也不应使用 `Me.GetType` 方法来为共享数据提供锁定对象。</span><span class="sxs-lookup"><span data-stu-id="6f408-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="6f408-149">这是因为， `GetType` 对于给定的类名称始终返回相同的 `Type` 对象。</span><span class="sxs-lookup"><span data-stu-id="6f408-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="6f408-150">外部代码可以调用 `GetType` 你的类，并获得你正在使用的同一个锁定对象。</span><span class="sxs-lookup"><span data-stu-id="6f408-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="6f408-151">这会导致两个类彼此阻止它们 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6f408-152">示例</span><span class="sxs-lookup"><span data-stu-id="6f408-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="6f408-153">说明</span><span class="sxs-lookup"><span data-stu-id="6f408-153">Description</span></span>  
 <span data-ttu-id="6f408-154">下面的示例演示维护简单消息列表的类。</span><span class="sxs-lookup"><span data-stu-id="6f408-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="6f408-155">它将消息保存在一个数组中，并将该数组的最后一个使用元素保存在一个变量中。</span><span class="sxs-lookup"><span data-stu-id="6f408-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="6f408-156">此 `addAnotherMessage` 过程将递增最后一个元素并存储新的消息。</span><span class="sxs-lookup"><span data-stu-id="6f408-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="6f408-157">这两个操作由 `SyncLock` 和语句保护 `End SyncLock` ，因为在递增最后一个元素之后，必须先存储新消息，然后其他任何线程才可以再次增加最后一个元素。</span><span class="sxs-lookup"><span data-stu-id="6f408-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="6f408-158">如果 `simpleMessageList` 类在所有实例中共享消息列表，则变量 `messagesList` 和将 `messagesLast` 声明为 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="6f408-159">在这种情况下，变量 `messagesLock` 还应为 `Shared` ，因此每个实例都使用单个锁对象。</span><span class="sxs-lookup"><span data-stu-id="6f408-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6f408-160">代码</span><span class="sxs-lookup"><span data-stu-id="6f408-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="6f408-161">说明</span><span class="sxs-lookup"><span data-stu-id="6f408-161">Description</span></span>  
 <span data-ttu-id="6f408-162">下面的示例使用线程和 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="6f408-163">只要该 `SyncLock` 语句存在，语句块就会成为关键部分，并且 `balance` 永远不会成为负数。</span><span class="sxs-lookup"><span data-stu-id="6f408-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="6f408-164">您可以 `SyncLock` `End SyncLock` 对和语句进行注释，以查看离开关键字的效果 `SyncLock` 。</span><span class="sxs-lookup"><span data-stu-id="6f408-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6f408-165">代码</span><span class="sxs-lookup"><span data-stu-id="6f408-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="6f408-166">注释</span><span class="sxs-lookup"><span data-stu-id="6f408-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f408-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f408-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="6f408-168">同步基元概述</span><span class="sxs-lookup"><span data-stu-id="6f408-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
