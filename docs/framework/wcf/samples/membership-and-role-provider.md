---
title: 成员资格和角色提供程序
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: e532f35a2c4cd9f53006c088956eadff616d2005
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543584"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="d45a0-102">成员资格和角色提供程序</span><span class="sxs-lookup"><span data-stu-id="d45a0-102">Membership and Role Provider</span></span>
<span data-ttu-id="d45a0-103">成员资格和角色提供程序示例演示服务如何使用 ASP.NET 成员资格和角色提供程序来对客户端进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="d45a0-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="d45a0-104">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="d45a0-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d45a0-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="d45a0-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d45a0-106">此示例演示：</span><span class="sxs-lookup"><span data-stu-id="d45a0-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="d45a0-107">客户端如何使用用户名和密码组合进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d45a0-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="d45a0-108">服务器可以根据 ASP.NET 的成员资格提供程序来验证客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="d45a0-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="d45a0-109">如何使用服务器的 X.509 证书对该服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d45a0-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="d45a0-110">服务器可以使用 ASP.NET 角色提供程序将经过身份验证的客户端映射到角色。</span><span class="sxs-lookup"><span data-stu-id="d45a0-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="d45a0-111">服务器如何使用 `PrincipalPermissionAttribute` 控制对服务公开的某些方法的访问。</span><span class="sxs-lookup"><span data-stu-id="d45a0-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="d45a0-112">成员资格和角色提供程序配置为使用 SQL Server 支持的存储。</span><span class="sxs-lookup"><span data-stu-id="d45a0-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="d45a0-113">连接字符串和各个选项在服务配置文件中指定。</span><span class="sxs-lookup"><span data-stu-id="d45a0-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="d45a0-114">成员资格提供程序命名为 `SqlMembershipProvider`，而角色提供程序命名为 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="d45a0-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
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
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="d45a0-115">服务会公开一个单一终结点以便与使用 Web.config 配置文件定义的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="d45a0-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="d45a0-116">终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="d45a0-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="d45a0-117">绑定使用默认使用 Windows 身份验证的标准 `wsHttpBinding` 进行配置。</span><span class="sxs-lookup"><span data-stu-id="d45a0-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="d45a0-118">此示例将标准 `wsHttpBinding` 设置为使用用户名身份验证。</span><span class="sxs-lookup"><span data-stu-id="d45a0-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="d45a0-119">该行为指定将使用服务器证书进行服务身份验证。</span><span class="sxs-lookup"><span data-stu-id="d45a0-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="d45a0-120">服务器证书必须包含与 `SubjectName` `findValue` 配置元素中的属性相同的值 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="d45a0-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="d45a0-121">此外，该行为指定 ASP.NET 成员资格提供程序执行用户名-密码对的身份验证，并且角色映射通过指定为这两个提供程序定义的名称，由 ASP.NET 角色提供程序执行。</span><span class="sxs-lookup"><span data-stu-id="d45a0-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"
                              storeName ="My"
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d45a0-122">运行此示例时，客户端使用三个不同的用户帐户来调用各个服务操作：Alice、Bob 和 Charlie。</span><span class="sxs-lookup"><span data-stu-id="d45a0-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="d45a0-123">操作请求和响应显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="d45a0-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d45a0-124">以用户“Alice”身份执行的所有四个调用都应成功。</span><span class="sxs-lookup"><span data-stu-id="d45a0-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="d45a0-125">用户“Bob”在尝试调用 Divide 方法时会收到拒绝访问错误。</span><span class="sxs-lookup"><span data-stu-id="d45a0-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="d45a0-126">用户“Charlie”在尝试调用 Multiply 方法时会收到拒绝访问错误。</span><span class="sxs-lookup"><span data-stu-id="d45a0-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="d45a0-127">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="d45a0-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d45a0-128">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="d45a0-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d45a0-129">若要生成 c # 或 Visual Basic .NET 版本的解决方案，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="d45a0-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="d45a0-130">确保已将 ASP.NET 配置为 [数据库应用程序服务](https://go.microsoft.com/fwlink/?LinkId=94997)。</span><span class="sxs-lookup"><span data-stu-id="d45a0-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d45a0-131">如果运行的是 SQL Server Express Edition，则服务器名称为 .\SQLEXPRESS。</span><span class="sxs-lookup"><span data-stu-id="d45a0-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="d45a0-132">在配置 ASP.NET 应用程序服务数据库以及 Web.config 连接字符串时，应使用此服务器。</span><span class="sxs-lookup"><span data-stu-id="d45a0-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d45a0-133">ASP.NET 工作进程帐户必须对此步骤中创建的数据库具有权限。</span><span class="sxs-lookup"><span data-stu-id="d45a0-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="d45a0-134">使用 sqlcmd 实用工具或 SQL Server Management Studio 来完成该工作。</span><span class="sxs-lookup"><span data-stu-id="d45a0-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="d45a0-135">若要用单一计算机配置或跨计算机配置来运行示例，请按照下列说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="d45a0-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="d45a0-136">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="d45a0-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="d45a0-137">请确保路径包含 Makecert.exe 所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d45a0-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="d45a0-138">从 Visual Studio 的开发人员命令提示中的示例安装文件夹运行 Setup.bat，并使用管理员权限运行。</span><span class="sxs-lookup"><span data-stu-id="d45a0-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="d45a0-139">这将安装运行此示例所需的服务证书。</span><span class="sxs-lookup"><span data-stu-id="d45a0-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="d45a0-140">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="d45a0-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="d45a0-141">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="d45a0-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="d45a0-142">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="d45a0-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d45a0-143">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="d45a0-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="d45a0-144">在服务计算机上创建目录。</span><span class="sxs-lookup"><span data-stu-id="d45a0-144">Create a directory on the service computer.</span></span> <span data-ttu-id="d45a0-145">使用 Internet Information Services (IIS) 管理工具为此目录创建名为 servicemodelsamples 的虚拟应用程序。</span><span class="sxs-lookup"><span data-stu-id="d45a0-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="d45a0-146">将服务程序文件从 \inetpub\wwwroot\servicemodelsamples 复制到服务计算机上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="d45a0-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="d45a0-147">确保复制 \bin 子目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="d45a0-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="d45a0-148">另外，将 Setup.bat、GetComputerName.vbs 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="d45a0-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="d45a0-149">在客户端计算机上为这些客户端二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="d45a0-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="d45a0-150">将客户端程序文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="d45a0-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="d45a0-151">另外，将 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 文件复制到客户端上。</span><span class="sxs-lookup"><span data-stu-id="d45a0-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="d45a0-152">在服务器上，打开具有管理权限的 Visual Studio 开发人员命令提示，然后运行 `setup.bat service` 。</span><span class="sxs-lookup"><span data-stu-id="d45a0-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="d45a0-153">使用参数运行将使用 `setup.bat` `service` 计算机的完全限定的域名创建一个服务证书，并将服务证书导出到名为的文件。</span><span class="sxs-lookup"><span data-stu-id="d45a0-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="d45a0-154">编辑 Web.config，以反映) 的属性中 (新的证书名称，该名称与 `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 计算机的完全限定域名相同。</span><span class="sxs-lookup"><span data-stu-id="d45a0-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="d45a0-155">将服务目录中的 Service.cer 文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="d45a0-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="d45a0-156">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="d45a0-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="d45a0-157">在客户端上，使用管理权限打开 Visual Studio 开发人员命令提示，并运行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="d45a0-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="d45a0-158">这会将 Service.cer 文件中的服务证书导入 CurrentUser – TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="d45a0-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="d45a0-159">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="d45a0-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="d45a0-160">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="d45a0-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d45a0-161">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="d45a0-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="d45a0-162">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="d45a0-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d45a0-163">此脚本不会在跨计算机运行此示例时移除客户端上的服务证书。</span><span class="sxs-lookup"><span data-stu-id="d45a0-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="d45a0-164">如果你已运行 Windows Communication Foundation 跨计算机使用证书 (WCF) 示例，请确保清除已安装在 CurrentUser-TrustedPeople 存储中的服务证书。</span><span class="sxs-lookup"><span data-stu-id="d45a0-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d45a0-165">为此，请使用以下命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="d45a0-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="d45a0-166">Setup 批处理文件</span><span class="sxs-lookup"><span data-stu-id="d45a0-166">The Setup Batch File</span></span>  
 <span data-ttu-id="d45a0-167">通过运行此示例随附的 Setup.bat 批处理文件，可以用相关的证书将服务器配置为运行需要基于服务器证书的安全性的自承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="d45a0-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="d45a0-168">必须修改此批处理文件，以便跨计算机或在非承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="d45a0-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="d45a0-169">下面提供了批处理文件不同节的简要概述，以便可以修改批处理文件从而在相应的配置中运行。</span><span class="sxs-lookup"><span data-stu-id="d45a0-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="d45a0-170">创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="d45a0-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="d45a0-171">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="d45a0-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="d45a0-172">%SERVER_NAME% 变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="d45a0-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="d45a0-173">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="d45a0-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="d45a0-174">在该批处理文件中，此名称默认为 localhost。</span><span class="sxs-lookup"><span data-stu-id="d45a0-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="d45a0-175">证书存储在 LocalMachine 存储位置下的 My（个人）存储区中。</span><span class="sxs-lookup"><span data-stu-id="d45a0-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="d45a0-176">将服务器证书安装到客户端的受信任证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="d45a0-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="d45a0-177">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="d45a0-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="d45a0-178">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="d45a0-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="d45a0-179">如果已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="d45a0-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```
