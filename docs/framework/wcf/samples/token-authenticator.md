---
title: 令牌身份验证器
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: f4b49edd3b5a2cecd203feed713c7694450f7497
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596547"
---
# <a name="token-authenticator"></a><span data-ttu-id="6f0c1-102">令牌身份验证器</span><span class="sxs-lookup"><span data-stu-id="6f0c1-102">Token Authenticator</span></span>
<span data-ttu-id="6f0c1-103">此示例演示如何实现一个自定义令牌身份验证器。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="6f0c1-104">Windows Communication Foundation （WCF）中的令牌身份验证器用于验证消息所使用的令牌，验证该令牌是否是自我一致的，并且对与令牌关联的标识进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="6f0c1-105">自定义令牌身份验证器可用在各种场合，如：</span><span class="sxs-lookup"><span data-stu-id="6f0c1-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="6f0c1-106">当您希望重写与令牌相关联的默认身份验证机制时。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-106">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="6f0c1-107">当您生成自定义令牌时。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-107">When you are building a custom token.</span></span>

 <span data-ttu-id="6f0c1-108">此示例对下列内容进行了说明：</span><span class="sxs-lookup"><span data-stu-id="6f0c1-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="6f0c1-109">客户端如何使用用户名/密码对来进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-109">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="6f0c1-110">服务器如何使用自定义令牌身份验证器来验证客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="6f0c1-111">WCF 服务代码如何与自定义令牌身份验证器结合。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-111">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="6f0c1-112">如何使用服务器的 X.509 证书对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="6f0c1-113">此示例还演示如何在自定义令牌身份验证过程之后从 WCF 访问调用方的标识。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="6f0c1-114">服务会公开单一终结点以便与使用 App.config 配置文件定义的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="6f0c1-115">终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="6f0c1-116">绑定是在安全模式设置为消息（这是 `wsHttpBinding` 的默认模式）的情况下用标准 `wsHttpBinding` 配置的。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="6f0c1-117">此示例将标准 `wsHttpBinding`设置为使用客户端用户名身份验证。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="6f0c1-118">服务还使用 `serviceCredentials` 行为来配置服务证书。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="6f0c1-119">使用 `securityCredentials` 行为可以指定服务证书。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="6f0c1-120">客户端使用服务证书对服务进行身份验证并提供消息保护。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="6f0c1-121">以下配置引用了在示例设置过程中安装的 localhost 证书，如下面的设置说明中所述。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="6f0c1-122">客户端终结点配置由配置名称、服务终结点的绝对地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="6f0c1-123">该客户端绑定是使用相应的 `Mode` 和 `clientCredentialType` 配置的。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

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

 <span data-ttu-id="6f0c1-124">客户端实现设置要使用的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-124">The client implementation sets the user name and password to use.</span></span>

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="6f0c1-125">自定义令牌身份验证器</span><span class="sxs-lookup"><span data-stu-id="6f0c1-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="6f0c1-126">使用下列步骤来创建自定义令牌身份验证器：</span><span class="sxs-lookup"><span data-stu-id="6f0c1-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="6f0c1-127">编写自定义令牌身份验证器。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="6f0c1-128">此示例实现一个自定义令牌身份验证器，用来验证用户名是否具有有效的电子邮件格式。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="6f0c1-129">它派生 <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="6f0c1-130">此类中最重要的方法是 <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="6f0c1-131">在该方法中，身份验证器验证用户名的格式是否有效，以及主机名是否不来自恶意域。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="6f0c1-132">如果用户名的格式有效，而且主机名不来自恶意域，则该示例会返回 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 实例的只读集合，这些实例随后将用来提供声明以表示存储在用户名令牌中的信息。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```csharp
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="6f0c1-133">提供由自定义令牌身份验证器返回的授权策略。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="6f0c1-134">此示例提供名为 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 的 `UnconditionalPolicy` 的自己的实现，在该示例的构造函数中，此策略返回一组传入该示例的声明和标识。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```csharp
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="6f0c1-135">编写自定义安全令牌管理器。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="6f0c1-136">使用 <xref:System.IdentityModel.Selectors.SecurityTokenManager>，可以为在 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 方法中传入该管理器的特定 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 对象创建 `CreateSecurityTokenAuthenticator`。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="6f0c1-137">安全令牌管理器还用于创建令牌提供程序和令牌序列化程序，但是它们不包括在此示例中。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="6f0c1-138">在此示例中，自定义安全令牌管理器继承自 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 类，并重写 `CreateSecurityTokenAuthenticator` 方法，这样，当所传递令牌的要求指示请求用户名身份验证器时，将返回自定义用户名令牌身份验证器。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```csharp
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="6f0c1-139">编写自定义服务凭据。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-139">Write a custom service credential.</span></span>

     <span data-ttu-id="6f0c1-140">使用服务凭据类，可以表示为服务配置的凭据，并创建一个用来获取令牌身份验证器、令牌提供程序和令牌序列化程序的安全令牌管理器。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```csharp
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="6f0c1-141">将服务配置为使用自定义服务凭据。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="6f0c1-142">为了让服务使用自定义服务凭据，我们在捕获已在默认服务凭据中预先配置的服务证书之后删除了默认的服务凭据类，将新的服务凭据实例配置为使用预先配置的服务证书，并将这个新服务凭据实例添加到服务行为中。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="6f0c1-143">若要显示调用方信息，可以使用 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="6f0c1-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 包含有关当前调用方的声明信息。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="6f0c1-145">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6f0c1-146">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="6f0c1-147">设置批处理文件</span><span class="sxs-lookup"><span data-stu-id="6f0c1-147">Setup Batch File</span></span>
 <span data-ttu-id="6f0c1-148">通过运行此示例随附的 Setup.bat 批处理文件，可以用相关的证书将服务器配置为运行需要基于服务器证书的安全性的自承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="6f0c1-149">必须修改此批处理文件，以便跨计算机或在非承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="6f0c1-150">下面提供了批处理文件不同节的简要概述，以便可以修改批处理文件从而在相应的配置中运行。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="6f0c1-151">创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-151">Creating the server certificate.</span></span>

     <span data-ttu-id="6f0c1-152">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="6f0c1-153">`%SERVER_NAME%`变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="6f0c1-154">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="6f0c1-155">此批处理文件中的默认值为 localhost。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-155">The default in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6f0c1-156">将服务器证书安装到客户端的受信任证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="6f0c1-157">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6f0c1-158">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6f0c1-159">如果您已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="6f0c1-160">Setup 批处理文件通过 Windows SDK 命令提示运行。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="6f0c1-161">这要求 MSSDK 环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="6f0c1-162">将在 Windows SDK 命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="6f0c1-163">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="6f0c1-163">To set up and build the sample</span></span>

1. <span data-ttu-id="6f0c1-164">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6f0c1-165">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6f0c1-166">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="6f0c1-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6f0c1-167">从使用管理员特权打开的 Visual Studio 2012 命令提示符下的示例安装文件夹中运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="6f0c1-168">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6f0c1-169">设置 bat 批处理文件设计为在 Visual Studio 2012 命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="6f0c1-170">在 Visual Studio 2012 命令提示符中设置的 PATH 环境变量指向包含安装程序 bat 脚本所需的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="6f0c1-171">启动 service\bin 中的 service.exe。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="6f0c1-172">启动 \client\bin 中的 client.exe。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="6f0c1-173">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="6f0c1-174">如果客户端和服务无法进行通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6f0c1-175">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="6f0c1-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="6f0c1-176">在服务计算机上为服务二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="6f0c1-177">将服务程序文件复制到服务计算机上的服务目录。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="6f0c1-178">另外，将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="6f0c1-179">必须具有一个其主题名称中包含计算机的完全限定域名的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="6f0c1-180">必须更新服务的 App.config 文件才能反映这个新证书名称。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="6f0c1-181">如果您将 `%SERVER_NAME%` 变量设置为将在其上运行服务的计算机的完全限定主机名，则可以使用 Setup.bat 来创建一个这样的证书。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="6f0c1-182">请注意，必须使用管理员权限打开 Visual Studio 的开发人员命令提示中的 setup.exe 文件。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="6f0c1-183">将服务器证书复制到客户端的 CurrentUser-TrustedPeople 存储中。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="6f0c1-184">除非服务器证书是由客户端的受信任颁发者颁发的，否则没有必要这样做。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="6f0c1-185">在服务计算机的 App.config 文件中，更改基址的值以指定一个完全限定的计算机名称，而不是 localhost。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="6f0c1-186">在服务计算机上，在命令提示符下运行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="6f0c1-187">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="6f0c1-188">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="6f0c1-189">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="6f0c1-190">如果客户端和服务无法进行通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6f0c1-191">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="6f0c1-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="6f0c1-192">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="6f0c1-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
