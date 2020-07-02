---
title: 自动代理检测
description: 了解自动代理检测，其中系统标识 Web 代理服务器并将其用于代表客户端发送请求。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
ms.openlocfilehash: dbd5d7fa671ae5ec3b7dc00205f0c9d8381bb3ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502687"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="4cc74-103">自动代理检测</span><span class="sxs-lookup"><span data-stu-id="4cc74-103">Automatic Proxy Detection</span></span>
<span data-ttu-id="4cc74-104">自动代理检测是一个进程，系统使用该进程来标识 Web 代理服务器，并用于代表客户端发送请求。</span><span class="sxs-lookup"><span data-stu-id="4cc74-104">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="4cc74-105">此功能也称为 Web 代理自动发现 (WPAD)。</span><span class="sxs-lookup"><span data-stu-id="4cc74-105">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="4cc74-106">启用自动代理检测后，系统会尝试查找代理配置脚本，该脚本负责返回一组可用于请求的代理。</span><span class="sxs-lookup"><span data-stu-id="4cc74-106">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="4cc74-107">如果找到了代理配置脚本，则会在针对使用 <xref:System.Net.WebProxy> 实例的请求获取代理信息、请求流或响应时，在本地计算机上下载、编译并运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="4cc74-107">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="4cc74-108">自动代理检测由 <xref:System.Net.WebProxy> 类执行，且可采用请求级设置、配置文件中的设置和通过 Internet Explorer“局域网(LAN)”对话框指定的设置。</span><span class="sxs-lookup"><span data-stu-id="4cc74-108">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cc74-109">可通过以下方式显示 Internet Explorer 的“局域网(LAN)设置”对话框：在 Internet Explorer 主菜单中选择“工具”，然后选择“Internet 选项”  。</span><span class="sxs-lookup"><span data-stu-id="4cc74-109">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="4cc74-110">接下来，选择“连接”选项卡，然后单击“LAN 设置” 。</span><span class="sxs-lookup"><span data-stu-id="4cc74-110">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="4cc74-111">启用自动代理检测后，<xref:System.Net.WebProxy> 类会尝试按如下方式找到代理配置脚本：</span><span class="sxs-lookup"><span data-stu-id="4cc74-111">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="4cc74-112">WinINet `InternetQueryOption` 函数用于查找 Internet Explorer 最近检测到的代理配置脚本。</span><span class="sxs-lookup"><span data-stu-id="4cc74-112">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="4cc74-113">如果找不到该脚本，<xref:System.Net.WebProxy> 类将使用动态主机配置协议 (DHCP) 查找该脚本。</span><span class="sxs-lookup"><span data-stu-id="4cc74-113">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="4cc74-114">DHCP 服务器可以采用脚本的位置（主机名）或脚本的完整 URL 进行响应。</span><span class="sxs-lookup"><span data-stu-id="4cc74-114">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="4cc74-115">如果 DHCP 未标识 WPAD 主机，则查询 DNS 以找到 WPAD 作为其名称或别名的主机。</span><span class="sxs-lookup"><span data-stu-id="4cc74-115">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="4cc74-116">如果未标识该主机，并且代理配置脚本的位置由 Internet Explorer LAN 设置或配置文件指定，则使用此位置。</span><span class="sxs-lookup"><span data-stu-id="4cc74-116">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cc74-117">作为 NT 服务或 ASP.NET 的一部分运行的应用程序使用调用用户的 Internet Explorer 代理服务器设置（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="4cc74-117">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="4cc74-118">这些设置可能并非对所有服务应用程序都可用。</span><span class="sxs-lookup"><span data-stu-id="4cc74-118">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="4cc74-119">代理基于每个 connectoid 进行配置。</span><span class="sxs-lookup"><span data-stu-id="4cc74-119">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="4cc74-120">connectoid 是网络连接对话框中的一项，可以是物理网络设备（调制解调器或以太网卡）或虚拟接口（例如，通过网络设备运行的 VPN 连接）。</span><span class="sxs-lookup"><span data-stu-id="4cc74-120">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="4cc74-121">如果 connectoid 发生更改（例如，无线连接更改了访问点，或启用了 VPN），则将再次运行代理检测算法。</span><span class="sxs-lookup"><span data-stu-id="4cc74-121">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="4cc74-122">默认情况下，Internet Explorer 代理设置用于检测此代理。</span><span class="sxs-lookup"><span data-stu-id="4cc74-122">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="4cc74-123">如果应用程序基于非交互式帐户运行（没有用于配置 IE 代理设置的简便方法），或要使用不同于 IE 设置的代理设置，则可以通过创建定义了 [\<defaultProxy> 元素（网络设置）](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md)和 [\<proxy> 元素（网络设置）](../configure-apps/file-schema/network/proxy-element-network-settings.md)元素的配置文件，对代理进行配置。</span><span class="sxs-lookup"><span data-stu-id="4cc74-123">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="4cc74-124">对于所创建的请求，可通过将空 <xref:System.Net.WebRequest.Proxy%2A> 用于该请求，禁用请求级别的自动代理检测，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="4cc74-124">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub
```  
  
 <span data-ttu-id="4cc74-125">没有代理的请求将使用应用程序域的默认代理（通过 <xref:System.Net.WebRequest.DefaultWebProxy%2A> 属性提供）。</span><span class="sxs-lookup"><span data-stu-id="4cc74-125">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc74-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="4cc74-126">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="4cc74-127">\<system.Net> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4cc74-127">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
