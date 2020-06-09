---
title: 如何：使用 ASP.NET 成员资格提供程序
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 840e4a5d365f2adbaf335c1061a580665a39824d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595318"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="a22f8-102">如何：使用 ASP.NET 成员资格提供程序</span><span class="sxs-lookup"><span data-stu-id="a22f8-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="a22f8-103">ASP.NET 成员资格提供程序是一项功能，使 ASP.NET 开发人员能够创建允许用户创建唯一的用户名和密码组合的网站。</span><span class="sxs-lookup"><span data-stu-id="a22f8-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="a22f8-104">使用此工具，任何用户都可以在该网站上建立帐户，并登录网站以便独占访问该网站及其服务。</span><span class="sxs-lookup"><span data-stu-id="a22f8-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="a22f8-105">这与要求用户在 Windows 域中具有帐户的 Windows 安全完全不同。</span><span class="sxs-lookup"><span data-stu-id="a22f8-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="a22f8-106">相反，任何提供凭据（用户名/密码组合）的用户都可以使用该网站及其服务。</span><span class="sxs-lookup"><span data-stu-id="a22f8-106">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="a22f8-107">有关示例应用程序，请参阅[成员身份和角色提供程序](../samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="a22f8-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="a22f8-108">有关使用 ASP.NET 角色提供程序功能的信息，请参阅[如何：将 ASP.NET 角色提供程序用于服务](how-to-use-the-aspnet-role-provider-with-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="a22f8-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="a22f8-109">成员资格功能要求使用 SQL Server 数据库来存储用户信息。</span><span class="sxs-lookup"><span data-stu-id="a22f8-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="a22f8-110">此功能还包括用于向忘记密码的用户提示问题的方法。</span><span class="sxs-lookup"><span data-stu-id="a22f8-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="a22f8-111">Windows Communication Foundation （WCF）开发人员可以出于安全目的利用这些功能。</span><span class="sxs-lookup"><span data-stu-id="a22f8-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="a22f8-112">当集成到 WCF 应用程序中时，用户必须为 WCF 客户端应用程序提供用户名/密码组合。</span><span class="sxs-lookup"><span data-stu-id="a22f8-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="a22f8-113">若要将数据传输到 WCF 服务，请使用支持用户名/密码凭据的绑定，如 <xref:System.ServiceModel.WSHttpBinding> （在配置中为 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ），并将客户端凭据类型设置为 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="a22f8-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="a22f8-114">在服务上，WCF 安全根据用户名和密码对用户进行身份验证，并分配由 ASP.NET 角色指定的角色。</span><span class="sxs-lookup"><span data-stu-id="a22f8-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="a22f8-115">WCF 不提供用用户名/密码组合或其他用户信息填充数据库的方法。</span><span class="sxs-lookup"><span data-stu-id="a22f8-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="a22f8-116">配置成员资格提供程序</span><span class="sxs-lookup"><span data-stu-id="a22f8-116">To configure the membership provider</span></span>

1. <span data-ttu-id="a22f8-117">在 web.config 文件中的 < > 元素下， `system.web` 创建一个 < `membership` > 元素。</span><span class="sxs-lookup"><span data-stu-id="a22f8-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="a22f8-118">在 `<membership>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a22f8-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="a22f8-119">`providers`添加 `<clear />` 元素以刷新提供程序的集合，作为 <> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="a22f8-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="a22f8-120">在 `<clear />` 元素下，创建一个 <`add`> 元素，并将以下属性设置为适当的值： `name` 、 `type` 、、、、、、 `connectionStringName` `applicationName` `enablePasswordRetrieval` `enablePasswordReset` `requiresQuestionAndAnswer` `requiresUniqueEmail` 和 `passwordFormat` 。</span><span class="sxs-lookup"><span data-stu-id="a22f8-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="a22f8-121">`name` 属性以后作为一个值在配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="a22f8-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="a22f8-122">下面的示例将其设置为 `SqlMembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="a22f8-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="a22f8-123">下面的示例显示配置节。</span><span class="sxs-lookup"><span data-stu-id="a22f8-123">The following example shows the configuration section.</span></span>

    ```xml
    <!-- Configure the Sql Membership Provider -->
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">
      <providers>
        <clear />
          <add
            name="SqlMembershipProvider"
            type="System.Web.Security.SqlMembershipProvider"
            connectionStringName="SqlConn"
            applicationName="MembershipAndRoleProviderSample"
            enablePasswordRetrieval="false"
            enablePasswordReset="false"
            requiresQuestionAndAnswer="false"
            requiresUniqueEmail="true"
            passwordFormat="Hashed" />
      </providers>
    </membership>
    ```

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="a22f8-124">配置服务安全以接受用户名/密码组合</span><span class="sxs-lookup"><span data-stu-id="a22f8-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="a22f8-125">在配置文件中的元素下， [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 添加一个 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="a22f8-125">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="a22f8-126">将添加 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 到 "绑定" 部分。</span><span class="sxs-lookup"><span data-stu-id="a22f8-126">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="a22f8-127">有关创建 WCF 绑定元素的详细信息，请参阅[如何：在配置中指定服务绑定](../how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="a22f8-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="a22f8-128">将 `mode` 元素的 `<security>` 属性设置为 `Message`。</span><span class="sxs-lookup"><span data-stu-id="a22f8-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="a22f8-129">将 `clientCredentialType` <> 元素的特性设置 `message` 为 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="a22f8-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="a22f8-130">这将指定将用户名/密码对用作客户端的凭据。</span><span class="sxs-lookup"><span data-stu-id="a22f8-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="a22f8-131">下面的示例显示绑定的配置代码。</span><span class="sxs-lookup"><span data-stu-id="a22f8-131">The following example shows the configuration code for the binding.</span></span>

    ```xml
    <system.serviceModel>
    <bindings>
      <wsHttpBinding>
      <!-- Set up a binding that uses UserName as the client credential type -->
        <binding name="MembershipBinding">
          <security mode ="Message">
            <message clientCredentialType ="UserName"/>
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    </system.serviceModel>
    ```

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="a22f8-132">配置服务以使用成员资格提供程序</span><span class="sxs-lookup"><span data-stu-id="a22f8-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="a22f8-133">作为元素的子元素 `<system.serviceModel>` ，添加一个 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素</span><span class="sxs-lookup"><span data-stu-id="a22f8-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="a22f8-134">将添加 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 到 <`behaviors`> 元素。</span><span class="sxs-lookup"><span data-stu-id="a22f8-134">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="a22f8-135">添加 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ，并将 `name` 属性设置为合适的值。</span><span class="sxs-lookup"><span data-stu-id="a22f8-135">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="a22f8-136">将添加 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 到 <`behavior`> 元素。</span><span class="sxs-lookup"><span data-stu-id="a22f8-136">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="a22f8-137">将添加 [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) 到 `<serviceCredentials>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a22f8-137">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="a22f8-138">将 `userNamePasswordValidationMode` 属性设置为 `MembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="a22f8-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a22f8-139">如果 `userNamePasswordValidationMode` 未设置此值，WCF 将使用 Windows 身份验证而不是 ASP.NET 成员资格提供程序。</span><span class="sxs-lookup"><span data-stu-id="a22f8-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="a22f8-140">将 `membershipProviderName` 属性设置为提供程序的名称（在本主题的第一个过程中添加提供程序时指定）。</span><span class="sxs-lookup"><span data-stu-id="a22f8-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="a22f8-141">下面的示例演示至此为止的 `<serviceCredentials>` 片段。</span><span class="sxs-lookup"><span data-stu-id="a22f8-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

    ```xml
    <behaviors>
       <serviceBehaviors>
          <behavior name="MyServiceBehavior">
             <serviceCredentials>
                <userNameAuthentication
                userNamePasswordValidationMode="MembershipProvider"
                membershipProviderName="SqlMembershipProvider" />
             </serviceCredentials>
          </behavior>
       </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a><span data-ttu-id="a22f8-142">示例</span><span class="sxs-lookup"><span data-stu-id="a22f8-142">Example</span></span>

<span data-ttu-id="a22f8-143">下面的代码示例演示使用 ASP 成员资格功能的服务的配置。</span><span class="sxs-lookup"><span data-stu-id="a22f8-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">
        <endpoint address="http://microsoft.com/WCFservices/Calculator"
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior name="MyServiceBehavior">
          <serviceCredentials>
            <userNameAuthentication
              userNamePasswordValidationMode="MembershipProvider"
              membershipProviderName="SqlMembershipProvider" />
          </serviceCredentials>
        </behavior>
          </serviceBehaviors>
    </behaviors>
    <bindings>
      <wsHttpBinding>
        <binding name="MembershipBinding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a22f8-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a22f8-144">See also</span></span>

- [<span data-ttu-id="a22f8-145">如何：将 ASP.NET 角色提供程序与服务一起使用</span><span class="sxs-lookup"><span data-stu-id="a22f8-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="a22f8-146">成员资格和角色提供程序</span><span class="sxs-lookup"><span data-stu-id="a22f8-146">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
