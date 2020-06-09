---
title: 支持令牌
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 9c8ee4b11cd61e51e91c2e116ab3c20448fc1a58
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575038"
---
# <a name="supporting-tokens"></a><span data-ttu-id="eba36-102">支持令牌</span><span class="sxs-lookup"><span data-stu-id="eba36-102">Supporting Tokens</span></span>
<span data-ttu-id="eba36-103">支持令牌示例演示如何将其他令牌添加到使用 WS-Security 的消息。</span><span class="sxs-lookup"><span data-stu-id="eba36-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="eba36-104">该示例除添加用户名安全令牌外，还添加 X.509 二进制安全令牌。</span><span class="sxs-lookup"><span data-stu-id="eba36-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="eba36-105">在 WS-Security 消息头中将令牌从客户端传递到服务，部分消息使用与 X.509 安全令牌关联的私钥进行签名，以证明 X.509 证书相对于接收方的所有权。</span><span class="sxs-lookup"><span data-stu-id="eba36-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="eba36-106">这可用于当要求有多个与消息关联的声明时对发送方进行身份验证或授权。</span><span class="sxs-lookup"><span data-stu-id="eba36-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="eba36-107">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="eba36-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eba36-108">演示</span><span class="sxs-lookup"><span data-stu-id="eba36-108">Demonstrates</span></span>
 <span data-ttu-id="eba36-109">本示例演示：</span><span class="sxs-lookup"><span data-stu-id="eba36-109">The sample demonstrates:</span></span>

- <span data-ttu-id="eba36-110">客户端如何向服务传递其他安全令牌。</span><span class="sxs-lookup"><span data-stu-id="eba36-110">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="eba36-111">服务器如何访问与其他安全令牌关联的声明。</span><span class="sxs-lookup"><span data-stu-id="eba36-111">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="eba36-112">如何使用服务器的 X.509 证书保护用于消息加密和签名的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="eba36-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
> <span data-ttu-id="eba36-113">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="eba36-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="eba36-114">使用用户名令牌进行客户端身份验证并支持 X.509 安全令牌</span><span class="sxs-lookup"><span data-stu-id="eba36-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>
 <span data-ttu-id="eba36-115">服务公开一个用于通信的单一终结点，此终结点是使用 `BindingHelper` 和 `EchoServiceHost` 类以编程方式创建的。</span><span class="sxs-lookup"><span data-stu-id="eba36-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="eba36-116">终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="eba36-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="eba36-117">此绑定使用 `SymmetricSecurityBindingElement` 和 `HttpTransportBindingElement` 按照自定义绑定进行配置。</span><span class="sxs-lookup"><span data-stu-id="eba36-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="eba36-118">本示例设置了 `SymmetricSecurityBindingElement` 以便使用服务 X.509 证书在传输过程中保护对称密钥和在 WS-Security 消息头中传递 `UserNameToken` 并支持 `X509SecurityToken`。</span><span class="sxs-lookup"><span data-stu-id="eba36-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="eba36-119">对称密钥用于对消息正文和用户名安全令牌进行加密。</span><span class="sxs-lookup"><span data-stu-id="eba36-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="eba36-120">支持令牌在 WS-Security 消息头中作为附加二进制安全令牌进行传递。</span><span class="sxs-lookup"><span data-stu-id="eba36-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="eba36-121">支持令牌的真实性是使用与支持 X.509 安全令牌关联的私钥通过消息的签名部分证实的。</span><span class="sxs-lookup"><span data-stu-id="eba36-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 <span data-ttu-id="eba36-122">此行为指定用于客户端身份验证的服务凭据和有关服务 X.509 证书的信息。</span><span class="sxs-lookup"><span data-stu-id="eba36-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="eba36-123">本示例在服务 X.509 证书中将 `CN=localhost` 用作主题名称。</span><span class="sxs-lookup"><span data-stu-id="eba36-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 <span data-ttu-id="eba36-124">服务代码：</span><span class="sxs-lookup"><span data-stu-id="eba36-124">Service code:</span></span>

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DistinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 <span data-ttu-id="eba36-125">客户端终结点的配置方式与服务终结点类似。</span><span class="sxs-lookup"><span data-stu-id="eba36-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="eba36-126">客户端使用相同的 `BindingHelper` 类创建绑定。</span><span class="sxs-lookup"><span data-stu-id="eba36-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="eba36-127">设置的其余部分位于 `Client` 类中。</span><span class="sxs-lookup"><span data-stu-id="eba36-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="eba36-128">客户端设置有关用户名安全令牌、支持 X.509 安全令牌的信息，并在设置代码中将有关服务 X.509 证书的信息设置为客户端终结点行为集合。</span><span class="sxs-lookup"><span data-stu-id="eba36-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
       string username = Console.ReadLine();
       Console.WriteLine("   Enter password:");
       string password = "";
       ConsoleKeyInfo info = Console.ReadKey(true);
       while (info.Key != ConsoleKey.Enter)
       {
           if (info.Key != ConsoleKey.Backspace)
           {
               if (info.KeyChar != '\0')
               {
                   password += info.KeyChar;
                }
                info = Console.ReadKey(true);
            }
            else if (info.Key == ConsoleKey.Backspace)
            {
                if (password != "")
                {
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a><span data-ttu-id="eba36-129">显示调用方信息</span><span class="sxs-lookup"><span data-stu-id="eba36-129">Displaying Callers' Information</span></span>
 <span data-ttu-id="eba36-130">若要显示调用方信息，可以使用 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="eba36-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="eba36-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` 包含与当前调用方关联的授权声明。</span><span class="sxs-lookup"><span data-stu-id="eba36-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="eba36-132">这些声明由 Windows Communication Foundation （WCF）为消息中收到的每个令牌自动提供。</span><span class="sxs-lookup"><span data-stu-id="eba36-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DistinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a><span data-ttu-id="eba36-133">运行示例</span><span class="sxs-lookup"><span data-stu-id="eba36-133">Running the Sample</span></span>
 <span data-ttu-id="eba36-134">运行此示例时，客户端首先提示您为用户名令牌提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="eba36-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="eba36-135">请确保为系统帐户提供正确的值，因为服务上的 WCF 将用户名令牌中提供的值映射到系统提供的标识中。</span><span class="sxs-lookup"><span data-stu-id="eba36-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="eba36-136">此后，客户端会显示来自服务的响应。</span><span class="sxs-lookup"><span data-stu-id="eba36-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="eba36-137">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="eba36-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="eba36-138">设置批处理文件</span><span class="sxs-lookup"><span data-stu-id="eba36-138">Setup Batch File</span></span>
 <span data-ttu-id="eba36-139">通过运行此示例随附的 Setup.bat 批处理文件，可以用相关的证书将服务器配置为运行以 Internet 信息服务 (IIS) 为宿主的应用程序，该应用程序要求基于服务器证书的安全性。</span><span class="sxs-lookup"><span data-stu-id="eba36-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="eba36-140">必须修改此批处理文件，以便跨计算机或在非承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="eba36-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="eba36-141">下面提供了批处理文件不同节的简要概述，以便可以修改批处理文件从而在相应的配置中运行。</span><span class="sxs-lookup"><span data-stu-id="eba36-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="eba36-142">创建客户端证书</span><span class="sxs-lookup"><span data-stu-id="eba36-142">Creating the Client Certificate</span></span>
 <span data-ttu-id="eba36-143">Setup.bat 批处理文件中的以下行创建将要使用的客户端证书。</span><span class="sxs-lookup"><span data-stu-id="eba36-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="eba36-144">`%CLIENT_NAME%` 变量指定客户端证书的主题。</span><span class="sxs-lookup"><span data-stu-id="eba36-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="eba36-145">本示例使用“client.com”作为主题名称。</span><span class="sxs-lookup"><span data-stu-id="eba36-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="eba36-146">证书存储在 `CurrentUser` 存储位置下的 My（个人）存储区中。</span><span class="sxs-lookup"><span data-stu-id="eba36-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="eba36-147">将客户端证书安装到服务器的受信任存储区中</span><span class="sxs-lookup"><span data-stu-id="eba36-147">Installing the Client Certificate into the Server's Trusted Store</span></span>
 <span data-ttu-id="eba36-148">Setup.bat 批处理文件中的以下行将客户端证书复制到服务器的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="eba36-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="eba36-149">因为服务器系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="eba36-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="eba36-150">如果您已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="eba36-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="eba36-151">创建服务器证书</span><span class="sxs-lookup"><span data-stu-id="eba36-151">Creating the Server Certificate</span></span>
 <span data-ttu-id="eba36-152">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="eba36-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="eba36-153">`%SERVER_NAME%`变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="eba36-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="eba36-154">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="eba36-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="eba36-155">此批处理文件中的默认值为 localhost。</span><span class="sxs-lookup"><span data-stu-id="eba36-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="eba36-156">证书存储在 LocalMachine 存储位置下的 My（个人）存储区中。</span><span class="sxs-lookup"><span data-stu-id="eba36-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="eba36-157">对于 IIS 承载的服务，证书存储在 LocalMachine 存储区中。</span><span class="sxs-lookup"><span data-stu-id="eba36-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="eba36-158">对于自承载服务，应该通过用 CurrentUser 替换字符串 LocalMachine 来修改批处理文件，以便将服务器证书存储在 CurrentUser 存储位置中。</span><span class="sxs-lookup"><span data-stu-id="eba36-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="eba36-159">将服务器证书安装到客户端的受信任证书存储区中</span><span class="sxs-lookup"><span data-stu-id="eba36-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>
 <span data-ttu-id="eba36-160">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="eba36-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="eba36-161">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="eba36-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="eba36-162">如果您已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="eba36-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="eba36-163">启用对证书私钥的访问</span><span class="sxs-lookup"><span data-stu-id="eba36-163">Enabling Access to the Certificate's Private Key</span></span>
 <span data-ttu-id="eba36-164">若要从 IIS 承载的服务启用对证书私钥的访问，必须为 IIS 承载的进程运行时所使用的用户帐户授予对该私钥的适当权限。</span><span class="sxs-lookup"><span data-stu-id="eba36-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="eba36-165">这将由 Setup.bat 脚本中的最后步骤来完成。</span><span class="sxs-lookup"><span data-stu-id="eba36-165">This is accomplished by last steps in the Setup.bat script.</span></span>

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eba36-166">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="eba36-166">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="eba36-167">请确保已[为 Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="eba36-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="eba36-168">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="eba36-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="eba36-169">若要用单一计算机配置或跨计算机配置来运行示例，请按照下列说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="eba36-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="eba36-170">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="eba36-170">To run the sample on the same machine</span></span>

1. <span data-ttu-id="eba36-171">在 Visual Studio 2012 命令提示符下，使用管理员权限运行安装程序 .bat。</span><span class="sxs-lookup"><span data-stu-id="eba36-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="eba36-172">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="eba36-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eba36-173">设置 bat 批处理文件设计为在 Visual Studio 2012 命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="eba36-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="eba36-174">在 Visual Studio 2012 命令提示符中设置的 PATH 环境变量指向包含安装程序 bat 脚本所需的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="eba36-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="eba36-175">确保在运行完该示例后运行 Cleanup.bat 移除证书。</span><span class="sxs-lookup"><span data-stu-id="eba36-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="eba36-176">其他安全示例使用相同的证书。</span><span class="sxs-lookup"><span data-stu-id="eba36-176">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="eba36-177">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="eba36-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="eba36-178">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="eba36-178">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="eba36-179">如果客户端和服务无法进行通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="eba36-179">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="eba36-180">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="eba36-180">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="eba36-181">在服务计算机上创建目录。</span><span class="sxs-lookup"><span data-stu-id="eba36-181">Create a directory on the service machine.</span></span> <span data-ttu-id="eba36-182">使用 Internet 信息服务 (IIS) 管理工具为此目录创建名为 servicemodelsamples 的虚拟应用程序。</span><span class="sxs-lookup"><span data-stu-id="eba36-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="eba36-183">将服务程序文件从 \inetpub\wwwroot\servicemodelsamples 复制到服务计算机上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="eba36-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="eba36-184">确保复制 \bin 子目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="eba36-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="eba36-185">另外，将 Setup.bat、Cleanup.bat 和 ImportClientCert.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="eba36-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="eba36-186">在客户端计算机上为这些客户端二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="eba36-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="eba36-187">将客户端程序文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="eba36-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="eba36-188">另外，将 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 文件复制到客户端上。</span><span class="sxs-lookup"><span data-stu-id="eba36-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="eba36-189">在服务器上， `setup.bat service` 在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="eba36-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="eba36-190">`setup.bat`使用参数运行将 `service` 使用计算机的完全限定的域名创建一个服务证书，并将服务证书导出到名为 .cer 的文件中。</span><span class="sxs-lookup"><span data-stu-id="eba36-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="eba36-191">编辑 Web.config 以反映新的证书名称（在的属性中），该名称与 `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 计算机的完全限定域名相同。</span><span class="sxs-lookup"><span data-stu-id="eba36-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="eba36-192">将服务目录中的 Service.cer 文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="eba36-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="eba36-193">在客户端上， `setup.bat client` 在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="eba36-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="eba36-194">如果使用 `setup.bat` 自变量运行 `client`，则会创建一个名为 client.com 的客户端证书，并将此客户端证书导出到名为 Client.cer 的文件中。</span><span class="sxs-lookup"><span data-stu-id="eba36-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="eba36-195">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="eba36-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="eba36-196">通过用服务器的完全限定域名替换 localhost 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="eba36-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="eba36-197">将客户端目录中的 Client.cer 文件复制到服务器上的服务目录中。</span><span class="sxs-lookup"><span data-stu-id="eba36-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="eba36-198">在客户端上，运行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="eba36-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="eba36-199">这会将 Service.cer 文件中的服务证书导入 CurrentUser – TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="eba36-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="eba36-200">在服务器上，运行 ImportClientCert.bat，这会将 Client.cer 文件中的客户端证书导入 LocalMachine - TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="eba36-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="eba36-201">在客户端计算机上，从命令提示符窗口中启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="eba36-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="eba36-202">如果客户端和服务无法进行通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="eba36-202">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="eba36-203">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="eba36-203">To clean up after the sample</span></span>  
  
- <span data-ttu-id="eba36-204">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="eba36-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eba36-205">此脚本不会在跨计算机运行此示例时移除客户端上的服务证书。</span><span class="sxs-lookup"><span data-stu-id="eba36-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="eba36-206">如果你已运行跨计算机使用证书的 WCF 示例，请确保清除已安装在 CurrentUser-TrustedPeople 存储中的服务证书。</span><span class="sxs-lookup"><span data-stu-id="eba36-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="eba36-207">为此，请使用以下命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="eba36-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
