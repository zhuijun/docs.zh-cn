---
title: 创建 gRPC 客户端库-WCF 开发人员 gRPC
description: 针对 gRPC services 的共享客户端库/包的讨论。
ms.date: 09/02/2019
ms.openlocfilehash: e47ccd958007f84d633bb9ad5808c5e97c231977
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358838"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="0e8e3-103">创建 gRPC 客户端库</span><span class="sxs-lookup"><span data-stu-id="0e8e3-103">Create gRPC client libraries</span></span>

<span data-ttu-id="0e8e3-104">不需要为 gRPC 应用程序分发客户端库。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="0e8e3-105">你可以在组织中创建文件的共享库 `.proto` ，并且其他团队可以使用这些文件在其自己的项目中生成客户端代码。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="0e8e3-106">但是，如果你有一个专用 NuGet 存储库，而其他许多团队正在使用 .NET Core，则可以创建并发布客户端 NuGet 包作为你的服务项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="0e8e3-107">这可以是共享和升级服务的一种好方法。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="0e8e3-108">分发客户端库的一个优点是，您可以使用有用的 "方便性" 方法和属性来增强生成的 gRPC 和 Protobuf 类。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="0e8e3-109">在客户端代码中，与在服务器中一样，所有类都声明为 `partial` ，因此你可以在不编辑生成的代码的情况下扩展它们。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="0e8e3-110">这意味着可以轻松地将构造函数、方法和计算属性添加到基本类型。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="0e8e3-111">不应使用自定义代码来提供基本功能。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="0e8e3-112">您不希望将这一基本功能限制为使用共享库的 .NET 团队，而不是将其提供给使用其他语言或平台（如 Python 或 Java）的团队。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="0e8e3-113">请确保尽可能多的团队可以访问你的 gRPC 服务。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="0e8e3-114">实现此目的的最佳方式是共享 `.proto` 文件，使开发人员能够生成自己的客户端。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="0e8e3-115">在多平台环境中尤其如此，在这种环境中，不同的团队经常使用不同的编程语言和框架，或者 API 可从外部访问。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="0e8e3-116">有用的扩展</span><span class="sxs-lookup"><span data-stu-id="0e8e3-116">Useful extensions</span></span>

<span data-ttu-id="0e8e3-117">.NET 中有两种常用接口用于处理对象的流： <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IObservable%601> 。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="0e8e3-118">从 .NET Core 3.0 和 c # 8.0 开始，有一个 <xref:System.Collections.Generic.IAsyncEnumerable%601> 用于异步处理流的接口，以及一个 `await foreach` 使用接口的语法。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="0e8e3-119">本部分提供可重用的代码，用于将这些接口应用到 gRPC 流。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="0e8e3-120">使用 .NET Core gRPC 客户端库，可使用的 `ReadAllAsync` 扩展方法 `IAsyncStreamReader<T>` 创建 `IAsyncEnumerable<T>` 接口。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="0e8e3-121">对于使用反应性编程的开发人员而言，创建接口的等效扩展方法 `IObservable<T>` 可能类似于以下部分中的示例。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="0e8e3-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="0e8e3-122">IObservable</span></span>

<span data-ttu-id="0e8e3-123">`IObservable<T>`接口是的 "事后" 反转 `IEnumerable<T>` 。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="0e8e3-124">反应方法不会从流中提取项，而是允许流将项推送到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="0e8e3-125">这非常类似于 gRPC 流，并且可以轻松地在 `IObservable<T>` 接口周围环绕接口 `IAsyncStreamReader<T>` 。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="0e8e3-126">此代码比 `IAsyncEnumerable<T>` 代码长，因为 c # 不支持使用可观察量。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="0e8e3-127">必须手动创建实现类。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="0e8e3-128">但它是一个泛型类，因此单个实现适用于所有类型。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-128">It's a generic class, though, so a single implementation works across all types.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public GrpcStreamObservable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="0e8e3-129">此可观察实现允许 `Subscribe` 只调用一次方法，因为尝试从流中读取多个订阅服务器会导致混乱。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="0e8e3-130">有一些运算符（例如 `Replay` ，在可观察量[System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq)中）支持缓冲和可重复共享的，可与此实现一起使用。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="0e8e3-131">`GrpcStreamSubscription`类处理的枚举 `IAsyncStreamReader` ：</span><span class="sxs-lookup"><span data-stu-id="0e8e3-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public GrpcStreamSubscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

<span data-ttu-id="0e8e3-132">现在只需要一个简单的扩展方法，用于从流读取器创建可观察的。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a><span data-ttu-id="0e8e3-133">总结</span><span class="sxs-lookup"><span data-stu-id="0e8e3-133">Summary</span></span>

<span data-ttu-id="0e8e3-134">`IAsyncEnumerable`和 `IObservable` 模型都是支持良好的，并以详细的方式记录了如何处理 .net 中的数据数据流。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="0e8e3-135">gRPC 流可以很好地映射到这两个范例，提供与 .NET Core 的紧密集成，并提供反应性和异步编程风格。</span><span class="sxs-lookup"><span data-stu-id="0e8e3-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0e8e3-136">[上一页](streaming-versus-repeated.md)
>[下一页](security.md)</span><span class="sxs-lookup"><span data-stu-id="0e8e3-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
