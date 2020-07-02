---
title: Web 和套接字权限
description: 了解 WebPermission 和 SocketPermission 类如何为在 .NET Framework 中使用 System.Net 命名空间提供 Internet 安全性。
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: 08ae360e8097f7281631da2a3f9846994dfbf5b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501893"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="1f5b8-103">Web 和套接字权限</span><span class="sxs-lookup"><span data-stu-id="1f5b8-103">Web and Socket Permissions</span></span>
<span data-ttu-id="1f5b8-104"><xref:System.Net.WebPermission> 和 <xref:System.Net.SocketPermission> 类为使用 <xref:System.Net> 命名空间的应用程序提供网络安全性。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-104">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="1f5b8-105">WebPermission 类控制应用程序从 URI 请求数据或向 Internet 提供 URI 的权限。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-105">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="1f5b8-106">SocketPermission 类控制应用程序使用 <xref:System.Net.Sockets.Socket> 在本地端口接受数据或使用传输协议连接其他地址的远程设备的权限（基于主机、端口号和套接字的传输协议）。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-106">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="1f5b8-107">权限类的选择取决于应用程序的类型。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-107">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="1f5b8-108">使用 <xref:System.Net.WebRequest> 的应用程序及其子代应使用 WebPermission 类来管理权限。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-108">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="1f5b8-109">使用套接字级别访问权限的应用程序及其子代应使用 SocketPermission 类来管理权限。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-109">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="1f5b8-110">WebPermission 和 SocketPermission 定义两种权限：接受和连接。 </span><span class="sxs-lookup"><span data-stu-id="1f5b8-110">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="1f5b8-111">“接受”授予应用程序应答来自其他参与方的传入连接的权限。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-111">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="1f5b8-112">“连接”授予应用程序向其他参与方发起连接的权限。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-112">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="1f5b8-113">对于 SocketPermission 实例，“接受”意味着应用程序可以在本地传输地址上接受传入的连接；“连接”意味着应用程序可以连接到某个远程（或本地）传输地址。</span><span class="sxs-lookup"><span data-stu-id="1f5b8-113">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="1f5b8-114">对于 WebPermission 实例，“接受”意味着应用程序可以将 WebPermission 控制的 URI 导出到外界；“连接”意味着应用程序可以访问该 URI（无论它是远程还是本地的）。 </span><span class="sxs-lookup"><span data-stu-id="1f5b8-114">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f5b8-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f5b8-115">See also</span></span>

- [<span data-ttu-id="1f5b8-116">安全性</span><span class="sxs-lookup"><span data-stu-id="1f5b8-116">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="1f5b8-117">网络编程中的安全性</span><span class="sxs-lookup"><span data-stu-id="1f5b8-117">Security in Network Programming</span></span>](security-in-network-programming.md)
