---
title: 保证客户端应用程序的安全
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: 96b43d28d3e22df66cb7f7010916b5c7f7a86b77
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189001"
---
# <a name="secure-client-applications"></a><span data-ttu-id="ac224-102">保证客户端应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="ac224-102">Secure Client Applications</span></span>

<span data-ttu-id="ac224-103">应用程序通常由多个部件组成，所有这些部件均不能包含漏洞，否则可能导致数据丢失或以其他方式危害系统。</span><span class="sxs-lookup"><span data-stu-id="ac224-103">Applications typically consist of many parts that must all be protected from vulnerabilities that could result in data loss or otherwise compromise the system.</span></span> <span data-ttu-id="ac224-104">在攻击者可访问数据或系统资源之前将其阻止，以此可创建安全的用户界面来防止出现许多问题。</span><span class="sxs-lookup"><span data-stu-id="ac224-104">Creating secure user interfaces can prevent many problems by blocking attackers before they can access data or system resources.</span></span>  
  
## <a name="validate-user-input"></a><span data-ttu-id="ac224-105">验证用户输入</span><span class="sxs-lookup"><span data-stu-id="ac224-105">Validate User Input</span></span>  

 <span data-ttu-id="ac224-106">在构建访问数据的应用程序时，除非能够证明其不为恶意输入，否则您应该假定所有用户输入均为恶意输入。</span><span class="sxs-lookup"><span data-stu-id="ac224-106">When constructing an application that accesses data, you should assume that all user input is malicious until proven otherwise.</span></span> <span data-ttu-id="ac224-107">如果未能实现此目的，则可能会使您的应用程序易于受到攻击。</span><span class="sxs-lookup"><span data-stu-id="ac224-107">Failure to do so can leave your application vulnerable to attack.</span></span> <span data-ttu-id="ac224-108">.NET Framework 包含的类可帮助您约束输入控件的值的域，如限制可输入字符的数目。</span><span class="sxs-lookup"><span data-stu-id="ac224-108">The .NET Framework contains classes to help you enforce a domain of values for input controls, such as limiting the number of characters that can be entered.</span></span> <span data-ttu-id="ac224-109">使用事件挂钩，您可以编写用于检查值的有效性的程序。</span><span class="sxs-lookup"><span data-stu-id="ac224-109">Event hooks allow you to write procedures to check the validity of values.</span></span> <span data-ttu-id="ac224-110">可验证和强类型化用户输入数据，从而限制应用程序对脚本和 SQL 注入攻击的公开程度。</span><span class="sxs-lookup"><span data-stu-id="ac224-110">User input data can be validated and strongly typed, limiting an application's exposure to script and SQL injection exploits.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ac224-111">您还必须验证数据源和客户端应用程序中的用户输入。</span><span class="sxs-lookup"><span data-stu-id="ac224-111">You must also validate user input at the data source as well as in the client application.</span></span> <span data-ttu-id="ac224-112">因为攻击者可能选择避开应用程序，而直接攻击数据源。</span><span class="sxs-lookup"><span data-stu-id="ac224-112">An attacker may choose to circumvent your application and attack the data source directly.</span></span>  
  
 [<span data-ttu-id="ac224-113">安全性和用户输入</span><span class="sxs-lookup"><span data-stu-id="ac224-113">Security and User Input</span></span>](../../../standard/security/security-and-user-input.md)  
 <span data-ttu-id="ac224-114">描述如何处理与用户输入相关的细微和潜在危险缺陷。</span><span class="sxs-lookup"><span data-stu-id="ac224-114">Describes how to handle subtle and potentially dangerous bugs involving user input.</span></span>  
  
 <span data-ttu-id="ac224-115">[验证 ASP.NET 网页中的用户输入](/previous-versions/aspnet/7kh55542(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac224-115">[Validating User Input in ASP.NET Web Pages](/previous-versions/aspnet/7kh55542(v=vs.100))</span></span>  
 <span data-ttu-id="ac224-116">概述如何使用 ASP.NET 验证控件验证用户输入。</span><span class="sxs-lookup"><span data-stu-id="ac224-116">Overview of validating user input using ASP.NET validation controls.</span></span>  
  
 [<span data-ttu-id="ac224-117">Windows 窗体中的用户输入</span><span class="sxs-lookup"><span data-stu-id="ac224-117">User Input in Windows Forms</span></span>](/dotnet/desktop/winforms/user-input-in-windows-forms)  
 <span data-ttu-id="ac224-118">提供用于验证 Windows 窗体应用程序中鼠标和键盘输入的链接和信息。</span><span class="sxs-lookup"><span data-stu-id="ac224-118">Provides links and information for validating mouse and keyboard input in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="ac224-119">.NET Framework 正则表达式</span><span class="sxs-lookup"><span data-stu-id="ac224-119">.NET Framework Regular Expressions</span></span>](../../../standard/base-types/regular-expressions.md)  
 <span data-ttu-id="ac224-120">描述如何使用 <xref:System.Text.RegularExpressions.Regex> 类检查用户输入的有效性。</span><span class="sxs-lookup"><span data-stu-id="ac224-120">Describes how to use the <xref:System.Text.RegularExpressions.Regex> class to check the validity of user input.</span></span>  
  
## <a name="windows-applications"></a><span data-ttu-id="ac224-121">Windows 应用程序</span><span class="sxs-lookup"><span data-stu-id="ac224-121">Windows Applications</span></span>  

 <span data-ttu-id="ac224-122">过去，Windows 应用程序通常使用完全权限运行。</span><span class="sxs-lookup"><span data-stu-id="ac224-122">In the past, Windows applications generally ran with full permissions.</span></span> <span data-ttu-id="ac224-123">通过使用代码启用安全性 (CAS)，.NET Framework 可提供限制在 Windows 应用程序中执行代码的基础结构。</span><span class="sxs-lookup"><span data-stu-id="ac224-123">The .NET Framework provides the infrastructure to restrict code executing in a Windows application by using code access security (CAS).</span></span> <span data-ttu-id="ac224-124">但是，仅使用 CAS 是不足以保护应用程序的。</span><span class="sxs-lookup"><span data-stu-id="ac224-124">However, CAS alone is not enough to protect your application.</span></span>  
  
 [<span data-ttu-id="ac224-125">Windows 窗体安全</span><span class="sxs-lookup"><span data-stu-id="ac224-125">Windows Forms Security</span></span>](/dotnet/desktop/winforms/windows-forms-security)  
 <span data-ttu-id="ac224-126">讨论如何保证 Windows 窗体应用程序的安全并提供相关主题的链接。</span><span class="sxs-lookup"><span data-stu-id="ac224-126">Discusses how to secure Windows Forms applications and provides links to related topics.</span></span>  
  
 [<span data-ttu-id="ac224-127">Windows 窗体和非托管应用程序</span><span class="sxs-lookup"><span data-stu-id="ac224-127">Windows Forms and Unmanaged Applications</span></span>](/dotnet/desktop/winforms/advanced/windows-forms-and-unmanaged-applications)  
 <span data-ttu-id="ac224-128">描述如何与 Windows 窗体应用程序中的非托管应用程序进行交互。</span><span class="sxs-lookup"><span data-stu-id="ac224-128">Describes how to interact with unmanaged applications in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="ac224-129">Windows 窗体的 ClickOnce 部署</span><span class="sxs-lookup"><span data-stu-id="ac224-129">ClickOnce Deployment for Windows Forms</span></span>](/dotnet/desktop/winforms/clickonce-deployment-for-windows-forms)  
 <span data-ttu-id="ac224-130">描述如何在 Windows 窗体应用程序中使用 `ClickOnce` 部署，并讨论安全含义。</span><span class="sxs-lookup"><span data-stu-id="ac224-130">Describes how to use `ClickOnce` deployment in a Windows Forms application and discusses the security implications.</span></span>  
  
## <a name="aspnet-and-xml-web-services"></a><span data-ttu-id="ac224-131">ASP.NET 和 XML Web services</span><span class="sxs-lookup"><span data-stu-id="ac224-131">ASP.NET and XML Web Services</span></span>  

 <span data-ttu-id="ac224-132">ASP.NET 应用程序通常需要限制对 Web 站点某些部分的访问，并提供其他数据保护机制和站点安全机制。</span><span class="sxs-lookup"><span data-stu-id="ac224-132">ASP.NET applications generally need to restrict access to some portions of the Web site and provide other mechanisms for data protection and site security.</span></span> <span data-ttu-id="ac224-133">这些链接可提供用于保护 ASP.NET 应用程序的有用信息。</span><span class="sxs-lookup"><span data-stu-id="ac224-133">These links provide useful information for securing your ASP.NET application.</span></span>  
  
 <span data-ttu-id="ac224-134">XML Web services 能够提供可由 ASP.NET 应用程序、Windows 窗体应用程序或其他 Web 服务使用的数据。</span><span class="sxs-lookup"><span data-stu-id="ac224-134">An XML Web service provides data that can be consumed by an ASP.NET application, a Windows Forms application, or another Web service.</span></span> <span data-ttu-id="ac224-135">你需要管理 Web 服务自身的安全性以及客户端应用程序的安全性。</span><span class="sxs-lookup"><span data-stu-id="ac224-135">You need to manage security for the Web service itself as well as security for the client application.</span></span>  
  
 <span data-ttu-id="ac224-136">有关详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="ac224-136">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="ac224-137">资源</span><span class="sxs-lookup"><span data-stu-id="ac224-137">Resource</span></span>|<span data-ttu-id="ac224-138">说明</span><span class="sxs-lookup"><span data-stu-id="ac224-138">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ac224-139">[保护 ASP.NET 网站](/previous-versions/aspnet/91f66yxt(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac224-139">[Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100))</span></span>|<span data-ttu-id="ac224-140">讨论如何保证 ASP.NET 应用程序的安全。</span><span class="sxs-lookup"><span data-stu-id="ac224-140">Discusses how to secure ASP.NET applications.</span></span>|  
|<span data-ttu-id="ac224-141">[保证使用 ASP.NET 创建的 XML Web services 的安全](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac224-141">[Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))</span></span>|<span data-ttu-id="ac224-142">讨论如何实现 ASP.NET Web 服务的安全性。</span><span class="sxs-lookup"><span data-stu-id="ac224-142">Discusses how to implement security for an ASP.NET Web Service.</span></span>|  
|<span data-ttu-id="ac224-143">[脚本攻击概述](/previous-versions/aspnet/w1sw53ds(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac224-143">[Script Exploits Overview](/previous-versions/aspnet/w1sw53ds(v=vs.100))</span></span>|<span data-ttu-id="ac224-144">讨论如何抵御脚本攻击，该攻击会尝试将恶意字符插入网页。</span><span class="sxs-lookup"><span data-stu-id="ac224-144">Discusses how to guard against a script exploit attack, which attempts to insert malicious characters into a Web page.</span></span>|  
|<span data-ttu-id="ac224-145">[Basic Security Practices for Web Applications（Web 应用程序的基本安全实践）](/previous-versions/aspnet/zdh19h94(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac224-145">[Basic Security Practices for Web Applications](/previous-versions/aspnet/zdh19h94(v=vs.100))</span></span>|<span data-ttu-id="ac224-146">常规安全信息和指向更多讨论的链接，</span><span class="sxs-lookup"><span data-stu-id="ac224-146">General security information and links to further discussion,</span></span>|  
  
## <a name="remoting"></a><span data-ttu-id="ac224-147">远程处理</span><span class="sxs-lookup"><span data-stu-id="ac224-147">Remoting</span></span>  

 <span data-ttu-id="ac224-148">利用 .NET 远程处理，可以方便地生成广泛分布的应用程序，而不论应用程序组件是全部集中在一台计算机上，还是分布在世界各地。</span><span class="sxs-lookup"><span data-stu-id="ac224-148">.NET remoting enables you to build widely distributed applications easily, whether the application components are all on one computer or spread out across the entire world.</span></span> <span data-ttu-id="ac224-149">生成的客户端应用程序可以使用同一台计算机（或可通过其网络连接到的任何其他计算机）上其他进程中的对象。</span><span class="sxs-lookup"><span data-stu-id="ac224-149">You can build client applications that use objects in other processes on the same computer or on any other computer that is reachable over its network.</span></span> <span data-ttu-id="ac224-150">您还可以在同一进程中使用 .NET 远程处理与其他应用程序域进行通信。</span><span class="sxs-lookup"><span data-stu-id="ac224-150">You can also use .NET remoting to communicate with other application domains in the same process.</span></span>  
  
|<span data-ttu-id="ac224-151">资源</span><span class="sxs-lookup"><span data-stu-id="ac224-151">Resource</span></span>|<span data-ttu-id="ac224-152">说明</span><span class="sxs-lookup"><span data-stu-id="ac224-152">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ac224-153">[远程应用程序的配置](/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac224-153">[Configuration of Remote Applications](/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))</span></span>|<span data-ttu-id="ac224-154">讨论如何配置远程处理应用程序以避免出现常见问题。</span><span class="sxs-lookup"><span data-stu-id="ac224-154">Discusses how to configure remoting applications in order to avoid common problems.</span></span>|  
|<span data-ttu-id="ac224-155">[远程处理中的安全性](/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac224-155">[Security in Remoting](/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))</span></span>|<span data-ttu-id="ac224-156">描述身份验证和加密以及与远程处理相关的其他安全主题。</span><span class="sxs-lookup"><span data-stu-id="ac224-156">Describes authentication and encryption as well as additional security topics relevant to remoting.</span></span>|  
|[<span data-ttu-id="ac224-157">安全性和远程处理注意事项</span><span class="sxs-lookup"><span data-stu-id="ac224-157">Security and Remoting Considerations</span></span>](../../misc/security-and-remoting-considerations.md)|<span data-ttu-id="ac224-158">描述与受保护对象和应用程序域交叉相关的安全问题。</span><span class="sxs-lookup"><span data-stu-id="ac224-158">Describes security issues with protected objects and application domain crossing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac224-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac224-159">See also</span></span>

- [<span data-ttu-id="ac224-160">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="ac224-160">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- <span data-ttu-id="ac224-161">[数据访问策略的建议](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ac224-161">[Recommendations for Data Access Strategies](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span></span>
- [<span data-ttu-id="ac224-162">保护应用程序</span><span class="sxs-lookup"><span data-stu-id="ac224-162">Securing Applications</span></span>](/visualstudio/ide/securing-applications)
- [<span data-ttu-id="ac224-163">保护连接信息</span><span class="sxs-lookup"><span data-stu-id="ac224-163">Protecting Connection Information</span></span>](protecting-connection-information.md)
- [<span data-ttu-id="ac224-164">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="ac224-164">ADO.NET Overview</span></span>](ado-net-overview.md)
