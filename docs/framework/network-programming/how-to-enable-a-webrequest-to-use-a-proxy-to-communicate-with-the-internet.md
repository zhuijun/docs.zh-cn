---
title: 如何：使 WebRequest 能够使用代理以与 Internet 通信
description: 了解如何创建全局代理实例，使任何 WebRequest 可以在 .NET Framework 中使用代理与 Internet 通信。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502530"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="bd9d3-103">如何：使 WebRequest 能够使用代理以与 Internet 通信</span><span class="sxs-lookup"><span data-stu-id="bd9d3-103">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="bd9d3-104">此示例将创建一个全局代理实例，该实例将启用任何 <xref:System.Net.WebRequest> 以使用代理与 Internet 进行通信。</span><span class="sxs-lookup"><span data-stu-id="bd9d3-104">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="bd9d3-105">该示例假定代理服务器名为 `webproxy`，且在端口 80（标准 HTTP 端口）上进行通信。</span><span class="sxs-lookup"><span data-stu-id="bd9d3-105">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="bd9d3-106">示例</span><span class="sxs-lookup"><span data-stu-id="bd9d3-106">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="bd9d3-107">编译代码</span><span class="sxs-lookup"><span data-stu-id="bd9d3-107">Compiling the Code</span></span>

<span data-ttu-id="bd9d3-108">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="bd9d3-108">This example requires:</span></span>

- <span data-ttu-id="bd9d3-109">System.Net 命名空间的 C# [`using` 指令](../../csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="bd9d3-109">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="bd9d3-110">System.Net 命名空间的 Visual Basic [`Imports` 语句](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="bd9d3-110">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd9d3-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="bd9d3-111">See also</span></span>

- [<span data-ttu-id="bd9d3-112">使用应用程序协议</span><span class="sxs-lookup"><span data-stu-id="bd9d3-112">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="bd9d3-113">通过代理访问 Internet</span><span class="sxs-lookup"><span data-stu-id="bd9d3-113">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
