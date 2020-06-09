---
title: 如何：将支持 AJAX 的 ASP.NET Web 服务迁移到 WCF
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6f356f47922945218e02271371d9ddea36ecc5a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597002"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="d8bcd-102">如何：将支持 AJAX 的 ASP.NET Web 服务迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="d8bcd-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="d8bcd-103">本主题概述将基本 ASP.NET AJAX 服务迁移到等效的启用 AJAX Windows Communication Foundation （WCF）服务的过程。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="d8bcd-104">它演示如何创建 ASP.NET AJAX 服务的功能等效的 WCF 版本。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="d8bcd-105">然后，可以并行使用这两个服务，或者可以使用 WCF 服务来替换 ASP.NET AJAX 服务。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="d8bcd-106">将现有的 ASP.NET AJAX 服务迁移到 WCF AJAX 服务可提供以下优势：</span><span class="sxs-lookup"><span data-stu-id="d8bcd-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="d8bcd-107">只需最少的额外配置，即可将 AJAX 服务公开为 SOAP 服务。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="d8bcd-108">可从 WCF 功能（如跟踪等）中受益。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="d8bcd-109">以下过程假定你使用的是 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="d8bcd-110">从本主题概述的过程中得到的代码将在过程后面的示例中提供。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="d8bcd-111">有关通过启用 AJAX 的终结点公开 WCF 服务的详细信息，请参阅[如何：使用配置添加 ASP.NET AJAX 终结点](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)主题。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="d8bcd-112">创建并测试 ASP.NET Web 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="d8bcd-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="d8bcd-113">打开 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="d8bcd-114">从 "**文件**" 菜单中依次选择 "**新建**"、"**项目**"、" **Web**"，然后选择 " **ASP.NET Web 服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="d8bcd-115">将项目命名为 `ASPHello` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="d8bcd-116">在 Service1.asmx.cs 文件中，取消对包含 `System.Web.Script.Services.ScriptService]` 的行的注释，以便为此服务启用 AJAX。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="d8bcd-117">在 "**生成**" 菜单中，选择 "**生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="d8bcd-118">在“调试”\*\*\*\* 菜单中，选择“启动但不调试”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="d8bcd-119">在生成的网页上，选择 `HelloWorld` 操作。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="d8bcd-120">单击 "测试" 页上的 "**调用**" 按钮 `HelloWorld` 。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="d8bcd-121">您应收到以下 XML 响应。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="d8bcd-122">此响应可确认您现在已拥有一项能正常运行的 ASP.NET AJAX 服务。具体而言，该服务现在已在 Service1.asmx/HelloWorld 处公开了一个响应 HTTP POST 请求并返回 XML 的终结点。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="d8bcd-123">现在，你已准备好将此服务转换为使用 WCF AJAX 服务。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="d8bcd-124">创建等效的 WCF AJAX 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="d8bcd-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="d8bcd-125">右键单击 " **ASPHello** " 项目，然后依次选择 "**添加**"、"**新建项**" 和 "**启用 AJAX 的 WCF 服务**"。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="d8bcd-126">为服务命名 `WCFHello` ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="d8bcd-127">打开 WCFHello.svc.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="d8bcd-128">从 Service1.asmx.cs 复制操作的以下实现 `HelloWorld` 。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="d8bcd-129">将操作的复制实现粘贴到 `HelloWorld` WCFHello.svc.cs 文件中以替代以下代码。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="d8bcd-130">将的 `Namespace` 属性指定 <xref:System.ServiceModel.ServiceContractAttribute> 为 `WCFHello` 。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="d8bcd-131">将添加 <xref:System.ServiceModel.Web.WebInvokeAttribute> 到 `HelloWorld` 操作，并将 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> 属性设置为返回 <xref:System.ServiceModel.Web.WebMessageFormat.Xml> 。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="d8bcd-132">请注意，如果未设置此属性，则默认返回类型为 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="d8bcd-133">在 "**生成**" 菜单中，选择 "**生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="d8bcd-134">打开 Wcfhello.svc 文件，并从 "**调试**" 菜单中选择 "**启动（不调试**）"。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="d8bcd-135">现在，服务在中公开一个终结点 `WCFHello.svc/HelloWorld` ，该终结点响应 HTTP POST 请求。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="d8bcd-136">HTTP POST 请求不能从浏览器进行测试，但终结点会返回以下 XML。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="d8bcd-137">`WCFHello.svc/HelloWorld`和 `Service1.aspx/HelloWorld` 端点现在功能等效。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="d8bcd-138">示例</span><span class="sxs-lookup"><span data-stu-id="d8bcd-138">Example</span></span>
 <span data-ttu-id="d8bcd-139">从本主题概述的过程中得到的代码将在下面的示例中提供。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 <span data-ttu-id="d8bcd-140"><xref:System.Xml.XmlDocument> 不支持 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 类型，因为此类型不能被 <xref:System.Xml.Serialization.XmlSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d8bcd-141">可以改用 <xref:System.Xml.Linq.XDocument> 类型或序列化 <xref:System.Xml.XmlDocument.DocumentElement%2A>。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="d8bcd-142">如果要将 .ASMX Web 服务并行升级并迁移到 WCF 服务，请避免将两个类型映射到客户端上的同一名称。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="d8bcd-143">如果 <xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.ServiceModel.ServiceContractAttribute> 中使用了同一类型，则这将导致序列化程序中出现异常：</span><span class="sxs-lookup"><span data-stu-id="d8bcd-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="d8bcd-144">如果首先添加 WCF 服务，则对该方法调用方法会导致中出现异常， <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> 因为代理中顺序的 WCF 样式定义优先。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="d8bcd-145">如果首先添加了 .ASMX Web 服务，则对 WCF 服务调用方法将导致中出现异常， <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 因为代理中顺序的 Web 服务样式定义优先。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="d8bcd-146"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 和 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 在行为上存在很大差异。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="d8bcd-147">例如，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 将字典表示为键/值对的数组，而 ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> 则将字典表示为实际的 JSON 对象。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="d8bcd-148">因此，下面是用 ASP.NET AJAX 表示的字典。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="d8bcd-149">在下面的列表中：此字典用 JSON 对象表示：</span><span class="sxs-lookup"><span data-stu-id="d8bcd-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="d8bcd-150"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 将其表示为 [{"Key":"one","Value":1},{"Key":"two","Value":2}]</span><span class="sxs-lookup"><span data-stu-id="d8bcd-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="d8bcd-151">ASP.NET AJAX {"one"：1，"两个"： 2}<xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="d8bcd-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="d8bcd-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 可以处理其中的键类型不是字符串的词典，而 <xref:System.Web.Script.Serialization.JavaScriptSerializer> 则无法处理，在这一方面前者的功能更为强大。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="d8bcd-153">但后者与 JSON 的兼容性更好。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="d8bcd-154">下表汇总了这些序列化程序之间的重大差异。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="d8bcd-155">差异类别</span><span class="sxs-lookup"><span data-stu-id="d8bcd-155">Category of Differences</span></span>|<span data-ttu-id="d8bcd-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="d8bcd-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="d8bcd-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="d8bcd-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="d8bcd-158">将空缓冲区（新 byte[0]）反序列化为 <xref:System.Object>（或 <xref:System.Uri>，或某些其他类）。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="d8bcd-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="d8bcd-159">SerializationException</span></span>|<span data-ttu-id="d8bcd-160">Null</span><span class="sxs-lookup"><span data-stu-id="d8bcd-160">null</span></span>|
|<span data-ttu-id="d8bcd-161"><xref:System.DBNull.Value> 的序列化</span><span class="sxs-lookup"><span data-stu-id="d8bcd-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="d8bcd-162">{}（或 {"__type"： "#System"}）</span><span class="sxs-lookup"><span data-stu-id="d8bcd-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="d8bcd-163">Null</span><span class="sxs-lookup"><span data-stu-id="d8bcd-163">Null</span></span>|
|<span data-ttu-id="d8bcd-164">[Serializable] 类型的私有成员的序列化。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="d8bcd-165">已序列化</span><span class="sxs-lookup"><span data-stu-id="d8bcd-165">serialized</span></span>|<span data-ttu-id="d8bcd-166">未序列化</span><span class="sxs-lookup"><span data-stu-id="d8bcd-166">not serialized</span></span>|
|<span data-ttu-id="d8bcd-167"><xref:System.Runtime.Serialization.ISerializable> 类型的公共属性的序列化。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="d8bcd-168">未序列化</span><span class="sxs-lookup"><span data-stu-id="d8bcd-168">not serialized</span></span>|<span data-ttu-id="d8bcd-169">已序列化</span><span class="sxs-lookup"><span data-stu-id="d8bcd-169">serialized</span></span>|
|<span data-ttu-id="d8bcd-170">JSON 的“扩展”</span><span class="sxs-lookup"><span data-stu-id="d8bcd-170">"Extensions" of JSON</span></span>|<span data-ttu-id="d8bcd-171">遵循 JSON 规范，该规范要求为对象成员名称加上引号 ({"a":"hello"})。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="d8bcd-172">支持不带引号的对象成员名称 ({a:"hello"})。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="d8bcd-173"><xref:System.DateTime> 协调世界时 (UTC)</span><span class="sxs-lookup"><span data-stu-id="d8bcd-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="d8bcd-174">不支持格式 " \\ /Date （123456789U） \\ /" 或 " \\ /Date \\ （\d + （U&#124; （ \\ + \\ -[\d {4} ]））？ \\ ） \\ \\/)".</span><span class="sxs-lookup"><span data-stu-id="d8bcd-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="d8bcd-175">支持格式 " \\ /Date （123456789U） \\ /" 和 " \\ /Date \\ （\d + （U&#124; （ \\ + \\ -[\d {4} ]））？ \\ ） \\ \\/） "为 DateTime 值。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="d8bcd-176">词典的表示形式</span><span class="sxs-lookup"><span data-stu-id="d8bcd-176">Representation of dictionaries</span></span>|<span data-ttu-id="d8bcd-177">KeyValuePair 的数组 \<K,V> ，处理不是字符串的键类型。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="d8bcd-178">作为实际的 JSON 对象 - 但仅处理是字符串的键类型。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="d8bcd-179">转义符</span><span class="sxs-lookup"><span data-stu-id="d8bcd-179">Escaped characters</span></span>|<span data-ttu-id="d8bcd-180">始终应带有转义正斜杠 (/)；切勿使用非转义的无效 JSON 字符，例如“\n”。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="d8bcd-181">对于 DateTime 值，带有转义正斜杠 (/)。</span><span class="sxs-lookup"><span data-stu-id="d8bcd-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d8bcd-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8bcd-182">See also</span></span>

- [<span data-ttu-id="d8bcd-183">如何：使用配置来添加 ASP.NET AJAX 终结点</span><span class="sxs-lookup"><span data-stu-id="d8bcd-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
