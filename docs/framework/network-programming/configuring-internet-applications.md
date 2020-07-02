---
title: 配置 Internet 应用程序
description: 了解如何使用 <system.Net> 元素在 .NET Framework 中配置 Internet 应用程序。 本文包含示例代码。
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: 760a4ac7cec9abeabfc372c3be5bd3860a6fb03a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502634"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="7ea5b-104">配置 Internet 应用程序</span><span class="sxs-lookup"><span data-stu-id="7ea5b-104">Configuring Internet Applications</span></span>
<span data-ttu-id="7ea5b-105">[\<system.Net> 元素（网络设置）](../configure-apps/file-schema/network/system-net-element-network-settings.md)配置元素包含应用程序的网络配置信息。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-105">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="7ea5b-106">使用 [\<system.Net> 元素（网络设置）](../configure-apps/file-schema/network/system-net-element-network-settings.md)元素，可以设置代理服务器，设置连接管理参数，包括自定义应用程序内的身份验证和请求模块。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-106">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="7ea5b-107">[\<defaultProxy> 元素（网络设置）](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md)元素定义 `GlobalProxySelection` 类返回的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-107">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="7ea5b-108">任何没有自身 <xref:System.Net.HttpWebRequest.Proxy%2A> 属性的 <xref:System.Net.HttpWebRequest> 都设置为使用默认代理的特定值。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-108">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="7ea5b-109">除了设置代理地址外，还可以创建不使用代理的服务器地址列表，并指示不应将代理用于本地地址。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-109">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="7ea5b-110">请注意，Microsoft Internet Explorer 设置与配置设置相结合，并且后者具有优先级。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-110">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="7ea5b-111">以下示例将默认代理服务器地址设置为 `http://proxyserver`，指示不应将代理用于本地地址，并指定对位于 contoso.com 域中服务器的所有请求均应绕过该代理。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-111">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="7ea5b-112">使用 [\<connectionManagement> 元素（网络设置）](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)元素来配置可与特定服务器或其他所有服务器进行的持久连接数。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-112">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="7ea5b-113">下面的示例将应用程序配置为使用 2 个与服务器 `www.contoso.com` 的持久连接，4 个与 IP 地址为 192.168.1.2 的服务器的持久连接，以及 1 个与其他所有服务器的持久连接。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-113">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="7ea5b-114">自定义身份验证模块已配置 [\<authenticationModules> 元素（网络设置）](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)元素。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-114">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="7ea5b-115">自定义身份验证模块应实现 <xref:System.Net.IAuthenticationModule> 接口。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-115">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="7ea5b-116">下面的示例配置自定义身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-116">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="7ea5b-117">可以使用 [\<webRequestModules> 元素（网络设置）](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)元素将应用程序配置为使用自定义协议特定的模块，以请求 Internet 资源中的信息。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-117">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="7ea5b-118">指定的模块应实现 <xref:System.Net.IWebRequestCreate> 接口。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-118">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="7ea5b-119">可在配置文件中指定自定义模块来替代默认 HTTP、HTTPS 和文件请求模块，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="7ea5b-119">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ea5b-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ea5b-120">See also</span></span>

- [<span data-ttu-id="7ea5b-121">.NET Framework 中的网络编程</span><span class="sxs-lookup"><span data-stu-id="7ea5b-121">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="7ea5b-122">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="7ea5b-122">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="7ea5b-123">\<system.Net> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="7ea5b-123">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
