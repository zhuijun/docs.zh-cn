---
title: 如何：使用用户名和密码进行身份验证
description: 了解如何通过使用示例代码，使 WCF 服务能够通过使用 Windows 域用户名和密码对客户端进行身份验证。
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 1f938f8041b2577b3705266948f29b42f23a6fd7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247242"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="2c009-103">如何：使用用户名和密码进行身份验证</span><span class="sxs-lookup"><span data-stu-id="2c009-103">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="2c009-104">本主题演示如何使 Windows Communication Foundation （WCF）服务能够使用 Windows 域用户名和密码对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2c009-104">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="2c009-105">它假定您有一个正在工作的自承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="2c009-105">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="2c009-106">有关创建基本的自承载 WCF 服务的示例，请参阅[入门教程](../getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="2c009-106">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="2c009-107">本主题假定在代码中配置服务。</span><span class="sxs-lookup"><span data-stu-id="2c009-107">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="2c009-108">若要查看使用配置文件配置类似服务的示例，请参阅[消息安全用户名](../samples/message-security-user-name.md)。</span><span class="sxs-lookup"><span data-stu-id="2c009-108">If you would like to see an example of configuring a similar service using a configuration file, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>

<span data-ttu-id="2c009-109">要配置服务以使用 Windows 域用户名和密码对其客户端进行身份验证，请使用 <xref:System.ServiceModel.WSHttpBinding>，并将其 `Security.Mode` 属性设置为 `Message`。</span><span class="sxs-lookup"><span data-stu-id="2c009-109">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="2c009-110">此外，您必须指定 X509 证书，该证书用于在将用户名和密码从客户端发送到服务时对它们进行加密。</span><span class="sxs-lookup"><span data-stu-id="2c009-110">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="2c009-111">在客户端上，您必须提示用户输入用户名和密码，并指定用户在 WCF 客户端代理上的凭据。</span><span class="sxs-lookup"><span data-stu-id="2c009-111">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="2c009-112">将 WCF 服务配置为使用 Windows 域用户名和密码进行身份验证</span><span class="sxs-lookup"><span data-stu-id="2c009-112">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="2c009-113">创建 <xref:System.ServiceModel.WSHttpBinding> 的实例，将绑定的安全模式设置为 <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>，将绑定的 `ClientCredentialType` 设置为 <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>，并使用配置的绑定将服务终结点添加到服务主机，如下面的代码中所示：</span><span class="sxs-lookup"><span data-stu-id="2c009-113">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="2c009-114">指定用于对通过网络发送的用户名和密码信息进行加密的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="2c009-114">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="2c009-115">此代码应紧跟在上面的代码之后。</span><span class="sxs-lookup"><span data-stu-id="2c009-115">This code should immediately follow the code above.</span></span> <span data-ttu-id="2c009-116">下面的示例使用 "[消息安全用户名](../samples/message-security-user-name.md)" 示例中由 setup.bat 文件创建的证书：</span><span class="sxs-lookup"><span data-stu-id="2c009-116">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="2c009-117">您可以使用您自己的证书，只需修改代码以引用您的证书。</span><span class="sxs-lookup"><span data-stu-id="2c009-117">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="2c009-118">有关创建和使用证书的详细信息，请参阅使用[证书](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="2c009-118">For more information about creating and using certificates see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="2c009-119">确保证书在本地计算机的受信任人证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="2c009-119">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="2c009-120">为此，可以运行 mmc.exe 并选择 "**文件**"、"**添加/删除管理单元 ...** " 菜单项。</span><span class="sxs-lookup"><span data-stu-id="2c009-120">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="2c009-121">在 "**添加或删除管理单元**" 对话框中，选择 "**证书" 管理单元**，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="2c009-121">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="2c009-122">在 "证书" 管理单元对话框中，选择 "**计算机帐户**"。</span><span class="sxs-lookup"><span data-stu-id="2c009-122">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="2c009-123">默认情况下，从消息安全用户名称示例生成的证书将位于个人/证书文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2c009-123">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="2c009-124">它将在 MMC 窗口中的 "颁发给" 列下作为 "localhost" 列出。</span><span class="sxs-lookup"><span data-stu-id="2c009-124">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="2c009-125">将证书拖放到 "**受信任人**" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2c009-125">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="2c009-126">这将允许 WCF 在执行身份验证时，将证书视为受信任的证书。</span><span class="sxs-lookup"><span data-stu-id="2c009-126">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="2c009-127">调用服务传递用户名和密码</span><span class="sxs-lookup"><span data-stu-id="2c009-127">To call the service passing username and password</span></span>

1. <span data-ttu-id="2c009-128">客户端应用程序必须提示用户输入其用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="2c009-128">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="2c009-129">以下代码要求用户输入用户名和密码：</span><span class="sxs-lookup"><span data-stu-id="2c009-129">The following code asks the user for username and password:</span></span>

    > [!WARNING]
    > <span data-ttu-id="2c009-130">此代码不应在生产中使用，因为密码在输入时将显示出来。</span><span class="sxs-lookup"><span data-stu-id="2c009-130">This code should not be used in production as the password is displayed while being entered.</span></span>

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
    }
    ```

2. <span data-ttu-id="2c009-131">创建客户端代理的实例，指定客户端的凭据，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="2c009-131">Create an instance of the client proxy specifying the client's credentials as shown in the following code:</span></span>

    ```csharp
    string username;
    string password;

    // Instantiate the proxy.
    var proxy = new Service1Client();

    // Prompt the user for username & password.
    GetPassword(out username, out password);

    // Set the user's credentials on the proxy.
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted.
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;
    // Call the service operation using the proxy
    ```

## <a name="see-also"></a><span data-ttu-id="2c009-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="2c009-132">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="2c009-133">通过基本身份验证确保的传输安全</span><span class="sxs-lookup"><span data-stu-id="2c009-133">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)
- [<span data-ttu-id="2c009-134">分布式应用程序安全</span><span class="sxs-lookup"><span data-stu-id="2c009-134">Distributed Application Security</span></span>](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
