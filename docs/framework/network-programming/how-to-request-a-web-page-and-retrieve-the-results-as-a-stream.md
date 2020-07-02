---
title: 如何：请求网页并以数据流的形式检索结果
description: 此示例演示如何请求网页并在 .NET Framework 的流中检索结果。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: bd57f9af6be29c783d044e785ebb36aaa8592df2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502478"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="22b8f-103">如何：请求网页并以数据流的形式检索结果</span><span class="sxs-lookup"><span data-stu-id="22b8f-103">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="22b8f-104">此示例演示如何请求 Web 页并在流中检索结果。</span><span class="sxs-lookup"><span data-stu-id="22b8f-104">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="22b8f-105">示例</span><span class="sxs-lookup"><span data-stu-id="22b8f-105">Example</span></span>

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a><span data-ttu-id="22b8f-106">编译代码</span><span class="sxs-lookup"><span data-stu-id="22b8f-106">Compiling the Code</span></span>

 <span data-ttu-id="22b8f-107">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="22b8f-107">This example requires:</span></span>

- <span data-ttu-id="22b8f-108">对 <xref:System.IO> 和 <xref:System.Net> 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="22b8f-108">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="22b8f-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="22b8f-109">See also</span></span>

- [<span data-ttu-id="22b8f-110">请求数据</span><span class="sxs-lookup"><span data-stu-id="22b8f-110">Requesting Data</span></span>](requesting-data.md)
