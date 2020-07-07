---
title: 将委托作为回调方法进行封送
description: 了解如何将委托作为回调方法进行封送。 请参阅如何将委托传递给需要函数指针的非托管函数的示例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
ms.openlocfilehash: bf9ef3b9d48c0869dcc96820c3a2fb6fb608479e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618943"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="85634-104">将委托作为回调方法进行封送</span><span class="sxs-lookup"><span data-stu-id="85634-104">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="85634-105">此示例演示如何将委托传递给需要函数指针的非托管函数。</span><span class="sxs-lookup"><span data-stu-id="85634-105">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="85634-106">委托是可以容纳方法引用的类，等效于类型安全函数指针或回调函数。</span><span class="sxs-lookup"><span data-stu-id="85634-106">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="85634-107">在调用内使用委托时，公共语言运行时防止在该调用的持续时间内对委托执行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="85634-107">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="85634-108">但是，如果非托管函数存储了该委托，以便在调用完成后使用，则必须手动防止垃圾回收，直到非托管函数结束对该委托的使用为止。</span><span class="sxs-lookup"><span data-stu-id="85634-108">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="85634-109">有关详细信息，请参阅 [HandleRef 示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100))和 [GCHandle 示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="85634-109">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="85634-110">回调示例使用以下非托管函数（与其原始函数声明一同显示）：</span><span class="sxs-lookup"><span data-stu-id="85634-110">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="85634-111">`TestCallBack` 从 PinvokeLib.dll 导出。</span><span class="sxs-lookup"><span data-stu-id="85634-111">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="85634-112">`TestCallBack2` 从 PinvokeLib.dll 导出。</span><span class="sxs-lookup"><span data-stu-id="85634-112">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="85634-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是一种自定义的非托管库，包含上述函数的实现。</span><span class="sxs-lookup"><span data-stu-id="85634-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="85634-114">在此示例中，`NativeMethods` 类包含 `TestCallBack` 和 `TestCallBack2` 方法的托管原型。</span><span class="sxs-lookup"><span data-stu-id="85634-114">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="85634-115">这两种方法都作为参数将委托传递给回调函数。</span><span class="sxs-lookup"><span data-stu-id="85634-115">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="85634-116">委托的签名必须匹配它引用的方法的签名。</span><span class="sxs-lookup"><span data-stu-id="85634-116">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="85634-117">例如，`FPtr` 和 `FPtr2`委托的签名与 `DoSomething` 和 `DoSomething2` 方法相同。</span><span class="sxs-lookup"><span data-stu-id="85634-117">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="85634-118">声明原型</span><span class="sxs-lookup"><span data-stu-id="85634-118">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="85634-119">调用函数</span><span class="sxs-lookup"><span data-stu-id="85634-119">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="85634-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="85634-120">See also</span></span>

- <span data-ttu-id="85634-121">[其他封送处理示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="85634-121">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="85634-122">平台调用数据类型</span><span class="sxs-lookup"><span data-stu-id="85634-122">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="85634-123">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="85634-123">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
