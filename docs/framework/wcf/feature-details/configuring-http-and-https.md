---
title: 配置 HTTP 和 HTTPS
description: 了解如何配置 HTTP/HTTPS 以允许 WCF 服务和客户端进行通信。 使用 Netsh.exe 配置 URL 注册和防火墙例外。
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: fbff78ff8e2c5c4fa73a56a3fdc15163596aa985
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245136"
---
# <a name="configuring-http-and-https"></a><span data-ttu-id="a654b-104">配置 HTTP 和 HTTPS</span><span class="sxs-lookup"><span data-stu-id="a654b-104">Configuring HTTP and HTTPS</span></span>

<span data-ttu-id="a654b-105">WCF 服务和客户端可以通过 HTTP 和 HTTPS 通信。</span><span class="sxs-lookup"><span data-stu-id="a654b-105">WCF services and clients can communicate over HTTP and HTTPS.</span></span> <span data-ttu-id="a654b-106">通过使用 Internet Information Services (IIS) 或命令行工具可以配置 HTTP/HTTPS 设置。</span><span class="sxs-lookup"><span data-stu-id="a654b-106">The HTTP/HTTPS settings are configured by using Internet Information Services (IIS) or through the use of a command-line tool.</span></span> <span data-ttu-id="a654b-107">当某个 WCF 服务承载于 IIS 之下时，可以在 IIS 中配置 HTTP 或 HTTPS 设置（使用 inetmgr.exe 工具）。</span><span class="sxs-lookup"><span data-stu-id="a654b-107">When a WCF service is hosted under IIS HTTP or HTTPS settings can be configured within IIS (using the inetmgr.exe tool).</span></span> <span data-ttu-id="a654b-108">如果 WCF 服务是自承载的，则可使用命令行工具配置 HTTP 或 HTTPS 设置。</span><span class="sxs-lookup"><span data-stu-id="a654b-108">If a WCF service is self-hosted, HTTP or HTTPS settings are configured by using a command-line tool.</span></span>

<span data-ttu-id="a654b-109">你至少需要为你的服务将使用的 URL 配置 URL 注册并添加防火墙例外。</span><span class="sxs-lookup"><span data-stu-id="a654b-109">At a minimum, you want to configure a URL registration and add a Firewall exception for the URL your service will be using.</span></span> <span data-ttu-id="a654b-110">可以通过 Netsh.exe 工具配置这些设置。</span><span class="sxs-lookup"><span data-stu-id="a654b-110">You can configure these settings with the Netsh.exe tool.</span></span>

## <a name="configuring-namespace-reservations"></a><span data-ttu-id="a654b-111">配置命名空间保留</span><span class="sxs-lookup"><span data-stu-id="a654b-111">Configuring namespace reservations</span></span>

<span data-ttu-id="a654b-112">命名空间预留将 HTTP URL 命名空间的一部分的权限分配给特定的用户组。</span><span class="sxs-lookup"><span data-stu-id="a654b-112">Namespace reservation assigns the rights for a portion of the HTTP URL namespace to a particular group of users.</span></span> <span data-ttu-id="a654b-113">预留提供给这些用户创建用于侦听命名空间的相应部分的服务的权限。</span><span class="sxs-lookup"><span data-stu-id="a654b-113">A reservation gives those users the right to create services that listen on that portion of the namespace.</span></span> <span data-ttu-id="a654b-114">保留是 URL 前缀，这意味着保留包含保留路径的所有子路径。</span><span class="sxs-lookup"><span data-stu-id="a654b-114">Reservations are URL prefixes, meaning that the reservation covers all subpaths of the reservation path.</span></span> <span data-ttu-id="a654b-115">命名空间预留允许以两种方式使用通配符。</span><span class="sxs-lookup"><span data-stu-id="a654b-115">Namespace reservations permit two ways to use wildcards.</span></span> <span data-ttu-id="a654b-116">HTTP 服务器 API 文档介绍了[涉及通配符的命名空间声明之间的解析顺序](/windows/desktop/Http/routing-incoming-requests)。</span><span class="sxs-lookup"><span data-stu-id="a654b-116">The HTTP Server API documentation describes the [order of resolution between namespace claims that involve wildcards](/windows/desktop/Http/routing-incoming-requests).</span></span>

<span data-ttu-id="a654b-117">运行的应用程序可以创建一个类似请求来添加命名空间注册。</span><span class="sxs-lookup"><span data-stu-id="a654b-117">A running application can create a similar request to add namespace registrations.</span></span> <span data-ttu-id="a654b-118">注册和预留会竞争命名空间的某些部分。</span><span class="sxs-lookup"><span data-stu-id="a654b-118">Registrations and reservations compete for portions of the namespace.</span></span> <span data-ttu-id="a654b-119">根据在[涉及通配符的命名空间声明之间的解析顺序，](/windows/desktop/Http/routing-incoming-requests)保留的顺序可能与注册的优先级不同。</span><span class="sxs-lookup"><span data-stu-id="a654b-119">A reservation may have precedence over a registration according to the order of resolution given in the [order of resolution between namespace claims that involve wildcards](/windows/desktop/Http/routing-incoming-requests).</span></span> <span data-ttu-id="a654b-120">在此情况下，预留会阻止运行的应用程序接收请求。</span><span class="sxs-lookup"><span data-stu-id="a654b-120">In this case, the reservation blocks the running application from receiving requests.</span></span>

<span data-ttu-id="a654b-121">下面的示例使用 Netsh.exe 工具：</span><span class="sxs-lookup"><span data-stu-id="a654b-121">The following example uses the Netsh.exe tool:</span></span>

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

<span data-ttu-id="a654b-122">此命令为 DOMAIN\user 帐户的指定 URL 命名空间添加 URL 保留项。</span><span class="sxs-lookup"><span data-stu-id="a654b-122">This command adds a URL reservation for the specified URL namespace for the DOMAIN\user account.</span></span> <span data-ttu-id="a654b-123">有关使用 netsh 命令的详细信息，请 `netsh http add urlacl /?` 在命令提示符下键入，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="a654b-123">For more information on using the netsh command, type `netsh http add urlacl /?` in a command-prompt and press Enter.</span></span>

## <a name="configuring-a-firewall-exception"></a><span data-ttu-id="a654b-124">配置防火墙例外</span><span class="sxs-lookup"><span data-stu-id="a654b-124">Configuring a firewall exception</span></span>

<span data-ttu-id="a654b-125">当自承载通过 HTTP 进行通信的 WCF 服务时，必须向防火墙配置添加一个例外，以允许使用特定 URL 的入站连接。</span><span class="sxs-lookup"><span data-stu-id="a654b-125">When self-hosting a WCF service that communicates over HTTP, an exception must be added to the firewall configuration to allow inbound connections using a particular URL.</span></span>

## <a name="configuring-ssl-certificates"></a><span data-ttu-id="a654b-126">配置 SSL 证书</span><span class="sxs-lookup"><span data-stu-id="a654b-126">Configuring SSL certificates</span></span>

<span data-ttu-id="a654b-127">安全套接字层 (SSL) 协议在客户端和服务器上使用证书来存储加密密钥。</span><span class="sxs-lookup"><span data-stu-id="a654b-127">The Secure Sockets Layer (SSL) protocol uses certificates on the client and server to store encryption keys.</span></span> <span data-ttu-id="a654b-128">在建立连接时，服务器会提供其 SSL 证书，以便客户端验证服务器标识。</span><span class="sxs-lookup"><span data-stu-id="a654b-128">The server provides its SSL certificate when a connection is made so that the client can verify the server identity.</span></span> <span data-ttu-id="a654b-129">服务器还可以从客户端请求证书以提供连接双方的相互身份验证。</span><span class="sxs-lookup"><span data-stu-id="a654b-129">The server can also request a certificate from the client to provide mutual authentication of both sides of the connection.</span></span>

<span data-ttu-id="a654b-130">证书将根据连接的 IP 地址和端口号存储在一个中央存储区中。</span><span class="sxs-lookup"><span data-stu-id="a654b-130">Certificates are stored in a centralized store according to the IP address and port number of the connection.</span></span> <span data-ttu-id="a654b-131">特殊的 IP 地址 0.0.0.0 可以与本地计算机的任何 IP 地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="a654b-131">The special IP address 0.0.0.0 matches any IP address for the local machine.</span></span> <span data-ttu-id="a654b-132">请注意，证书存储区不会基于路径来区分 Url。</span><span class="sxs-lookup"><span data-stu-id="a654b-132">Note that the certificate store doesn't distinguish URLs based on the path.</span></span> <span data-ttu-id="a654b-133">即使服务的 URL 中的路径不同，带有相同 IP 地址和端口组合的服务也必须共享证书。</span><span class="sxs-lookup"><span data-stu-id="a654b-133">Services with the same IP address and port combination must share certificates even if the path in the URL for the services is different.</span></span>

<span data-ttu-id="a654b-134">有关分步说明，请参阅[如何：使用 SSL 证书配置端口](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="a654b-134">For step-by-step instructions, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

## <a name="configuring-the-ip-listen-list"></a><span data-ttu-id="a654b-135">配置 IP 侦听列表</span><span class="sxs-lookup"><span data-stu-id="a654b-135">Configuring the IP Listen List</span></span>

<span data-ttu-id="a654b-136">在用户注册一个 URL 之后，HTTP 服务器 API 只绑定到一个 IP 地址和端口。</span><span class="sxs-lookup"><span data-stu-id="a654b-136">The HTTP Server API only binds to an IP address and port once a user registers a URL.</span></span> <span data-ttu-id="a654b-137">默认情况下，对于计算机的所有 IP 地址，HTTP 服务器 API 将绑定到所注册的 URL 中的端口。</span><span class="sxs-lookup"><span data-stu-id="a654b-137">By default, the HTTP Server API binds to the port in the URL for all of the IP addresses of the machine.</span></span> <span data-ttu-id="a654b-138">如果未使用 HTTP 服务器 API 的应用程序以前已绑定到该 IP 地址和端口的组合，则会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="a654b-138">A conflict arises if an application that doesn't use the HTTP Server API has previously bound to that combination of IP address and port.</span></span> <span data-ttu-id="a654b-139">IP 侦听列表允许 WCF 服务与使用端口的应用程序共存于计算机的某些 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a654b-139">The IP Listen List allows WCF services to coexist with applications that use a port for some of the IP addresses of the machine.</span></span> <span data-ttu-id="a654b-140">如果 IP 侦听列表包含任何项，则 HTTP 服务器 API 只绑定到该列表指定的那些 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a654b-140">If the IP Listen List contains any entries, the HTTP Server API only binds to those IP addresses that the list specifies.</span></span> <span data-ttu-id="a654b-141">修改 IP 侦听列表需要管理特权。</span><span class="sxs-lookup"><span data-stu-id="a654b-141">Modifying the IP Listen List requires administrative privileges.</span></span>

<span data-ttu-id="a654b-142">使用 netsh 工具修改 IP 侦听列表，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="a654b-142">Use the netsh tool to modify the IP Listen List, as shown in the following example:</span></span>

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a><span data-ttu-id="a654b-143">其他配置设置</span><span class="sxs-lookup"><span data-stu-id="a654b-143">Other configuration settings</span></span>

<span data-ttu-id="a654b-144">使用 <xref:System.ServiceModel.WSDualHttpBinding> 时，客户端连接使用与命名空间预留和 Windows 防火墙兼容的默认设置。</span><span class="sxs-lookup"><span data-stu-id="a654b-144">When using <xref:System.ServiceModel.WSDualHttpBinding>, the client connection uses defaults that are compatible with namespace reservations and the Windows firewall.</span></span> <span data-ttu-id="a654b-145">如果选择自定义双向连接的客户端基址，则还必须配置这些客户端上的 HTTP 设置以与新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="a654b-145">If you choose to customize the client base address of a dual connection, then you also must configure these HTTP settings on the client to match the new address.</span></span>

<span data-ttu-id="a654b-146">HTTP 服务器 API 具有一些无法通过 Httpcfg.exe 获得的高级配置设置。</span><span class="sxs-lookup"><span data-stu-id="a654b-146">The HTTP Server API has some advanced configuration settings that aren't available through HttpCfg.</span></span> <span data-ttu-id="a654b-147">这些设置保留在注册表中并应用于在使用 HTTP 服务器 API 的系统上运行的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="a654b-147">These settings are maintained in the registry and apply to all applications running on the systems that use the HTTP Server APIs.</span></span> <span data-ttu-id="a654b-148">有关这些设置的详细信息，请参阅[Http.sys IIS 的注册表设置](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows)。</span><span class="sxs-lookup"><span data-stu-id="a654b-148">For information about these settings, see [Http.sys registry settings for IIS](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows).</span></span> <span data-ttu-id="a654b-149">大多数用户不需要更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="a654b-149">Most users don't need to change these settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="a654b-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="a654b-150">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- [<span data-ttu-id="a654b-151">如何：使用 SSL 证书配置端口</span><span class="sxs-lookup"><span data-stu-id="a654b-151">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
