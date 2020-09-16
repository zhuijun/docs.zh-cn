---
title: 用户名密码验证程序
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 4ad365061e6a0f3178650699febd6c18cdd14205
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553108"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="21d3f-102">用户名密码验证程序</span><span class="sxs-lookup"><span data-stu-id="21d3f-102">User Name Password Validator</span></span>
<span data-ttu-id="21d3f-103">此示例演示如何实现自定义 UserNamePassword 验证程序。</span><span class="sxs-lookup"><span data-stu-id="21d3f-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="21d3f-104">这在以下情况中非常有用：所有内置 UserNamePassword 验证模式均不符合应用程序的需求；例如，当用户名/密码对存储在某个外部存储区（如数据库）中时。</span><span class="sxs-lookup"><span data-stu-id="21d3f-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="21d3f-105">此示例显示了一个具有自定义验证程序（可检查两个特定用户名/密码对）的服务。</span><span class="sxs-lookup"><span data-stu-id="21d3f-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="21d3f-106">客户端使用此种用户名/密码对来对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="21d3f-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21d3f-107">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="21d3f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="21d3f-108">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="21d3f-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="21d3f-109">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21d3f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21d3f-110">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="21d3f-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="21d3f-111">由于任何人都可以构建使用自定义验证程序接受的用户名/密码对的用户名凭据，因此标准 UserNamePassword 验证程序提供的默认行为比服务更安全。</span><span class="sxs-lookup"><span data-stu-id="21d3f-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="21d3f-112">标准 UserNamePassword 验证程序尝试将提供的用户名/密码对映射到 Windows 帐户，如果此映射失败则身份验证失败。</span><span class="sxs-lookup"><span data-stu-id="21d3f-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="21d3f-113">此示例中的自定义 UserNamePassword 验证程序不得用于成品代码，仅作演示使用。</span><span class="sxs-lookup"><span data-stu-id="21d3f-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="21d3f-114">概括而言，此示例演示：</span><span class="sxs-lookup"><span data-stu-id="21d3f-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="21d3f-115">如何使用用户名令牌对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="21d3f-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="21d3f-116">服务器如何根据自定义 UserNamePasswordValidator 验证客户端凭据，以及如何将用户名和密码验证逻辑中的自定义错误传播到客户端。</span><span class="sxs-lookup"><span data-stu-id="21d3f-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="21d3f-117">如何使用服务器的 X.509 证书对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="21d3f-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="21d3f-118">服务公开一个终结点，以便与使用配置文件定义的服务进行通信，App.config。终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="21d3f-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="21d3f-119">绑定使用 `wsHttpBinding` 默认为使用 WS 安全性和用户名身份验证的标准配置。</span><span class="sxs-lookup"><span data-stu-id="21d3f-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="21d3f-120">服务行为指定用以验证客户端用户名/密码对的 `Custom` 模式以及验证程序类的类型。</span><span class="sxs-lookup"><span data-stu-id="21d3f-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="21d3f-121">该行为还使用 `serviceCertificate` 元素指定服务器证书。</span><span class="sxs-lookup"><span data-stu-id="21d3f-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="21d3f-122">服务器证书必须包含与中相同的值 `SubjectName` `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="21d3f-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="21d3f-123">客户端终结点配置由配置名称、服务终结点的绝对地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="21d3f-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="21d3f-124">该客户端绑定是使用适当的模式和消息 `clientCredentialType` 配置的。</span><span class="sxs-lookup"><span data-stu-id="21d3f-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="21d3f-125">客户端实现提示用户输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="21d3f-125">The client implementation prompts the user to enter a username and password.</span></span>

```csharp
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
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
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 <span data-ttu-id="21d3f-126">此示例使用自定义 UserNamePasswordValidator 来验证用户名/密码对。</span><span class="sxs-lookup"><span data-stu-id="21d3f-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="21d3f-127">此示例实现从 `CustomUserNamePasswordValidator` 派生的 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>。</span><span class="sxs-lookup"><span data-stu-id="21d3f-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="21d3f-128">有关更多信息，请参阅 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的文档。</span><span class="sxs-lookup"><span data-stu-id="21d3f-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="21d3f-129">此特定自定义验证程序示例实现 `Validate` 方法，以接受两个特定用户名/密码对，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="21d3f-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

```csharp
public class CustomUserNameValidator : UserNamePasswordValidator
{
 // This method validates users. It allows in two users,
 // test1 and test2 with passwords 1tset and 2tset respectively.
 // This code is for illustration purposes only and
 // MUST NOT be used in a production environment because it
 // is NOT secure.
 public override void Validate(string userName, string password)
 {
  if (null == userName || null == password)
  {
   throw new ArgumentNullException();
  }

  if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
  {
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 <span data-ttu-id="21d3f-130">在服务代码中实现验证程序后，必须通知服务主机关于要使用的验证程序实例的信息。</span><span class="sxs-lookup"><span data-stu-id="21d3f-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="21d3f-131">这是使用以下代码完成的。</span><span class="sxs-lookup"><span data-stu-id="21d3f-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="21d3f-132">或者，您可以在如下配置中执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="21d3f-132">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
   </serviceCredentials>
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="21d3f-133">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="21d3f-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="21d3f-134">客户端应成功地调用所有方法。</span><span class="sxs-lookup"><span data-stu-id="21d3f-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="21d3f-135">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="21d3f-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="21d3f-136">设置批处理文件</span><span class="sxs-lookup"><span data-stu-id="21d3f-136">Setup Batch File</span></span>
 <span data-ttu-id="21d3f-137">通过运行此示例随附的 Setup.bat 批处理文件，可以用相关的证书将服务器配置为运行需要基于服务器证书的安全性的自承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="21d3f-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="21d3f-138">此批处理文件必须经过修改才能跨计算机或在非自承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="21d3f-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="21d3f-139">下面提供了批处理文件不同节的简要概述，以便可以修改批处理文件从而在相应的配置中运行。</span><span class="sxs-lookup"><span data-stu-id="21d3f-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="21d3f-140">创建服务器证书：</span><span class="sxs-lookup"><span data-stu-id="21d3f-140">Creating the server certificate:</span></span>

     <span data-ttu-id="21d3f-141">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="21d3f-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="21d3f-142">%SERVER_NAME% 变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="21d3f-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="21d3f-143">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="21d3f-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="21d3f-144">默认值为 localhost。</span><span class="sxs-lookup"><span data-stu-id="21d3f-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="21d3f-145">将服务器证书安装到客户端的受信任证书存储区中：</span><span class="sxs-lookup"><span data-stu-id="21d3f-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="21d3f-146">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="21d3f-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="21d3f-147">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="21d3f-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="21d3f-148">如果您已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="21d3f-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="21d3f-149">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="21d3f-149">To set up and build the sample</span></span>

1. <span data-ttu-id="21d3f-150">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="21d3f-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="21d3f-151">若要用单一计算机配置或跨计算机配置来运行示例，请按照下列说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="21d3f-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="21d3f-152">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="21d3f-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="21d3f-153">从 Visual Studio 2012 命令提示符下的示例安装文件夹中运行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="21d3f-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="21d3f-154">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="21d3f-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="21d3f-155">Setup.bat 批处理文件设计为在 Visual Studio 2012 命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="21d3f-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="21d3f-156">在 Visual Studio 2012 命令提示符下设置的 PATH 环境变量指向包含 Setup.bat 脚本所需的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="21d3f-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="21d3f-157">启动 service\bin 中的 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="21d3f-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="21d3f-158">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="21d3f-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="21d3f-159">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="21d3f-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="21d3f-160">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="21d3f-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="21d3f-161">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="21d3f-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="21d3f-162">在服务计算机上为服务二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="21d3f-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="21d3f-163">将服务程序文件复制到服务计算机上的服务目录。</span><span class="sxs-lookup"><span data-stu-id="21d3f-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="21d3f-164">另外，将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="21d3f-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="21d3f-165">需要有一个其主题名称中包含计算机的完全限定域名的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="21d3f-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="21d3f-166">必须更新服务器的配置文件以反映此新证书名称。</span><span class="sxs-lookup"><span data-stu-id="21d3f-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="21d3f-167">将服务器证书复制到客户端的 CurrentUser-TrustedPeople 存储中。</span><span class="sxs-lookup"><span data-stu-id="21d3f-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="21d3f-168">只有当服务器证书不是由受信任的颁发者颁发的情况下才需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="21d3f-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="21d3f-169">在服务计算机的 App.config 文件中，更改基址的值以指定一个完全限定的计算机名称，而不是 localhost。</span><span class="sxs-lookup"><span data-stu-id="21d3f-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="21d3f-170">在服务计算机上，从命令提示符窗口中启动 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="21d3f-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="21d3f-171">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="21d3f-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="21d3f-172">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="21d3f-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="21d3f-173">在客户端计算机上，从命令提示符窗口中启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="21d3f-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="21d3f-174">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="21d3f-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="21d3f-175">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="21d3f-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="21d3f-176">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="21d3f-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="21d3f-177">这将从证书存储区中移除服务器证书。</span><span class="sxs-lookup"><span data-stu-id="21d3f-177">This removes the server certificate from the certificate store.</span></span>
