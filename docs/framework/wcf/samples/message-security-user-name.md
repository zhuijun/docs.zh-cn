---
title: 用户名消息安全
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: c6b742cbb438b10b443aa8d1cfca21a80acd2afe
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558610"
---
# <a name="message-security-user-name"></a><span data-ttu-id="7a15a-102">用户名消息安全</span><span class="sxs-lookup"><span data-stu-id="7a15a-102">Message Security User Name</span></span>
<span data-ttu-id="7a15a-103">本示例演示如何实现一个应用程序，该应用程序对客户端使用具有用户名身份验证的 WS-Security，并要求使用服务器的 X.509v3 证书对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="7a15a-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="7a15a-104">客户端与服务器之间的所有应用程序消息均已进行签名和加密。</span><span class="sxs-lookup"><span data-stu-id="7a15a-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="7a15a-105">默认情况下，使用客户端提供的用户名和密码登录有效的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="7a15a-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="7a15a-106">此示例基于 [WSHttpBinding](wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="7a15a-106">This sample is based on the [WSHttpBinding](wshttpbinding.md).</span></span> <span data-ttu-id="7a15a-107">本示例由客户端控制台程序 (Client.exe) 和 Internet 信息服务 (IIS) 所承载的服务库 (Service.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="7a15a-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7a15a-108">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="7a15a-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a15a-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="7a15a-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7a15a-110">本示例还演示：</span><span class="sxs-lookup"><span data-stu-id="7a15a-110">This sample also demonstrates:</span></span>  
  
- <span data-ttu-id="7a15a-111">到 Windows 帐户的默认映射，以便可以执行其他授权。</span><span class="sxs-lookup"><span data-stu-id="7a15a-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
- <span data-ttu-id="7a15a-112">如何访问服务代码中的调用方标识信息。</span><span class="sxs-lookup"><span data-stu-id="7a15a-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="7a15a-113">服务公开一个终结点以便与服务进行通信，该终结点是使用配置文件 Web.config 来定义的。终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="7a15a-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7a15a-114">绑定是使用标准配置的 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ，默认情况下使用消息安全性。</span><span class="sxs-lookup"><span data-stu-id="7a15a-114">The binding is configured with a standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="7a15a-115">此示例将标准设置 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 为使用客户端用户名身份验证。</span><span class="sxs-lookup"><span data-stu-id="7a15a-115">This sample sets the standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="7a15a-116">该行为指定使用用户凭据对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="7a15a-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="7a15a-117">服务器证书必须包含与中的属性相同的使用者名称值 `findValue` [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="7a15a-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
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
</system.serviceModel>  
```  
  
 <span data-ttu-id="7a15a-118">客户端终结点配置由服务终结点的绝对地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="7a15a-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="7a15a-119">该客户端绑定是使用相应的 `securityMode` 和 `authenticationMode` 配置的。</span><span class="sxs-lookup"><span data-stu-id="7a15a-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="7a15a-120">在跨计算机方案中运行时，必须相应更改服务终结点地址。</span><span class="sxs-lookup"><span data-stu-id="7a15a-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7a15a-121">客户端实现设置要使用的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="7a15a-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="7a15a-122">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="7a15a-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7a15a-123">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="7a15a-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7a15a-124">通过运行消息安全示例随附的 Setup.bat 批处理文件，您可以用相关的证书将服务器配置为运行承载的应用程序，这些应用程序需要基于证书的安全性。</span><span class="sxs-lookup"><span data-stu-id="7a15a-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="7a15a-125">可以在两种模式中运行此批处理文件。</span><span class="sxs-lookup"><span data-stu-id="7a15a-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="7a15a-126">若要在单一计算机模式下运行该批处理文件，请在命令行键入 `setup.bat`。</span><span class="sxs-lookup"><span data-stu-id="7a15a-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="7a15a-127">若要在服务模式下运行该批处理文件，请键入 `setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="7a15a-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="7a15a-128">跨计算机运行示例时，请使用此模式。</span><span class="sxs-lookup"><span data-stu-id="7a15a-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="7a15a-129">有关详细信息，请参见本主题末尾的设置过程。</span><span class="sxs-lookup"><span data-stu-id="7a15a-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="7a15a-130">下面提供该批处理文件不同部分的简要概述。</span><span class="sxs-lookup"><span data-stu-id="7a15a-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="7a15a-131">创建服务器证书</span><span class="sxs-lookup"><span data-stu-id="7a15a-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="7a15a-132">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="7a15a-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="7a15a-133">%SERVER_NAME% 变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="7a15a-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="7a15a-134">该证书存储在 LocalMachine 存储区中。</span><span class="sxs-lookup"><span data-stu-id="7a15a-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="7a15a-135">如果用服务自变量（如 `setup.bat service`）运行 Setup.bat 批处理文件，则 %SERVER_NAME% 包含计算机的完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="7a15a-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="7a15a-136">否则，它默认为 localhost。</span><span class="sxs-lookup"><span data-stu-id="7a15a-136">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="7a15a-137">将服务器证书安装到客户端的受信任证书存储区中</span><span class="sxs-lookup"><span data-stu-id="7a15a-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="7a15a-138">以下行将服务器证书复制到客户端的受信任人存储中。</span><span class="sxs-lookup"><span data-stu-id="7a15a-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7a15a-139">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="7a15a-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7a15a-140">如果已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="7a15a-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="7a15a-141">授予对证书私钥的权限</span><span class="sxs-lookup"><span data-stu-id="7a15a-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="7a15a-142">Setup.bat 批处理文件中的以下行使 ASP.NET 工作进程帐户可以访问存储在 LocalMachine 存储区中的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="7a15a-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="7a15a-143">如果你使用的是非美国Windows 英文版你必须编辑 Setup.bat 文件，并将 `NT AUTHORITY\NETWORK SERVICE` 帐户名称替换为你的区域性等效项。</span><span class="sxs-lookup"><span data-stu-id="7a15a-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7a15a-144">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="7a15a-144">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7a15a-145">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7a15a-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7a15a-146">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7a15a-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7a15a-147">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="7a15a-147">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="7a15a-148">请确保路径包括 Makecert.exe 和 FindPrivateKey.exe 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7a15a-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2. <span data-ttu-id="7a15a-149">从 Visual Studio 的开发人员命令提示中的示例安装文件夹运行 Setup.bat，并使用管理员权限打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7a15a-149">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="7a15a-150">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="7a15a-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7a15a-151">Setup.bat 批处理文件设计为从 Visual Studio 的开发人员命令提示运行。</span><span class="sxs-lookup"><span data-stu-id="7a15a-151">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="7a15a-152">这要求路径环境变量指向 SDK 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="7a15a-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="7a15a-153">在 Visual Studio 开发人员命令提示中自动设置此环境变量。</span><span class="sxs-lookup"><span data-stu-id="7a15a-153">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="7a15a-154">通过输入地址来验证使用浏览器访问服务 `http://localhost/servicemodelsamples/service.svc` 。</span><span class="sxs-lookup"><span data-stu-id="7a15a-154">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>
  
4. <span data-ttu-id="7a15a-155">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="7a15a-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="7a15a-156">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="7a15a-156">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="7a15a-157">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="7a15a-157">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="7a15a-158">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="7a15a-158">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="7a15a-159">在服务计算机上创建目录。</span><span class="sxs-lookup"><span data-stu-id="7a15a-159">Create a directory on the service computer.</span></span> <span data-ttu-id="7a15a-160">使用 Internet Information Services 管理工具为此目录创建名为 servicemodelsamples 的虚拟应用程序。</span><span class="sxs-lookup"><span data-stu-id="7a15a-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2. <span data-ttu-id="7a15a-161">将服务程序文件从 \inetpub\wwwroot\servicemodelsamples 复制到服务计算机上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="7a15a-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="7a15a-162">确保复制 \bin 子目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="7a15a-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="7a15a-163">另外，将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="7a15a-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="7a15a-164">在客户端计算机上为这些客户端二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="7a15a-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="7a15a-165">将客户端程序文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="7a15a-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="7a15a-166">另外，将 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 文件复制到客户端上。</span><span class="sxs-lookup"><span data-stu-id="7a15a-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="7a15a-167">在服务器上， `setup.bat service` 在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="7a15a-167">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="7a15a-168">使用参数运行将使用 `setup.bat` `service` 计算机的完全限定的域名创建一个服务证书，并将服务证书导出到名为的文件。</span><span class="sxs-lookup"><span data-stu-id="7a15a-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="7a15a-169">编辑 Web.config 以反映新的证书名称（在 serviceCertificate 元素的 findValue 属性中），该名称与计算机的完全限定域名相同。</span><span class="sxs-lookup"><span data-stu-id="7a15a-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7. <span data-ttu-id="7a15a-170">将服务目录中的 Service.cer 文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="7a15a-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="7a15a-171">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="7a15a-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="7a15a-172">在客户端上，在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="7a15a-172">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="7a15a-173">这会将 Service.cer 文件中的服务证书导入 CurrentUser – TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="7a15a-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="7a15a-174">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="7a15a-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="7a15a-175">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="7a15a-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7a15a-176">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="7a15a-176">To clean up after the sample</span></span>  
  
- <span data-ttu-id="7a15a-177">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="7a15a-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7a15a-178">此脚本不会在跨计算机运行此示例时移除客户端上的服务证书。</span><span class="sxs-lookup"><span data-stu-id="7a15a-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="7a15a-179">如果你已运行 Windows Communication Foundation 跨计算机使用证书 (WCF) 示例，请确保清除已安装在 CurrentUser-TrustedPeople 存储中的服务证书。</span><span class="sxs-lookup"><span data-stu-id="7a15a-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="7a15a-180">为此，请使用以下命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="7a15a-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
