---
title: 匿名消息安全
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 7ba64f28d621dad51957438025de22827405dd87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558662"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="9e79b-102">匿名消息安全</span><span class="sxs-lookup"><span data-stu-id="9e79b-102">Message Security Anonymous</span></span>
<span data-ttu-id="9e79b-103">消息安全匿名示例演示如何实现 Windows Communication Foundation (WCF) 应用程序，该应用程序使用不带客户端身份验证的消息级安全性，但需要使用服务器的 x.509 证书进行服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="9e79b-103">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="9e79b-104">客户端与服务器之间的所有应用程序消息均已进行签名和加密。</span><span class="sxs-lookup"><span data-stu-id="9e79b-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="9e79b-105">此示例基于 [WSHttpBinding](wshttpbinding.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="9e79b-105">This sample is based on the [WSHttpBinding](wshttpbinding.md) sample.</span></span> <span data-ttu-id="9e79b-106">此示例由客户端控制台程序 (.exe) 和 Internet 信息服务 (IIS) 所承载的服务库 (.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="9e79b-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="9e79b-107">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="9e79b-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="9e79b-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="9e79b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="9e79b-109">如果不对客户端进行身份验证，则本示例向返回 `True` 的计算器接口添加新运算。</span><span class="sxs-lookup"><span data-stu-id="9e79b-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 <span data-ttu-id="9e79b-110">服务公开单一终结点，以便与使用配置文件 (Web.config) 定义的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="9e79b-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="9e79b-111">终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="9e79b-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="9e79b-112">此绑定是用 `wsHttpBinding` 绑定配置的。</span><span class="sxs-lookup"><span data-stu-id="9e79b-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="9e79b-113">`wsHttpBinding` 绑定的默认安全模式是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="9e79b-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="9e79b-114">`clientCredentialType` 属性设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="9e79b-114">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="9e79b-115">要用于服务身份验证的凭据在中指定 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="9e79b-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="9e79b-116">服务器证书包含的 `SubjectName` 的值必须与为 `findValue` 属性指定的值相同，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="9e79b-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="9e79b-117">客户端终结点配置由服务终结点的绝对地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="9e79b-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="9e79b-118">`wsHttpBinding` 绑定的客户端安全模式为 `Message`。</span><span class="sxs-lookup"><span data-stu-id="9e79b-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="9e79b-119">`clientCredentialType` 属性设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="9e79b-119">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="9e79b-120">本示例将 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 设置为 <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> 以便对服务的证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="9e79b-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="9e79b-121">这是在`behaviors`一节中的客户端的 App.config 文件中实现的。</span><span class="sxs-lookup"><span data-stu-id="9e79b-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="9e79b-122">这意味着如果证书在用户的“受信任人”存储中，则信任此证书，而不对证书的颁发者链执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="9e79b-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="9e79b-123">此处使用的设置是为了方便起见，使示例可以不需要证书颁发机构 (CA) 颁发的证书就能运行。</span><span class="sxs-lookup"><span data-stu-id="9e79b-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="9e79b-124">此设置没有默认设置 ChainTrust 安全。</span><span class="sxs-lookup"><span data-stu-id="9e79b-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="9e79b-125">在生产代码中使用 `PeerOrChainTrust` 之前，应仔细考虑此设置的安全含义。</span><span class="sxs-lookup"><span data-stu-id="9e79b-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="9e79b-126">客户端实现添加对方法的调用 `IsCallerAnonymous` ，否则不同于 [WSHttpBinding](wshttpbinding.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="9e79b-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](wshttpbinding.md) sample.</span></span>

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="9e79b-127">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="9e79b-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9e79b-128">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="9e79b-128">Press ENTER in the client window to shut down the client.</span></span>

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="9e79b-129">“匿名消息安全”示例随附的 Setup.bat 批处理文件使您可以用相关的证书来配置服务器，以运行所承载的需要基于证书的安全的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e79b-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="9e79b-130">可以在两种模式中运行此批处理文件。</span><span class="sxs-lookup"><span data-stu-id="9e79b-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="9e79b-131">若要在单一计算机模式下运行该批处理文件，请在命令行键入 `setup.bat`。</span><span class="sxs-lookup"><span data-stu-id="9e79b-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="9e79b-132">若要在服务模式中运行此文件，请键入 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="9e79b-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="9e79b-133">跨计算机运行示例时，请使用此模式。</span><span class="sxs-lookup"><span data-stu-id="9e79b-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="9e79b-134">有关详细信息，请参见本主题末尾的设置过程。</span><span class="sxs-lookup"><span data-stu-id="9e79b-134">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="9e79b-135">下面提供了有关此批处理文件的不同部分的简要概述：</span><span class="sxs-lookup"><span data-stu-id="9e79b-135">The following provides a brief overview of the different sections of the batch files:</span></span>

- <span data-ttu-id="9e79b-136">创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="9e79b-136">Creating the server certificate.</span></span>

     <span data-ttu-id="9e79b-137">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="9e79b-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="9e79b-138">%SERVER_NAME% 变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="9e79b-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="9e79b-139">该证书存储在 LocalMachine 存储区中。</span><span class="sxs-lookup"><span data-stu-id="9e79b-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="9e79b-140">如果用服务参数（如 `setup.bat service`）运行 setup 批处理文件，则 %SERVER_NAME% 包含计算机的完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="9e79b-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="9e79b-141">否则，它默认为 localhost。</span><span class="sxs-lookup"><span data-stu-id="9e79b-141">Otherwise it defaults to localhost.</span></span>

- <span data-ttu-id="9e79b-142">将服务器证书安装到客户端的受信任证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="9e79b-142">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="9e79b-143">以下行将服务器证书复制到客户端的受信任人存储中。</span><span class="sxs-lookup"><span data-stu-id="9e79b-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="9e79b-144">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="9e79b-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="9e79b-145">如果已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="9e79b-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="9e79b-146">授予对证书私钥的权限。</span><span class="sxs-lookup"><span data-stu-id="9e79b-146">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="9e79b-147">Setup.bat 批处理文件中的以下行使 ASP.NET 工作进程帐户可以访问存储在 LocalMachine 存储区中的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="9e79b-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> <span data-ttu-id="9e79b-148">如果你使用的是非美国Windows 英文版你必须编辑 Setup.bat 文件，并将 `NT AUTHORITY\NETWORK SERVICE` 帐户名称替换为你的区域性等效项。</span><span class="sxs-lookup"><span data-stu-id="9e79b-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9e79b-149">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="9e79b-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="9e79b-150">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9e79b-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="9e79b-151">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="9e79b-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9e79b-152">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="9e79b-152">To run the sample on the same computer</span></span>

1. <span data-ttu-id="9e79b-153">请确保路径包括 Makecert.exe 和 FindPrivateKey.exe 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9e79b-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2. <span data-ttu-id="9e79b-154">从 Visual Studio 的开发人员命令提示中的示例安装文件夹运行 Setup.bat，并使用管理员权限运行。</span><span class="sxs-lookup"><span data-stu-id="9e79b-154">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="9e79b-155">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="9e79b-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9e79b-156">安装批处理文件设计为从 Visual Studio 的开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="9e79b-156">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="9e79b-157">这要求路径环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="9e79b-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="9e79b-158">在 Visual Studio 开发人员命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="9e79b-158">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="9e79b-159">通过输入地址来验证使用浏览器访问服务 `http://localhost/servicemodelsamples/service.svc` 。</span><span class="sxs-lookup"><span data-stu-id="9e79b-159">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4. <span data-ttu-id="9e79b-160">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="9e79b-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="9e79b-161">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="9e79b-161">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="9e79b-162">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="9e79b-162">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9e79b-163">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="9e79b-163">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="9e79b-164">在服务计算机上创建目录。</span><span class="sxs-lookup"><span data-stu-id="9e79b-164">Create a directory on the service computer.</span></span> <span data-ttu-id="9e79b-165">使用 Internet Information Services (IIS) 管理工具为此目录创建名为 servicemodelsamples 的虚拟应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e79b-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="9e79b-166">将服务程序文件从 \inetpub\wwwroot\servicemodelsamples 复制到服务计算机上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="9e79b-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="9e79b-167">确保复制 \bin 子目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="9e79b-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="9e79b-168">另外，将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="9e79b-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="9e79b-169">在客户端计算机上为这些客户端二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="9e79b-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="9e79b-170">将客户端程序文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="9e79b-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="9e79b-171">另外，将 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 文件复制到客户端上。</span><span class="sxs-lookup"><span data-stu-id="9e79b-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="9e79b-172">在服务器上， `setup.bat service` 在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="9e79b-172">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="9e79b-173">使用参数运行将使用 `setup.bat` `service` 计算机的完全限定的域名创建一个服务证书，并将服务证书导出到名为的文件。</span><span class="sxs-lookup"><span data-stu-id="9e79b-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="9e79b-174">编辑 Web.config，以反映) 的属性中 (新的证书名称，该名称与 `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 计算机的完全限定域名相同。</span><span class="sxs-lookup"><span data-stu-id="9e79b-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="9e79b-175">将服务目录中的 Service.cer 文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="9e79b-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="9e79b-176">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="9e79b-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="9e79b-177">在客户端上，在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="9e79b-177">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="9e79b-178">这会将 Service.cer 文件中的服务证书导入 CurrentUser – TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="9e79b-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="9e79b-179">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="9e79b-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="9e79b-180">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="9e79b-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9e79b-181">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="9e79b-181">To clean up after the sample</span></span>  
  
- <span data-ttu-id="9e79b-182">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="9e79b-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e79b-183">此脚本不会在跨计算机运行此示例时移除客户端上的服务证书。</span><span class="sxs-lookup"><span data-stu-id="9e79b-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="9e79b-184">如果你已运行 Windows Communication Foundation 跨计算机使用证书 (WCF) 示例，请确保清除已安装在 CurrentUser-TrustedPeople 存储中的服务证书。</span><span class="sxs-lookup"><span data-stu-id="9e79b-184">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="9e79b-185">为此，请使用以下命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`。</span><span class="sxs-lookup"><span data-stu-id="9e79b-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>
