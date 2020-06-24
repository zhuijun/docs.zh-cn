---
title: 如何：使用自定义用户名和密码验证程序
description: 了解如何合并用于 WFC 应用程序的自定义密码验证程序来代替默认的 Windows 用户名和密码验证。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 7f69db7bf8248593b64cdae4378983c2460de597
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246787"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0ef9b-103">如何：使用自定义用户名和密码验证程序</span><span class="sxs-lookup"><span data-stu-id="0ef9b-103">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="0ef9b-104">默认情况下，当使用用户名和密码进行身份验证时，Windows Communication Foundation （WCF）使用 Windows 来验证用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-104">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="0ef9b-105">不过，WCF 允许使用自定义用户名和密码身份验证方案（也称为*验证*程序）。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-105">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="0ef9b-106">若要合并自定义用户名和密码验证程序，请创建一个从 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 派生的类，然后对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-106">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="0ef9b-107">有关示例应用程序，请参阅[用户名密码验证](../samples/user-name-password-validator.md)程序。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-107">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0ef9b-108">创建自定义用户名和密码验证程序</span><span class="sxs-lookup"><span data-stu-id="0ef9b-108">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="0ef9b-109">创建一个从 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 派生的类。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-109">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="0ef9b-110">通过重写 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法，实现自定义身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-110">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="0ef9b-111">请不要使用下面示例中的代码在生产环境中重写 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-111">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="0ef9b-112">请将该代码替换为你的自定义用户名和密码验证方案，这可能会涉及到从数据库检索用户名和密码对。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-112">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="0ef9b-113">若要将身份验证错误返回到客户端，应在 <xref:System.ServiceModel.FaultException> 方法中引发 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-113">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0ef9b-114">配置服务以使用自定义用户名和密码验证程序</span><span class="sxs-lookup"><span data-stu-id="0ef9b-114">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="0ef9b-115">配置一个绑定，该绑定在任何传输上使用消息安全，或者在 HTTP(S) 上使用传输级安全。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-115">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="0ef9b-116">使用消息安全时，添加一个系统提供的绑定，如 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ，或 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 支持消息安全和 `UserName` 凭据类型的。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-116">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="0ef9b-117">在 HTTP （S）上使用传输级安全时，请添加 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 使用 http （s）和 `Basic` 身份验证方案的或。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-117">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0ef9b-118">使用 .NET Framework 3.5 或更高版本时，可以将自定义用户名和密码验证程序用于消息和传输安全。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-118">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="0ef9b-119">使用 WinFX，自定义用户名和密码验证程序只能与消息安全一起使用。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-119">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="0ef9b-120">有关 \<netTcpBinding> 在此上下文中使用的详细信息，请参阅 [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-120">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="0ef9b-121">在配置文件中的元素下， [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 添加一个 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-121">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="0ef9b-122">将 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 或 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 元素添加到 "绑定" 部分。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-122">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="0ef9b-123">有关创建 WCF 绑定元素的详细信息，请参阅[如何：在配置中指定服务绑定](../how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-123">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="0ef9b-124">将 `mode` 或的属性设置 [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) 为 `Message` 、 `Transport` 或 `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-124">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="0ef9b-125">设置 `clientCredentialType` 或的属性 [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-125">Set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="0ef9b-126">使用消息安全时，将 `clientCredentialType` 的特性设置 [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) 为 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-126">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="0ef9b-127">当通过 HTTP 使用传输级安全时，请将 `clientCredentialType` 或的属性设置 [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) 为 `Basic` 。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-127">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="0ef9b-128">当 WCF 服务在使用传输级安全性的 Internet Information Services （IIS）中承载并且 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> 属性设置为时 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> ，自定义身份验证方案将使用 Windows 身份验证的子集。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-128">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="0ef9b-129">这是因为在这种情况下，IIS 将在 WCF 调用自定义验证器之前执行 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-129">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="0ef9b-130">有关创建 WCF 绑定元素的详细信息，请参阅[如何：在配置中指定服务绑定](../how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-130">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="0ef9b-131">下面的示例演示绑定的配置代码：</span><span class="sxs-lookup"><span data-stu-id="0ef9b-131">The following example shows the configuration code for the binding:</span></span>

    ```xml
    <system.serviceModel>
      <bindings>
      <wsHttpBinding>
          <binding name="Binding1">
            <security mode="Message">
              <message clientCredentialType="UserName" />
            </security>
          </binding>
        </wsHttpBinding>
      </bindings>
    </system.serviceModel>
    ```

2. <span data-ttu-id="0ef9b-132">配置一个行为，该行为指定使用自定义用户名和密码验证程序来验证传入的 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 安全令牌的用户名和密码对。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-132">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="0ef9b-133">添加元素作为元素的子元素 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-133">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="0ef9b-134">将添加 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 到 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-134">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="0ef9b-135">添加 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 元素，并将 `name` 属性设置为合适的值。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-135">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="0ef9b-136">将添加 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 到 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-136">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="0ef9b-137">将添加 [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) 到 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-137">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="0ef9b-138">将 `userNamePasswordValidationMode` 设置为 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-138">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="0ef9b-139">如果 `userNamePasswordValidationMode` 未设置此值，WCF 将使用 Windows 身份验证而不是自定义用户名和密码验证程序。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="0ef9b-140">将 `customUserNamePasswordValidatorType` 设置为表示自定义用户名和密码验证程序的类型。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-140">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="0ef9b-141">下面的示例显示了 `<serviceCredentials>` 到此点的片段：</span><span class="sxs-lookup"><span data-stu-id="0ef9b-141">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="0ef9b-142">示例</span><span class="sxs-lookup"><span data-stu-id="0ef9b-142">Example</span></span>

<span data-ttu-id="0ef9b-143">下面的代码示例演示如何创建自定义用户名和密码验证程序。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-143">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="0ef9b-144">请不要使用代码重写生产环境中的 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-144">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="0ef9b-145">请将该代码替换为你的自定义用户名和密码验证方案，这可能会涉及到从数据库检索用户名和密码对。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-145">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0ef9b-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="0ef9b-146">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="0ef9b-147">如何：使用 ASP.NET 成员资格提供程序</span><span class="sxs-lookup"><span data-stu-id="0ef9b-147">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="0ef9b-148">身份验证</span><span class="sxs-lookup"><span data-stu-id="0ef9b-148">Authentication</span></span>](authentication-in-wcf.md)
