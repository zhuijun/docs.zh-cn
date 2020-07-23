---
title: 实现 DisposeAsync 方法
description: ''
author: IEvangelist
ms.author: dapine
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 91ace1932e8bb751e8e1d85e00b3e239a01aa9ea
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309815"
---
# <a name="implement-a-disposeasync-method"></a>实现 DisposeAsync 方法

已将 <xref:System.IAsyncDisposable?displayProperty=nameWithType> 接口作为 C# 8.0 的一部分引入。 需要执行资源清理时，可以实现 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 方法，就像[实现 Dispose 方法](implementing-dispose.md)一样。 但是，其中一个主要区别是，此实现允许异步清理操作。 <xref:System.IAsyncDisposable.DisposeAsync> 返回表示异步释放操作的 <xref:System.Threading.Tasks.ValueTask>。

通常，当实现 <xref:System.IAsyncDisposable> 接口时，类还将实现 <xref:System.IDisposable> 接口。 <xref:System.IAsyncDisposable> 接口的一种良好实现模式是为同步或异步释放做好准备。 用于实现释放模式的所有指南都适用于异步实现。 本文假设你已熟悉如何[实现 Dispose 方法](implementing-dispose.md)。

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync() 和 DisposeAsyncCore()

<xref:System.IAsyncDisposable> 接口声明单个无参数方法 <xref:System.IAsyncDisposable.DisposeAsync>。 任何非密封类都应具有另外一个也返回 <xref:System.Threading.Tasks.ValueTask> 的 `DisposeAsyncCore()` 方法。

- 没有参数的 `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> 实现。
- 一个 `protected virtual ValueTask DisposeAsyncCore()` 方法，其签名为：

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

`DisposeAsyncCore()` 方法是 `virtual`，以便派生类可以在其重写中定义其他清理。

### <a name="the-disposeasync-method"></a>DisposeAsync() 方法

`public` 无参数的 `DisposeAsync()` 方法在 `await using` 语句中隐式调用，其用途是释放非托管资源，执行常规清理，以及指示终结器（如果存在）不必运行。 释放与托管对象关联的内存始终是[垃圾回收器](index.md)的域。 因此，它具有标准实现：

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of managed resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> 与释放模式相比，异步释放模式的主要差异在于，从 <xref:System.IAsyncDisposable.DisposeAsync> 到 `Dispose(bool)` 重载方法的调用被赋予 `false` 作为参数。 但实现 <xref:System.IDisposable.Dispose?displayProperty=nameWithType> 方法时，改为传递 `true`。 这有助于确保与同步释放模式的功能等效性，并进一步确保仍调用终结器代码路径。 换句话说，`DisposeAsyncCore()` 方法将异步释放托管资源，因此不希望也同步释放这些资源。 因此，调用 `Dispose(false)` 而非 `Dispose(true)`。

## <a name="implement-the-async-dispose-pattern"></a>实现异步释放模式

所有非密封类都应被视为潜在的基类，因为它们可以被继承。 如果为任何潜在基类实现异步释放模式，则必须提供 `protected virtual ValueTask DisposeAsyncCore()` 方法。 下面是使用 <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 的异步释放模式的实现示例。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

前面的示例使用 <xref:System.Text.Json.Utf8JsonWriter>。 有关 `System.Text.Json` 的详细信息，请参阅[如何从 Newtonsoft.Json 迁移到 System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)。

## <a name="using-async-disposable"></a>使用异步释放

要正确使用实现 <xref:System.IAsyncDisposable> 接口的对象，请将 [await](../../csharp/language-reference/operators/await.md)和 [using](../../csharp/language-reference/keywords/using-statement.md) 关键字结合使用。 请考虑以下示例，其中 `ExampleAsyncDisposable` 类进行了实例化，然后包装在 `await using` 语句中。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> 使用 <xref:System.IAsyncDisposable> 接口的 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 扩展方法配置延续任务在其原始上下文或计划程序上的封送方式。 有关 `ConfigureAwait` 的详细信息，请参阅 [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/)。

对于不需要使用 `ConfigureAwait` 的情况，可以按如下所示简化 `await using` 语句：

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

此外，它还可以编写为使用 [using 声明](../../csharp/whats-new/csharp-8.md#using-declarations)的隐式范围。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>堆叠的 using

在创建和使用实现 <xref:System.IAsyncDisposable> 的多个对象的情况下，残存错误条件中堆叠的 `using` 语句可能会阻止调用 <xref:System.IAsyncDisposable.DisposeAsync>。 为了帮助防止潜在的问题，应避免堆叠，并遵循以下示例模式：

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a>请参阅

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
