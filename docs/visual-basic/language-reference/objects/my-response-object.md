---
title: My.Response 对象
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372450"
---
# <a name="myresponse-object"></a><span data-ttu-id="600f3-102">My.Response 对象</span><span class="sxs-lookup"><span data-stu-id="600f3-102">My.Response Object</span></span>
<span data-ttu-id="600f3-103">获取 <xref:System.Web.HttpResponse> 与关联的对象 <xref:System.Web.UI.Page> 。</span><span class="sxs-lookup"><span data-stu-id="600f3-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="600f3-104">使用此对象，可以将 HTTP 响应数据发送到客户端，并包含此响应的相关信息。</span><span class="sxs-lookup"><span data-stu-id="600f3-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="600f3-105">备注</span><span class="sxs-lookup"><span data-stu-id="600f3-105">Remarks</span></span>  
 <span data-ttu-id="600f3-106">`My.Response`对象包含 <xref:System.Web.HttpResponse> 与页关联的当前对象。</span><span class="sxs-lookup"><span data-stu-id="600f3-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="600f3-107">`My.Response`对象仅适用于 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="600f3-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="600f3-108">示例</span><span class="sxs-lookup"><span data-stu-id="600f3-108">Example</span></span>  
 <span data-ttu-id="600f3-109">下面的示例从对象获取标头集合 `My.Request` ，并使用 `My.Response` 对象将其写入到 ASP.NET 页。</span><span class="sxs-lookup"><span data-stu-id="600f3-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="600f3-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="600f3-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="600f3-111">My.Request 对象</span><span class="sxs-lookup"><span data-stu-id="600f3-111">My.Request Object</span></span>](my-request-object.md)
