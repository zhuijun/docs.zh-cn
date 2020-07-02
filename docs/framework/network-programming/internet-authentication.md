---
title: Internet 身份验证
description: 了解 System.Net 类支持 .NET Framework 中的应用程序的各种客户端身份验证机制。
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: a1f0829aa0e9e4bcc68168b73443578c3a34310b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502374"
---
# <a name="internet-authentication"></a><span data-ttu-id="9e960-103">Internet 身份验证</span><span class="sxs-lookup"><span data-stu-id="9e960-103">Internet Authentication</span></span>
<span data-ttu-id="9e960-104"><xref:System.Net> 类支持多种客户端身份验证机制，包括标准 Internet 身份验证方法、基本、摘要式、协商、NTLM 和 Kerberos 身份验证，以及可以创建的自定义方法。</span><span class="sxs-lookup"><span data-stu-id="9e960-104">The <xref:System.Net> classes support a variety of client authentication mechanisms, including the standard Internet authentication methods basic, digest, negotiate, NTLM, and Kerberos authentication, as well as custom methods that you can create.</span></span>  
  
 <span data-ttu-id="9e960-105">身份验证凭据存储在实现 <xref:System.Net.ICredentials> 接口的 <xref:System.Net.NetworkCredential> 和 <xref:System.Net.CredentialCache> 类中。</span><span class="sxs-lookup"><span data-stu-id="9e960-105">Authentication credentials are stored in the <xref:System.Net.NetworkCredential> and <xref:System.Net.CredentialCache> classes, which implement the <xref:System.Net.ICredentials> interface.</span></span> <span data-ttu-id="9e960-106">在查询其中一个类以获取凭据时，它会返回 NetworkCredential 类的实例。</span><span class="sxs-lookup"><span data-stu-id="9e960-106">When one of these classes is queried for credentials, it returns an instance of the **NetworkCredential** class.</span></span> <span data-ttu-id="9e960-107">身份验证过程由 <xref:System.Net.AuthenticationManager> 类管理，而实际的身份验证过程由实现 <xref:System.Net.IAuthenticationModule> 接口的身份验证模块类执行。</span><span class="sxs-lookup"><span data-stu-id="9e960-107">The authentication process is managed by the <xref:System.Net.AuthenticationManager> class, and the actual authentication process is performed by an authentication module class that implements the <xref:System.Net.IAuthenticationModule> interface.</span></span> <span data-ttu-id="9e960-108">必须首先向 AuthenticationManager 注册自定义身份验证模块才能使用此模块；基本、摘要式、协商、NTLM 和 Kerberos 身份验证方法的模块是默认注册的。</span><span class="sxs-lookup"><span data-stu-id="9e960-108">You must register a custom authentication module with the **AuthenticationManager** before it can be used; modules for the basic, digest, negotiate, NTLM, and Kerberos authentication methods are registered by default.</span></span>  
  
 <span data-ttu-id="9e960-109">NetworkCredential 存储与由 URI 标识的单个 Internet 资源相关联的凭据集，并返回它们以响应任何对 <xref:System.Net.NetworkCredential.GetCredential%2A> 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="9e960-109">**NetworkCredential** stores a set of credentials associated with a single Internet resource identified by a URI and returns them in response to any call to the <xref:System.Net.NetworkCredential.GetCredential%2A> method.</span></span> <span data-ttu-id="9e960-110">NetworkCredential 类通常由访有限数量的 Internet 资源的应用程序使用，或者由在所有情况下使用同一凭据集的应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="9e960-110">The **NetworkCredential** class is typically used by applications that access a limited number of Internet resources or by applications that use the same set of credentials in all cases.</span></span>  
  
 <span data-ttu-id="9e960-111">CredentialCache 类存储各种 Web 资源的凭据集合。</span><span class="sxs-lookup"><span data-stu-id="9e960-111">The **CredentialCache** class stores a collection of credentials for various Web resources.</span></span> <span data-ttu-id="9e960-112">调用 <xref:System.Net.CredentialCache.GetCredential%2A> 方法时，CredentialCache 会返回适合的凭据集，由 Web 资源的 URI 以及请求的身份验证方案来确定。</span><span class="sxs-lookup"><span data-stu-id="9e960-112">When the <xref:System.Net.CredentialCache.GetCredential%2A> method is called, **CredentialCache** returns the proper set of credentials, as determined by the URI of the Web resource and the requested authentication scheme.</span></span> <span data-ttu-id="9e960-113">通过不同的身份验证方案使用各种 Internet 资源的应用程序可从使用 CredentialCache 中受益，因为此类可以存储所有凭据，并按照请求提供这些凭据。</span><span class="sxs-lookup"><span data-stu-id="9e960-113">Applications that use a variety of Internet resources with different authentication schemes benefit from using the **CredentialCache** class, since it stores all the credentials and provides them as requested.</span></span>  
  
 <span data-ttu-id="9e960-114">Internet 资源请求身份验证时，<xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> 方法将 <xref:System.Net.WebRequest> 发送给 AuthenticationManager，同时会发送对凭据的请求。</span><span class="sxs-lookup"><span data-stu-id="9e960-114">When an Internet resource requests authentication, the <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> method sends the <xref:System.Net.WebRequest> to the **AuthenticationManager** along with the request for credentials.</span></span> <span data-ttu-id="9e960-115">之后会根据以下过程对请求进行身份验证：</span><span class="sxs-lookup"><span data-stu-id="9e960-115">The request is then authenticated according to the following process:</span></span>  
  
1. <span data-ttu-id="9e960-116">AuthenticationManager 按照注册的顺序在每个已注册的身份验证模块上调用 <xref:System.Net.IAuthenticationModule.Authenticate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9e960-116">The **AuthenticationManager** calls the <xref:System.Net.IAuthenticationModule.Authenticate%2A> method on each of the registered authentication modules in the order they were registered.</span></span> <span data-ttu-id="9e960-117">AuthenticationManager 使用第一个不返回 null 的模块来执行身份验证过程 。</span><span class="sxs-lookup"><span data-stu-id="9e960-117">The **AuthenticationManager** uses the first module that does not return **null** to carry out the authentication process.</span></span> <span data-ttu-id="9e960-118">此过程的详细信息根据所涉及到的身份验证模块类型而异。</span><span class="sxs-lookup"><span data-stu-id="9e960-118">The details of the process vary depending on the type of authentication module involved.</span></span>  
  
2. <span data-ttu-id="9e960-119">完成身份验证过程后，此身份验证模块向包含访问 Internet 资源所需的信息的 WebRequest 返回 <xref:System.Net.Authorization>。</span><span class="sxs-lookup"><span data-stu-id="9e960-119">When the authentication process is complete, the authentication module returns an <xref:System.Net.Authorization> to the **WebRequest** that contains the information needed to access the Internet resource.</span></span>  
  
 <span data-ttu-id="9e960-120">某些身份验证方案可以对用户进行身份验证，而无需首先对资源发出请求。</span><span class="sxs-lookup"><span data-stu-id="9e960-120">Some authentication schemes can authenticate a user without first making a request for a resource.</span></span> <span data-ttu-id="9e960-121">应用程序可以使用资源预先对用户进行身份验证以节省时间，这样可以减少至少到服务器的一个往返。</span><span class="sxs-lookup"><span data-stu-id="9e960-121">An application can save time by preauthenticating the user with the resource, thus eliminating at least one round trip to the server.</span></span> <span data-ttu-id="9e960-122">或者，它也可以在程序启动期间执行身份验证，便于稍后更好地响应用户。</span><span class="sxs-lookup"><span data-stu-id="9e960-122">Or, it can perform authentication during program startup in order to be more responsive to the user later.</span></span> <span data-ttu-id="9e960-123">可以使用预身份验证的身份验证方案将 <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> 属性设置为“true”。</span><span class="sxs-lookup"><span data-stu-id="9e960-123">Authentication schemes that can use preauthentication set the <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> property to **true**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e960-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="9e960-124">See also</span></span>

- [<span data-ttu-id="9e960-125">基本和摘要式身份验证</span><span class="sxs-lookup"><span data-stu-id="9e960-125">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="9e960-126">NTLM 和 Kerberos 身份验证</span><span class="sxs-lookup"><span data-stu-id="9e960-126">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="9e960-127">网络编程中的安全性</span><span class="sxs-lookup"><span data-stu-id="9e960-127">Security in Network Programming</span></span>](security-in-network-programming.md)
