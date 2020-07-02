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
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>如何：检索与 WebRequest 匹配的特定于协议的 WebResponse
此示例演示如何检索与 WebRequest 匹配的特定于协议的 WebResponse。  
  
## <a name="example"></a>示例  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
- 引用 System.Net 命名空间。  
  
## <a name="see-also"></a>请参阅

- [请求数据](requesting-data.md)
