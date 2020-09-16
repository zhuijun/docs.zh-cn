---
title: 令牌提供程序
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 442371d211fe55cab33a87a5cf1b660679d7f94a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548548"
---
# <a name="token-provider"></a><span data-ttu-id="44e94-102">令牌提供程序</span><span class="sxs-lookup"><span data-stu-id="44e94-102">Token Provider</span></span>
<span data-ttu-id="44e94-103">此示例演示如何实现自定义令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="44e94-104">Windows Communication Foundation 中的令牌提供程序 (WCF) 用于向安全基础结构提供凭据。</span><span class="sxs-lookup"><span data-stu-id="44e94-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="44e94-105">令牌提供程序一般检查目标并颁发相应的凭据，以使安全基础结构能够确保消息的安全。</span><span class="sxs-lookup"><span data-stu-id="44e94-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="44e94-106">WCF 附带了默认的凭据管理器令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="44e94-107">WCF 还附带了一个 CardSpace 令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="44e94-108">自定义令牌提供程序在下列情况下有用：</span><span class="sxs-lookup"><span data-stu-id="44e94-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="44e94-109">存在不能由这些令牌提供程序操作的凭据存储。</span><span class="sxs-lookup"><span data-stu-id="44e94-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="44e94-110">如果希望提供自己的自定义机制，以便在 WCF 客户端框架使用凭据时，从用户提供详细信息时开始转换凭据。</span><span class="sxs-lookup"><span data-stu-id="44e94-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="44e94-111">要生成一个自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="44e94-111">If you are building a custom token.</span></span>

 <span data-ttu-id="44e94-112">此示例演示如何生成一个自定义令牌提供程序，以便将用户的输入转换为另一种格式。</span><span class="sxs-lookup"><span data-stu-id="44e94-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="44e94-113">总之，此示例将演示如下内容：</span><span class="sxs-lookup"><span data-stu-id="44e94-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="44e94-114">客户端如何使用用户名/密码对来进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="44e94-114">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="44e94-115">如何使用自定义令牌提供程序对客户端进行配置。</span><span class="sxs-lookup"><span data-stu-id="44e94-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="44e94-116">服务器如何使用密码和自定义 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>（用来验证用户名和密码是否相匹配）来验证客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="44e94-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="44e94-117">客户端如何使用服务器的 X.509 证书对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="44e94-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="44e94-118">此示例还演示在执行自定义令牌身份验证过程之后，如何访问调用方的标识。</span><span class="sxs-lookup"><span data-stu-id="44e94-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="44e94-119">服务会公开单一终结点以便与使用 App.config 配置文件定义的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="44e94-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="44e94-120">终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="44e94-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="44e94-121">绑定是使用标准 `wsHttpBinding` 配置的，该元素在默认情况下使用消息安全性。</span><span class="sxs-lookup"><span data-stu-id="44e94-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="44e94-122">此示例将标准 `wsHttpBinding`设置为使用客户端用户名身份验证。</span><span class="sxs-lookup"><span data-stu-id="44e94-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="44e94-123">服务还使用 serviceCredentials 行为来配置服务证书。</span><span class="sxs-lookup"><span data-stu-id="44e94-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="44e94-124">使用 serviceCredentials 行为可以配置服务证书。</span><span class="sxs-lookup"><span data-stu-id="44e94-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="44e94-125">客户端使用服务证书对服务进行身份验证并提供消息保护。</span><span class="sxs-lookup"><span data-stu-id="44e94-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="44e94-126">以下配置引用了在示例设置过程中安装的 localhost 证书，如下面的设置说明中所述。</span><span class="sxs-lookup"><span data-stu-id="44e94-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
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
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="44e94-127">客户端终结点配置由配置名称、服务终结点的绝对地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="44e94-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="44e94-128">该客户端绑定是使用适当的 `Mode` 和消息 `clientCredentialType` 配置的。</span><span class="sxs-lookup"><span data-stu-id="44e94-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="44e94-129">以下步骤演示如何开发自定义令牌提供程序并将其与 WCF 安全框架集成：</span><span class="sxs-lookup"><span data-stu-id="44e94-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="44e94-130">编写自定义令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-130">Write a custom token provider.</span></span>

     <span data-ttu-id="44e94-131">此示例实现一个用来获取用户名和密码的自定义令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="44e94-132">密码必须与用户名相匹配。</span><span class="sxs-lookup"><span data-stu-id="44e94-132">The password must match this username.</span></span> <span data-ttu-id="44e94-133">这个自定义的令牌提供程序仅用于演示目的，不建议用在实际部署中。</span><span class="sxs-lookup"><span data-stu-id="44e94-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="44e94-134">为了执行此任务，自定义令牌提供程序派生了 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 类，并重写了 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="44e94-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="44e94-135">此方法创建并返回一个新的 `UserNameSecurityToken`。</span><span class="sxs-lookup"><span data-stu-id="44e94-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. <span data-ttu-id="44e94-136">编写自定义安全令牌管理器。</span><span class="sxs-lookup"><span data-stu-id="44e94-136">Write custom security token manager.</span></span>

     <span data-ttu-id="44e94-137">使用 <xref:System.IdentityModel.Selectors.SecurityTokenManager>，可以为在 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法中传入该管理器的特定 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 创建 `CreateSecurityTokenProvider`。</span><span class="sxs-lookup"><span data-stu-id="44e94-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="44e94-138">安全令牌管理器还用于创建令牌身份验证器和令牌序列化程序，但它们不包括在此示例中。</span><span class="sxs-lookup"><span data-stu-id="44e94-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="44e94-139">在此示例中，自定义安全令牌管理器继承自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 类并重写 `CreateSecurityTokenProvider` 方法，这样，当所传递令牌的要求指示需要用户名提供程序时，将返回自定义用户名令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. <span data-ttu-id="44e94-140">编写自定义客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="44e94-140">Write a custom client credential.</span></span>

     <span data-ttu-id="44e94-141">客户端凭据类用于表示为客户端代理配置的凭据并创建一个安全令牌管理器，该管理器用于获取令牌身份验证器、令牌提供程序和令牌序列化程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. <span data-ttu-id="44e94-142">配置客户端以使用自定义客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="44e94-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="44e94-143">为了让客户端使用自定义客户端凭据，此示例删除了默认的客户端凭据类并提供了新的客户端凭据类。</span><span class="sxs-lookup"><span data-stu-id="44e94-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 <span data-ttu-id="44e94-144">在服务上，若要显示调用方信息，请使用 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>，如下面的代码示例中所示。</span><span class="sxs-lookup"><span data-stu-id="44e94-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="44e94-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 包含有关当前调用方的声明信息。</span><span class="sxs-lookup"><span data-stu-id="44e94-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="44e94-146">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="44e94-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="44e94-147">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="44e94-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="44e94-148">设置批处理文件</span><span class="sxs-lookup"><span data-stu-id="44e94-148">Setup Batch File</span></span>
 <span data-ttu-id="44e94-149">通过运行此示例随附的 Setup.bat 批处理文件，可以用相关的证书将服务器配置为运行需要基于服务器证书的安全性的自承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="44e94-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="44e94-150">必须修改此批处理文件，以便跨计算机或在非承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="44e94-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="44e94-151">下面提供了批处理文件不同节的简要概述，以便可以修改批处理文件从而在相应的配置中运行：</span><span class="sxs-lookup"><span data-stu-id="44e94-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="44e94-152">创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="44e94-152">Creating the server certificate.</span></span>

     <span data-ttu-id="44e94-153">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="44e94-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="44e94-154">`%SERVER_NAME%`变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="44e94-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="44e94-155">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="44e94-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="44e94-156">此批处理文件中的默认值为 localhost。</span><span class="sxs-lookup"><span data-stu-id="44e94-156">The default value in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="44e94-157">将服务器证书安装到客户端的受信任证书存储区中：</span><span class="sxs-lookup"><span data-stu-id="44e94-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="44e94-158">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="44e94-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="44e94-159">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="44e94-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="44e94-160">如果您已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="44e94-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> <span data-ttu-id="44e94-161">Setup.bat 批处理文件设计为通过 Windows SDK 命令提示运行。</span><span class="sxs-lookup"><span data-stu-id="44e94-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="44e94-162">这要求 MSSDK 环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="44e94-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="44e94-163">将在 Windows SDK 命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="44e94-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="44e94-164">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="44e94-164">To set up and build the sample</span></span>

1. <span data-ttu-id="44e94-165">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="44e94-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="44e94-166">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="44e94-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="44e94-167">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="44e94-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="44e94-168">在使用管理员特权打开的 Visual Studio 2012 命令提示符下，从示例安装文件夹中运行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="44e94-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="44e94-169">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="44e94-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="44e94-170">Setup.bat 批处理文件设计为在 Visual Studio 2012 命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="44e94-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="44e94-171">在 Visual Studio 2012 命令提示符下设置的 PATH 环境变量指向包含 Setup.bat 脚本所需的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="44e94-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="44e94-172">启动 service\bin 中的 service.exe。</span><span class="sxs-lookup"><span data-stu-id="44e94-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="44e94-173">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="44e94-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="44e94-174">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="44e94-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="44e94-175">在用户名提示下，键入一个用户名。</span><span class="sxs-lookup"><span data-stu-id="44e94-175">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="44e94-176">在密码提示下，使用已在用户名提示下键入的字符串。</span><span class="sxs-lookup"><span data-stu-id="44e94-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="44e94-177">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="44e94-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="44e94-178">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="44e94-178">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="44e94-179">在服务计算机上为服务二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="44e94-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="44e94-180">将服务程序文件复制到服务计算机上的服务目录。</span><span class="sxs-lookup"><span data-stu-id="44e94-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="44e94-181">另外，将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="44e94-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="44e94-182">必须具有一个其主题名称中包含计算机的完全限定域名的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="44e94-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="44e94-183">必须更新 Service.exe.config 文件以反映此新证书名称。</span><span class="sxs-lookup"><span data-stu-id="44e94-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="44e94-184">可以通过修改 Setup.bat 批处理文件来创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="44e94-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="44e94-185">请注意，必须使用管理员权限打开 Visual Studio 开发人员命令提示的 setup.bat 文件。</span><span class="sxs-lookup"><span data-stu-id="44e94-185">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="44e94-186">必须将 `%SERVER_NAME%` 变量设置为用于承载服务的计算机的完全限定的主机名。</span><span class="sxs-lookup"><span data-stu-id="44e94-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="44e94-187">将服务器证书复制到客户端的 CurrentUser-TrustedPeople 存储中。</span><span class="sxs-lookup"><span data-stu-id="44e94-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="44e94-188">当服务器证书是由客户端的受信任颁发者颁发时，不必执行此操作。</span><span class="sxs-lookup"><span data-stu-id="44e94-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="44e94-189">在服务计算机的 Service.exe.config 文件中，更改基址的值以指定一个完全限定的计算机名称，而不是 localhost。</span><span class="sxs-lookup"><span data-stu-id="44e94-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="44e94-190">在服务计算机上，在命令提示符下运行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="44e94-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="44e94-191">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="44e94-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="44e94-192">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="44e94-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="44e94-193">在客户端计算机上，从命令提示窗口中启动 `Client.exe`。</span><span class="sxs-lookup"><span data-stu-id="44e94-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="44e94-194">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="44e94-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="44e94-195">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="44e94-195">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="44e94-196">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="44e94-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
