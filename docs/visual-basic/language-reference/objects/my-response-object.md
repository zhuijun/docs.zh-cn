---
title: My.Response 对象
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 53e8012e762c46e6efbd8e9d2191aa62d58aa42b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870037"
---
# <a name="myresponse-object"></a><span data-ttu-id="76ab4-102">My.Response 对象</span><span class="sxs-lookup"><span data-stu-id="76ab4-102">My.Response Object</span></span>

<span data-ttu-id="76ab4-103">获取 <xref:System.Web.HttpResponse> 与关联的对象 <xref:System.Web.UI.Page> 。</span><span class="sxs-lookup"><span data-stu-id="76ab4-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="76ab4-104">使用此对象，可以将 HTTP 响应数据发送到客户端，并包含此响应的相关信息。</span><span class="sxs-lookup"><span data-stu-id="76ab4-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76ab4-105">备注</span><span class="sxs-lookup"><span data-stu-id="76ab4-105">Remarks</span></span>  

 <span data-ttu-id="76ab4-106">`My.Response`对象包含 <xref:System.Web.HttpResponse> 与页关联的当前对象。</span><span class="sxs-lookup"><span data-stu-id="76ab4-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="76ab4-107">`My.Response`对象仅适用于 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="76ab4-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ab4-108">示例</span><span class="sxs-lookup"><span data-stu-id="76ab4-108">Example</span></span>  

 <span data-ttu-id="76ab4-109">下面的示例从对象获取标头集合 `My.Request` ，并使用 `My.Response` 对象将其写入到 ASP.NET 页。</span><span class="sxs-lookup"><span data-stu-id="76ab4-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="76ab4-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76ab4-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="76ab4-111">My.Request 对象</span><span class="sxs-lookup"><span data-stu-id="76ab4-111">My.Request Object</span></span>](my-request-object.md)
