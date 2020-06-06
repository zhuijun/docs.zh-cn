---
title: <network> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154811"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="c5132-102">\<network> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="c5132-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="c5132-103">配置外部简单邮件传输协议（SMTP）服务器的网络选项。</span><span class="sxs-lookup"><span data-stu-id="c5132-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="c5132-104">语法</span><span class="sxs-lookup"><span data-stu-id="c5132-104">Syntax</span></span>  
  
```xml  
<network  
  clientDomain="string"
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"
  password="string"  
  port="integer"
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5132-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c5132-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c5132-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c5132-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5132-107">特性</span><span class="sxs-lookup"><span data-stu-id="c5132-107">Attributes</span></span>  
  
|<span data-ttu-id="c5132-108">属性</span><span class="sxs-lookup"><span data-stu-id="c5132-108">Attribute</span></span>|<span data-ttu-id="c5132-109">说明</span><span class="sxs-lookup"><span data-stu-id="c5132-109">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="c5132-110">指定要在初始 SMTP 协议请求中用来连接到 SMTP 邮件服务器的客户端域名。</span><span class="sxs-lookup"><span data-stu-id="c5132-110">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="c5132-111">默认值为发送请求的本地计算机的本地主机名。</span><span class="sxs-lookup"><span data-stu-id="c5132-111">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="c5132-112">指定是否应使用默认用户凭据访问 smtp 邮件服务器以获取 SMTP 事务。</span><span class="sxs-lookup"><span data-stu-id="c5132-112">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="c5132-113">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="c5132-113">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="c5132-114">指定是否使用 SSL 访问 SMTP 邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="c5132-114">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="c5132-115">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="c5132-115">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="c5132-116">指定用于 SMTP 事务的 SMTP 邮件服务器的主机名。</span><span class="sxs-lookup"><span data-stu-id="c5132-116">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="c5132-117">此属性没有默认值。</span><span class="sxs-lookup"><span data-stu-id="c5132-117">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="c5132-118">指定对 SMTP 邮件服务器进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="c5132-118">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="c5132-119">此属性没有默认值。</span><span class="sxs-lookup"><span data-stu-id="c5132-119">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="c5132-120">指定用于连接到 SMTP 邮件服务器的端口号。</span><span class="sxs-lookup"><span data-stu-id="c5132-120">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="c5132-121">默认值为 25。</span><span class="sxs-lookup"><span data-stu-id="c5132-121">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="c5132-122">指定在对 SMTP 事务使用扩展保护时用于身份验证的服务提供程序名称（SPN）。</span><span class="sxs-lookup"><span data-stu-id="c5132-122">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="c5132-123">此属性没有默认值。</span><span class="sxs-lookup"><span data-stu-id="c5132-123">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="c5132-124">指定用于对 SMTP 邮件服务器进行身份验证的用户名。</span><span class="sxs-lookup"><span data-stu-id="c5132-124">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="c5132-125">此属性没有默认值。</span><span class="sxs-lookup"><span data-stu-id="c5132-125">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5132-126">子元素</span><span class="sxs-lookup"><span data-stu-id="c5132-126">Child Elements</span></span>  
 <span data-ttu-id="c5132-127">无。</span><span class="sxs-lookup"><span data-stu-id="c5132-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5132-128">父元素</span><span class="sxs-lookup"><span data-stu-id="c5132-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c5132-129">元素</span><span class="sxs-lookup"><span data-stu-id="c5132-129">Element</span></span>|<span data-ttu-id="c5132-130">描述</span><span class="sxs-lookup"><span data-stu-id="c5132-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5132-131">\<smtp>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="c5132-131">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="c5132-132">配置简单邮件传输协议（SMTP）邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="c5132-132">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5132-133">注解</span><span class="sxs-lookup"><span data-stu-id="c5132-133">Remarks</span></span>  
 <span data-ttu-id="c5132-134">某些 SMTP 服务器要求在使用之前向服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c5132-134">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="c5132-135">如果要使用主机上的默认网络凭据对自己进行身份验证，请将 `defaultCredentials` 属性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="c5132-135">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="c5132-136"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>属性可用于 `defaultCredentials` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="c5132-136">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c5132-137">你还可以使用基本身份验证（用户名和密码）对 SMTP 服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c5132-137">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="c5132-138">若要使用此选项，你必须为指定的 SMTP 服务器指定有效的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="c5132-138">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5132-139">基本身份验证将 `userName` 和 `password` 值发送到未加密的服务器。</span><span class="sxs-lookup"><span data-stu-id="c5132-139">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="c5132-140">监视网络流量的任何人都可以查看凭据并使用它们连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="c5132-140">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="c5132-141">你应考虑使用更安全的身份验证机制，如 Kerberos 或 NT LAN Manager （NTLM）。如果 `defaultCredentials` 为 `true` ，则如果服务器支持这些协议，则将使用 KERBEROS 或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="c5132-141">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="c5132-142">基本身份验证和默认网络凭据选项相互排斥;如果将设置 `defaultCredentials` 为 `true` 并指定用户名和密码，则将使用默认网络凭据，并忽略基本身份验证数据。</span><span class="sxs-lookup"><span data-stu-id="c5132-142">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="c5132-143">对于基本身份验证，如果指定 `userName` ，则还应指定， `password` 以便自行向邮件服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c5132-143">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="c5132-144"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>属性可用于 `userName` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="c5132-144">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="c5132-145"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>属性可用于 `password` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="c5132-145">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="c5132-146">`password`出于安全原因，通常不会将属性输入到配置文件中。</span><span class="sxs-lookup"><span data-stu-id="c5132-146">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="c5132-147">`clientDomain`属性将在初始 smtp 协议请求中使用的客户端域名更改为 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="c5132-147">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="c5132-148">`clientDomain`属性可以设置为本地计算机的完全限定域名，而不能设置为默认使用的 localhost 名称。</span><span class="sxs-lookup"><span data-stu-id="c5132-148">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="c5132-149">这可以更好地符合 SMTP 协议标准。</span><span class="sxs-lookup"><span data-stu-id="c5132-149">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="c5132-150">默认值为发送请求的本地计算机的本地主机名。</span><span class="sxs-lookup"><span data-stu-id="c5132-150">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="c5132-151"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>属性可用于 `clientDomain` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="c5132-151">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c5132-152">`targetName`使用扩展保护时，此属性用于身份验证。</span><span class="sxs-lookup"><span data-stu-id="c5132-152">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="c5132-153">默认值的格式为 "SMTPSVC/"， \<host> 其中 \<host> 是 SMTP 邮件服务器的主机名。</span><span class="sxs-lookup"><span data-stu-id="c5132-153">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="c5132-154"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>属性可用于 `targetName` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="c5132-154">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c5132-155">`enableSsl`特性指定是否使用 SSL 访问 SMTP 邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="c5132-155">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="c5132-156"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>类仅支持在 RFC 3207 中定义的基于传输层安全性的安全 smtp 的 Smtp 服务扩展。</span><span class="sxs-lookup"><span data-stu-id="c5132-156">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="c5132-157">在此模式下，SMTP 会话在未加密的通道上开始，然后客户端向服务器发出一个 STARTTLS 命令，以使用 SSL 切换到安全通信。</span><span class="sxs-lookup"><span data-stu-id="c5132-157">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="c5132-158">有关详细信息，请参阅 Internet 工程任务组（IETF）发布的 RFC 3207。</span><span class="sxs-lookup"><span data-stu-id="c5132-158">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="c5132-159">备用连接方法是在发送任何协议命令之前提前建立 SSL 会话的位置。</span><span class="sxs-lookup"><span data-stu-id="c5132-159">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="c5132-160">此连接方法有时称为 SMTPS，默认情况下使用端口465。</span><span class="sxs-lookup"><span data-stu-id="c5132-160">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="c5132-161">当前不支持使用 SSL 的替代连接方法。</span><span class="sxs-lookup"><span data-stu-id="c5132-161">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="c5132-162"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>属性可用于 `enableSsl` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="c5132-162">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5132-163">示例</span><span class="sxs-lookup"><span data-stu-id="c5132-163">Example</span></span>  
 <span data-ttu-id="c5132-164">下面的示例指定了使用默认网络凭据发送电子邮件所需的适当 SMTP 参数。</span><span class="sxs-lookup"><span data-stu-id="c5132-164">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5132-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5132-165">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="c5132-166">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="c5132-166">Network Settings Schema</span></span>](index.md)
