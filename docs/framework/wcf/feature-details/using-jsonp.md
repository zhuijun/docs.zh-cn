---
title: 使用 JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 82290319b5d8b58708f0b2ebf40522ee76127b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594954"
---
# <a name="using-jsonp"></a><span data-ttu-id="00201-102">使用 JSONP</span><span class="sxs-lookup"><span data-stu-id="00201-102">Using JSONP</span></span>

<span data-ttu-id="00201-103">JSON Padding (JSONP) 是一种在 Web 浏览器中启用跨站点脚本支持的机制。</span><span class="sxs-lookup"><span data-stu-id="00201-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="00201-104">JSONP 是围绕 Web 浏览器的功能而设计的，用于从检索当前所加载文档的站点之外的站点加载脚本。</span><span class="sxs-lookup"><span data-stu-id="00201-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="00201-105">该机制的工作原理是使用用户定义的回调函数名来填充 JSON 负载，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="00201-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="00201-106">在上例中，JSON 负载 `{"a" = \\"b\\"}` 包装在函数调用 `callback` 中。</span><span class="sxs-lookup"><span data-stu-id="00201-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="00201-107">必须已在当前网页中定义回调函数。</span><span class="sxs-lookup"><span data-stu-id="00201-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="00201-108">JSONP 响应的内容类型为 `application/javascript` 。</span><span class="sxs-lookup"><span data-stu-id="00201-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="00201-109">JSONP 不会自动启用。</span><span class="sxs-lookup"><span data-stu-id="00201-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="00201-110">若要启用 JSONP，请在某个 HTTP 标准终结点（`javascriptCallbackEnabled` 或 `true`）上将 <xref:System.ServiceModel.Description.WebHttpEndpoint> 特性设置为 <xref:System.ServiceModel.Description.WebScriptEndpoint>，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="00201-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="00201-111">可以在称为回调的查询变量中指定回调函数的名称，如下面的 URL 中所示。</span><span class="sxs-lookup"><span data-stu-id="00201-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="00201-112">调用时，该服务将发送如下响应。</span><span class="sxs-lookup"><span data-stu-id="00201-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="00201-113">也可以通过对服务类应用 <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> 来指定回调函数名称，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="00201-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

<span data-ttu-id="00201-114">对于上面显示的服务，将发出如下请求。</span><span class="sxs-lookup"><span data-stu-id="00201-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="00201-115">调用时，该服务通过以下内容进行响应。</span><span class="sxs-lookup"><span data-stu-id="00201-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="00201-116">HTTP 状态代码</span><span class="sxs-lookup"><span data-stu-id="00201-116">HTTP Status Codes</span></span>

<span data-ttu-id="00201-117">具有 200 以外的 HTTP 状态代码的 JSONP 响应包括另一个参数，该参数使用 HTTP 状态代码的数字表示形式，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="00201-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="00201-118">验证</span><span class="sxs-lookup"><span data-stu-id="00201-118">Validations</span></span>

<span data-ttu-id="00201-119">启用 JSONP 后将执行以下验证：</span><span class="sxs-lookup"><span data-stu-id="00201-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="00201-120">如果启用了 `javascriptCallback`，请求中存在回调查询字符串参数，且将响应格式设置为 JSON，WCF 基础结构将引发异常。</span><span class="sxs-lookup"><span data-stu-id="00201-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="00201-121">如果请求包含回调查询字符串参数，但操作不是 HTTP GET，则将忽略回调参数。</span><span class="sxs-lookup"><span data-stu-id="00201-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="00201-122">如果回调名称为 `null` 或空字符串，则响应的格式不会设置为 JSONP。</span><span class="sxs-lookup"><span data-stu-id="00201-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="00201-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00201-123">See also</span></span>

- [<span data-ttu-id="00201-124">WCF Web HTTP 编程模型概述</span><span class="sxs-lookup"><span data-stu-id="00201-124">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
