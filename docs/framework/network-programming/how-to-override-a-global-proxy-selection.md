---
title: 如何：重写全局代理选择
description: 按照此示例，通过将 WebRequest 发送到 URL 来替代全局代理选择，这将使用代理服务器来替代该选择。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 91f64775e2f401be9b740fe9e4c41e1087eb9617
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502504"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="02b0c-103">如何：重写全局代理选择</span><span class="sxs-lookup"><span data-stu-id="02b0c-103">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="02b0c-104">此示例将 WebRequest 发送到 `www.contoso.com`，其在端口 80 上使用名为 `alternateproxy` 的代理服务器替代全局代理选择。</span><span class="sxs-lookup"><span data-stu-id="02b0c-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02b0c-105">示例</span><span class="sxs-lookup"><span data-stu-id="02b0c-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02b0c-106">编译代码</span><span class="sxs-lookup"><span data-stu-id="02b0c-106">Compiling the Code</span></span>  
 <span data-ttu-id="02b0c-107">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="02b0c-107">This example requires:</span></span>  
  
- <span data-ttu-id="02b0c-108">System.Net 命名空间的 [`using` 指令](../../csharp/language-reference/keywords/using-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="02b0c-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b0c-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="02b0c-109">See also</span></span>

- [<span data-ttu-id="02b0c-110">使用应用程序协议</span><span class="sxs-lookup"><span data-stu-id="02b0c-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="02b0c-111">通过代理访问 Internet</span><span class="sxs-lookup"><span data-stu-id="02b0c-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
