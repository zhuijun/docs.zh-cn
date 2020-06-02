---
title: 主体和标识对象
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
ms.openlocfilehash: cece51370fb269121e776e865275cd464c1af095
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291222"
---
# <a name="principal-and-identity-objects"></a>主体和标识对象
托管代码可以通过包含对对象的引用的对象发现标识或主体的角色 <xref:System.Security.Principal.IPrincipal> <xref:System.Security.Principal.IIdentity> 。 将标识对象和主体对象同用户帐户与组帐户这样常见的概念进行比较，可能会有所帮助。 在大多数网络环境中，用户帐户表示人员或程序，而组帐户表示特定类别的用户及其拥有的权限。 同样，.NET Framework 中的标识对象表示用户，而角色表示成员资格与安全性上下文。 在 .NET Framework 中，主体对象同时封装标识对象和角色。 .NET Framework 应用程序根据主体的标识或角色成员资格（后者更常见）来向主体授予权限。  
  
## <a name="identity-objects"></a>标识对象  
 标识对象封装有关正在验证的用户或实体的信息。 在最基本的级别上，标识对象包含名称和身份验证类型。 名称可以是用户名或 Windows 帐户名，而身份验证类型可以是所支持的登录协议（如 Kerberos V5）或自定义值。 .NET Framework 定义一个 <xref:System.Security.Principal.GenericIdentity> 对象，该对象可用于大多数自定义登录方案和更专用的 <xref:System.Security.Principal.WindowsIdentity> 对象，当你希望应用程序依赖于 Windows 身份验证时，可以使用该对象。 此外，还可以定义自己的标识类来封装自定义用户信息。  
  
 <xref:System.Security.Principal.IIdentity>接口定义用于访问名称和身份验证类型（如 Kerberos V5 或 NTLM）的属性。 所有 **Identity** 类均实现 **IIdentity** 接口。 **Identity** 对象与当前执行线程所用的 Windows NT 进程标记之间不需要有什么关系。 但是，如果 **Identity** 对象是 **WindowsIdentity** 对象，则假定标识表示 Windows NT 安全标记。  
  
## <a name="principal-objects"></a>主体对象  
 主体对象表示代码运行时所在的安全性上下文。 实现基于角色的安全性的应用程序基于与主体对象关联的角色来授予权限。 与标识对象类似，.NET Framework 提供 <xref:System.Security.Principal.GenericPrincipal> 对象和 <xref:System.Security.Principal.WindowsPrincipal> 对象。 你还可以定义自己的自定义主体类。  
  
 <xref:System.Security.Principal.IPrincipal>接口定义用于访问关联的**标识**对象的属性，以及用于确定由**主体**对象标识的用户是否是给定角色的成员的方法。 所有 **Principal** 类都实现 **IPrincipal** 接口以及任何必需的附加属性和方法。 例如，公共语言运行时提供 **WindowsPrincipal** 类，该类实现将 Windows NT 或 Windows 2000 组成员资格映射到角色的附加功能。  
  
 **主体**对象绑定到 <xref:System.Runtime.Remoting.Messaging.CallContext> 应用程序域（）中的调用上下文（）对象 <xref:System.AppDomain> 。 默认的调用上下文始终用每个新的 **AppDomain** 创建，因此始终存在可用于接受 **Principal** 对象的调用上下文。 创建新线程的同时也为该线程创建 **CallContext** 对象。 **Principal** 对象引用从正在创建的线程自动复制到新线程的 **CallContext** 中。 如果运行时无法确定哪个**Principal** 对象属于线程的创建者，则会遵循 **Principal** 和 **Identity** 对象创建的默认策略。  
  
 可配置的应用程序域特定策略定义了一些规则，用以决定同新的应用程序域关联的 **Principal** 对象类型。 在安全策略的允许范围内，运行时可创建 **Principal** 和 **Identity** 对象来反射与当前执行线程关联的操作系统标记。 默认情况下，运行时使用 **Principal** 和 **Identity** 对象表示未经身份验证的用户。 运行时不创建这些默认的 **Principal** 和 **Identity** 对象，除非代码尝试访问它们。  
  
 创建应用程序域的受信任代码可设置应用程序域策略，以控制默认 **Principal** 和 **Identity** 对象的构造。 此应用程序域特定策略适用于该应用程序域中的所有执行线程。 非托管的受信任主机本质上能够设置此策略，但设置此策略的托管代码必须具有 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> 用于控制域策略的。  
  
 在不同的应用程序域之间、但在同一进程内（因此在同一台计算机上）传输 **Principal** 对象时，远程处理基础结构将与调用方上下文相关联的、对 **Principal** 对象的引用复制到被调用方的上下文中。  
  
## <a name="see-also"></a>另请参阅

- [如何：创建 WindowsPrincipal 对象](how-to-create-a-windowsprincipal-object.md)
- [如何：创建 GenericPrincipal 和 GenericIdentity 对象](how-to-create-genericprincipal-and-genericidentity-objects.md)
- [替换 Principal 对象](replacing-a-principal-object.md)
- [模拟与恢复](impersonating-and-reverting.md)
- [基于角色的安全性](role-based-security.md)
- [安全性的基础概念](key-security-concepts.md)
