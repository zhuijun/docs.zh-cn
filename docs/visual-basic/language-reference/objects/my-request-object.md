---
title: My.Request 对象
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 38f510e2a3958761b902f37760069aa8d595ea8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372422"
---
# <a name="myrequest-object"></a><span data-ttu-id="04608-102">My.Request 对象</span><span class="sxs-lookup"><span data-stu-id="04608-102">My.Request Object</span></span>
<span data-ttu-id="04608-103">获取所请求的页面的 <xref:System.Web.HttpRequest> 对象。</span><span class="sxs-lookup"><span data-stu-id="04608-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04608-104">备注</span><span class="sxs-lookup"><span data-stu-id="04608-104">Remarks</span></span>  
 <span data-ttu-id="04608-105">`My.Request` 对象包含当前 HTTP 请求的相关信息。</span><span class="sxs-lookup"><span data-stu-id="04608-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="04608-106">`My.Request` 对象仅适用于 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="04608-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04608-107">示例</span><span class="sxs-lookup"><span data-stu-id="04608-107">Example</span></span>  
 <span data-ttu-id="04608-108">下面的示例从对象获取标头集合 `My.Request` ，并使用 `My.Response` 对象将其写入到 ASP.NET 页。</span><span class="sxs-lookup"><span data-stu-id="04608-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="04608-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04608-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="04608-110">My.Response 对象</span><span class="sxs-lookup"><span data-stu-id="04608-110">My.Response Object</span></span>](my-response-object.md)
