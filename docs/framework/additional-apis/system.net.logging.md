---
title: 日志记录类（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990442"
---
# <a name="logging-class"></a><span data-ttu-id="56b11-102">日志记录类</span><span class="sxs-lookup"><span data-stu-id="56b11-102">Logging class</span></span>

<span data-ttu-id="56b11-103">提供跟踪日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="56b11-103">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="56b11-104">此类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="56b11-104">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="56b11-105">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="56b11-105">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="56b11-106">关联方法</span><span class="sxs-lookup"><span data-stu-id="56b11-106">Associate method</span></span>

<span data-ttu-id="56b11-107">记录两个对象彼此关联的信息。</span><span class="sxs-lookup"><span data-stu-id="56b11-107">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="56b11-108">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-108">Parameters</span></span>

- <span data-ttu-id="56b11-109">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-109">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-110">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-110">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-111">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-111">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-112">要与关联的对象 `objB` 。</span><span class="sxs-lookup"><span data-stu-id="56b11-112">The object to associate with `objB`.</span></span>

- <span data-ttu-id="56b11-113">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-113">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-114">要与关联的对象 `objA` 。</span><span class="sxs-lookup"><span data-stu-id="56b11-114">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="56b11-115">Enter （TraceSource，object，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-115">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="56b11-116">日志进入到方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-116">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="56b11-117">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-117">Parameters</span></span>

- <span data-ttu-id="56b11-118">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-118">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-119">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-119">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-120">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-120">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-121">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-121">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-122">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-122">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-123">正在输入的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-123">The method that is being entered.</span></span>

- <span data-ttu-id="56b11-124">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-124">`param` <xref:System.String></span></span>

  <span data-ttu-id="56b11-125">传递给方法的参数。</span><span class="sxs-lookup"><span data-stu-id="56b11-125">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="56b11-126">Enter （TraceSource，object，string，object）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-126">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="56b11-127">日志进入到方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-127">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="56b11-128">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-128">Parameters</span></span>

- <span data-ttu-id="56b11-129">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-129">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-130">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-130">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-131">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-131">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-132">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-132">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-133">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-133">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-134">正在输入的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-134">The method that is being entered.</span></span>

- <span data-ttu-id="56b11-135">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-135">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-136">传递给方法的参数。</span><span class="sxs-lookup"><span data-stu-id="56b11-136">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="56b11-137">Enter （TraceSource，string，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-137">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="56b11-138">日志进入到方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-138">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="56b11-139">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-139">Parameters</span></span>

- <span data-ttu-id="56b11-140">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-140">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-141">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-141">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-142">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-142">`obj` <xref:System.String></span></span>

  <span data-ttu-id="56b11-143">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-143">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-144">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-144">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-145">正在输入的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-145">The method that is being entered.</span></span>

- <span data-ttu-id="56b11-146">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-146">`param` <xref:System.String></span></span>

  <span data-ttu-id="56b11-147">传递给方法的参数。</span><span class="sxs-lookup"><span data-stu-id="56b11-147">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="56b11-148">Enter （TraceSource，string，string，object）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-148">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="56b11-149">日志进入到方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-149">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="56b11-150">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-150">Parameters</span></span>

- <span data-ttu-id="56b11-151">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-151">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-152">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-152">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-153">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-153">`obj` <xref:System.String></span></span>

  <span data-ttu-id="56b11-154">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-154">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-155">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-155">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-156">正在输入的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-156">The method that is being entered.</span></span>

- <span data-ttu-id="56b11-157">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-157">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-158">传递给方法的参数。</span><span class="sxs-lookup"><span data-stu-id="56b11-158">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="56b11-159">Enter （TraceSource，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-159">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="56b11-160">日志进入到方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-160">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="56b11-161">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-161">Parameters</span></span>

- <span data-ttu-id="56b11-162">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-162">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-163">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-163">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-164">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-164">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-165">正在输入的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-165">The method that is being entered.</span></span>

- <span data-ttu-id="56b11-166">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-166">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="56b11-167">传递给方法的参数。</span><span class="sxs-lookup"><span data-stu-id="56b11-167">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="56b11-168">Enter （TraceSource，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-168">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="56b11-169">日志进入到方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-169">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="56b11-170">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-170">Parameters</span></span>

- <span data-ttu-id="56b11-171">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-171">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-172">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-172">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-173">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-173">`msg` <xref:System.String></span></span>

  <span data-ttu-id="56b11-174">要记录到跟踪源的入口消息。</span><span class="sxs-lookup"><span data-stu-id="56b11-174">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="56b11-175">Exception 方法</span><span class="sxs-lookup"><span data-stu-id="56b11-175">Exception method</span></span>

<span data-ttu-id="56b11-176">记录异常并还原缩进。</span><span class="sxs-lookup"><span data-stu-id="56b11-176">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="56b11-177">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-177">Parameters</span></span>

- <span data-ttu-id="56b11-178">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-178">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-179">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-179">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-180">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-180">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-181">调用了引发异常的方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-181">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="56b11-182">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-182">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-183">引发异常的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-183">The method that threw the exception.</span></span>

- <span data-ttu-id="56b11-184">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="56b11-184">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="56b11-185">抛出的异常。</span><span class="sxs-lookup"><span data-stu-id="56b11-185">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="56b11-186">Exit （TraceSource、object、string、object）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-186">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="56b11-187">日志从函数退出。</span><span class="sxs-lookup"><span data-stu-id="56b11-187">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="56b11-188">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-188">Parameters</span></span>

- <span data-ttu-id="56b11-189">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-189">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-190">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-190">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-191">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-191">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-192">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-192">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-193">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-193">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-194">正在退出的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-194">The method that is being exited.</span></span>

- <span data-ttu-id="56b11-195">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-195">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-196">由方法返回的值。</span><span class="sxs-lookup"><span data-stu-id="56b11-196">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="56b11-197">Exit （TraceSource、string、string、object）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-197">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="56b11-198">日志从函数退出。</span><span class="sxs-lookup"><span data-stu-id="56b11-198">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="56b11-199">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-199">Parameters</span></span>

- <span data-ttu-id="56b11-200">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-200">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-201">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-201">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-202">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-202">`obj` <xref:System.String></span></span>

  <span data-ttu-id="56b11-203">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-203">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-204">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-204">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-205">正在退出的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-205">The method that is being exited.</span></span>

- <span data-ttu-id="56b11-206">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-206">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-207">由方法返回的值。</span><span class="sxs-lookup"><span data-stu-id="56b11-207">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="56b11-208">Exit （TraceSource，object，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-208">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="56b11-209">日志从函数退出。</span><span class="sxs-lookup"><span data-stu-id="56b11-209">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="56b11-210">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-210">Parameters</span></span>

- <span data-ttu-id="56b11-211">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-211">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-212">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-212">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-213">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="56b11-213">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="56b11-214">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-214">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-215">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-215">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-216">正在退出的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-216">The method that is being exited.</span></span>

- <span data-ttu-id="56b11-217">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-217">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="56b11-218">由方法返回的值。</span><span class="sxs-lookup"><span data-stu-id="56b11-218">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="56b11-219">Exit （TraceSource，string，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-219">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="56b11-220">日志从函数退出。</span><span class="sxs-lookup"><span data-stu-id="56b11-220">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="56b11-221">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-221">Parameters</span></span>

- <span data-ttu-id="56b11-222">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-222">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-223">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-223">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-224">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-224">`obj` <xref:System.String></span></span>

  <span data-ttu-id="56b11-225">在其上调用方法的对象。</span><span class="sxs-lookup"><span data-stu-id="56b11-225">The object that the method was called on.</span></span>

- <span data-ttu-id="56b11-226">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-226">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-227">正在退出的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-227">The method that is being exited.</span></span>

- <span data-ttu-id="56b11-228">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-228">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="56b11-229">由方法返回的值。</span><span class="sxs-lookup"><span data-stu-id="56b11-229">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="56b11-230">Exit （TraceSource，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-230">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="56b11-231">日志从函数退出。</span><span class="sxs-lookup"><span data-stu-id="56b11-231">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="56b11-232">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-232">Parameters</span></span>

- <span data-ttu-id="56b11-233">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-233">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-234">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-234">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-235">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-235">`method` <xref:System.String></span></span>

  <span data-ttu-id="56b11-236">正在退出的方法。</span><span class="sxs-lookup"><span data-stu-id="56b11-236">The method that is being exited.</span></span>

- <span data-ttu-id="56b11-237">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-237">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="56b11-238">传递给正在退出的方法的参数。</span><span class="sxs-lookup"><span data-stu-id="56b11-238">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="56b11-239">Exit （TraceSource，string）方法</span><span class="sxs-lookup"><span data-stu-id="56b11-239">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="56b11-240">日志从函数退出。</span><span class="sxs-lookup"><span data-stu-id="56b11-240">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="56b11-241">参数</span><span class="sxs-lookup"><span data-stu-id="56b11-241">Parameters</span></span>

- <span data-ttu-id="56b11-242">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="56b11-242">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="56b11-243">要将事件记录到的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-243">The trace source to log the event to.</span></span>

- <span data-ttu-id="56b11-244">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="56b11-244">`msg` <xref:System.String></span></span>

  <span data-ttu-id="56b11-245">要记录到跟踪源的退出消息。</span><span class="sxs-lookup"><span data-stu-id="56b11-245">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="56b11-246">Http 属性</span><span class="sxs-lookup"><span data-stu-id="56b11-246">Http property</span></span>

<span data-ttu-id="56b11-247">获取 "系统 .Net" 的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="56b11-247">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="56b11-248">属性值</span><span class="sxs-lookup"><span data-stu-id="56b11-248">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="56b11-249">"系统 .Net" 的跟踪源， `null` 如果未启用日志记录，则为。</span><span class="sxs-lookup"><span data-stu-id="56b11-249">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="56b11-250">On 属性</span><span class="sxs-lookup"><span data-stu-id="56b11-250">On property</span></span>

<span data-ttu-id="56b11-251">获取一个值，该值指示是否启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="56b11-251">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="56b11-252">属性值</span><span class="sxs-lookup"><span data-stu-id="56b11-252">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="56b11-253">如果启用日志记录，则为 `true`；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="56b11-253">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="56b11-254">要求</span><span class="sxs-lookup"><span data-stu-id="56b11-254">Requirements</span></span>

<span data-ttu-id="56b11-255">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="56b11-255">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="56b11-256">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="56b11-256">**Assembly:** System (in System.dll)</span></span>
