---
title: lock 语句 - C# 参考
description: 使用 C# lock 语句同步对共享资源的线程访问
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406685"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="99f6a-103">lock 语句（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="99f6a-103">lock statement (C# reference)</span></span>

<span data-ttu-id="99f6a-104">`lock` 语句获取给定对象的互斥 lock，执行语句块，然后释放 lock。</span><span class="sxs-lookup"><span data-stu-id="99f6a-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="99f6a-105">持有 lock 时，持有 lock 的线程可以再次获取并释放 lock。</span><span class="sxs-lookup"><span data-stu-id="99f6a-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="99f6a-106">阻止任何其他线程获取 lock 并等待释放 lock。</span><span class="sxs-lookup"><span data-stu-id="99f6a-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="99f6a-107">`lock` 语句具有以下格式</span><span class="sxs-lookup"><span data-stu-id="99f6a-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="99f6a-108">其中 `x` 是[引用类型](reference-types.md)的表达式。</span><span class="sxs-lookup"><span data-stu-id="99f6a-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="99f6a-109">它完全等同于</span><span class="sxs-lookup"><span data-stu-id="99f6a-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="99f6a-110">由于该代码使用 [try...finally](try-finally.md) 块，即使在 `lock` 语句的正文中引发异常，也会释放 lock。</span><span class="sxs-lookup"><span data-stu-id="99f6a-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="99f6a-111">在 `lock` 语句的正文中不能使用 [await 运算符](../operators/await.md)。</span><span class="sxs-lookup"><span data-stu-id="99f6a-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="99f6a-112">准则</span><span class="sxs-lookup"><span data-stu-id="99f6a-112">Guidelines</span></span>

<span data-ttu-id="99f6a-113">当同步对共享资源的线程访问时，请锁定专用对象实例（例如，`private readonly object balanceLock = new object();`）或另一个不太可能被代码无关部分用作 lock 对象的实例。</span><span class="sxs-lookup"><span data-stu-id="99f6a-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="99f6a-114">避免对不同的共享资源使用相同的 lock 对象实例，因为这可能导致死锁或锁争用。</span><span class="sxs-lookup"><span data-stu-id="99f6a-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="99f6a-115">具体而言，避免将以下对象用作 lock 对象：</span><span class="sxs-lookup"><span data-stu-id="99f6a-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="99f6a-116">`this`（调用方可能将其用作 lock）。</span><span class="sxs-lookup"><span data-stu-id="99f6a-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="99f6a-117"><xref:System.Type> 实例（可以通过 [typeof](../operators/type-testing-and-cast.md#typeof-operator) 运算符或反射获取）。</span><span class="sxs-lookup"><span data-stu-id="99f6a-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="99f6a-118">字符串实例，包括字符串文本，（这些可能是[暂存的](/dotnet/api/system.string.intern#remarks)）。</span><span class="sxs-lookup"><span data-stu-id="99f6a-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="99f6a-119">尽可能缩短持有锁的时间，以减少锁争用。</span><span class="sxs-lookup"><span data-stu-id="99f6a-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="99f6a-120">示例</span><span class="sxs-lookup"><span data-stu-id="99f6a-120">Example</span></span>

<span data-ttu-id="99f6a-121">以下示例定义了一个 `Account` 类，该类通过锁定专用的 `balanceLock` 实例来同步对其专用 `balance` 字段的访问。</span><span class="sxs-lookup"><span data-stu-id="99f6a-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="99f6a-122">使用相同的实例进行锁定可确保尝试同时调用 `Debit` 或 `Credit` 方法的两个线程无法同时更新 `balance` 字段。</span><span class="sxs-lookup"><span data-stu-id="99f6a-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="99f6a-123">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="99f6a-123">C# language specification</span></span>

<span data-ttu-id="99f6a-124">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [lock 语句](~/_csharplang/spec/statements.md#the-lock-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="99f6a-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99f6a-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="99f6a-125">See also</span></span>

- [<span data-ttu-id="99f6a-126">C# 参考</span><span class="sxs-lookup"><span data-stu-id="99f6a-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="99f6a-127">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="99f6a-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="99f6a-128">同步基元概述</span><span class="sxs-lookup"><span data-stu-id="99f6a-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
