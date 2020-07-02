---
title: 如何：检索与 WebRequest 匹配的特定于协议的 WebResponse
description: 了解如何检索与 .NET Framework 中的 WebRequest 匹配的特定于协议的 WebResponse。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 15b1912a7bd951df7f3c14eb96251c2bdf237b4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502452"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="0374a-103">如何：检索与 WebRequest 匹配的特定于协议的 WebResponse</span><span class="sxs-lookup"><span data-stu-id="0374a-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="0374a-104">此示例演示如何检索与 WebRequest 匹配的特定于协议的 WebResponse。</span><span class="sxs-lookup"><span data-stu-id="0374a-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0374a-105">示例</span><span class="sxs-lookup"><span data-stu-id="0374a-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0374a-106">编译代码</span><span class="sxs-lookup"><span data-stu-id="0374a-106">Compiling the Code</span></span>  
 <span data-ttu-id="0374a-107">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="0374a-107">This example requires:</span></span>  
  
- <span data-ttu-id="0374a-108">引用 System.Net 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0374a-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0374a-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="0374a-109">See also</span></span>

- [<span data-ttu-id="0374a-110">请求数据</span><span class="sxs-lookup"><span data-stu-id="0374a-110">Requesting Data</span></span>](requesting-data.md)
