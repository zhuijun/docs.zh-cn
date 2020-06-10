---
title: X.509 证书验证程序
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 32d99b93ef014967aa04bc70f73fbd2ebcfe2c60
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594824"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="ff784-102">X.509 证书验证程序</span><span class="sxs-lookup"><span data-stu-id="ff784-102">X.509 Certificate Validator</span></span>

<span data-ttu-id="ff784-103">此示例演示如何实现自定义 X.509 证书验证程序。</span><span class="sxs-lookup"><span data-stu-id="ff784-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="ff784-104">当内置的 X.509 证书验证模式都不能满足应用程序的要求时，实现自定义证书验证程序很有用。</span><span class="sxs-lookup"><span data-stu-id="ff784-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="ff784-105">此示例演示了具有自定义验证程序的服务，该验证程序接受自行颁发的证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="ff784-106">客户端使用此类证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ff784-106">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="ff784-107">注意：因为任何人都可以构造自行颁发的证书，所以服务使用的自定义验证程序的安全性低于 ChainTrust X509CertificateValidationMode 提供的默认行为。</span><span class="sxs-lookup"><span data-stu-id="ff784-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="ff784-108">在成品代码中使用此验证逻辑之前，应慎重考虑这样做的安全隐患。</span><span class="sxs-lookup"><span data-stu-id="ff784-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="ff784-109">概括而言，此示例演示：</span><span class="sxs-lookup"><span data-stu-id="ff784-109">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="ff784-110">如何使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ff784-110">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="ff784-111">服务器如何根据自定义 X509CertificateValidator 验证客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="ff784-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="ff784-112">如何使用服务器的 X.509 证书对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ff784-112">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="ff784-113">服务公开一个终结点，以便与使用配置文件 App.config 定义的服务进行通信。终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="ff784-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ff784-114">绑定配置为使用 `wsHttpBinding` 默认为使用 `WSSecurity` 和客户端证书身份验证的标准。</span><span class="sxs-lookup"><span data-stu-id="ff784-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="ff784-115">服务行为指定对客户端 X.509 证书进行验证的“自定义”模式以及验证程序类的类型。</span><span class="sxs-lookup"><span data-stu-id="ff784-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="ff784-116">该行为还使用 serviceCertificate 元素指定服务器证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="ff784-117">服务器证书必须包含与中相同的值 `SubjectName` `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="ff784-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="ff784-118">客户端终结点配置由配置名称、服务终结点的绝对地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="ff784-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="ff784-119">该客户端绑定是使用适当的模式和消息 `clientCredentialType` 配置的。</span><span class="sxs-lookup"><span data-stu-id="ff784-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

<span data-ttu-id="ff784-120">客户端实现设置要使用的客户端证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-120">The client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

<span data-ttu-id="ff784-121">此示例使用自定义 X509CertificateValidator 来验证证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="ff784-122">此示例实现从 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 派生的 CustomX509CertificateValidator。</span><span class="sxs-lookup"><span data-stu-id="ff784-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="ff784-123">有关更多信息，请参见有关 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 的文档。</span><span class="sxs-lookup"><span data-stu-id="ff784-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="ff784-124">这个特定的自定义验证程序示例实现了 Validate 方法，可以接受自行颁发的任何 X.509 证书，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="ff784-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 <span data-ttu-id="ff784-125">在服务代码中实现验证程序后，必须通知服务主机关于要使用的验证程序实例的信息。</span><span class="sxs-lookup"><span data-stu-id="ff784-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="ff784-126">这是使用以下代码完成的。</span><span class="sxs-lookup"><span data-stu-id="ff784-126">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="ff784-127">或者，您可以在如下配置中执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="ff784-127">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="ff784-128">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="ff784-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ff784-129">客户端应成功地调用所有方法。</span><span class="sxs-lookup"><span data-stu-id="ff784-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="ff784-130">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="ff784-130">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="ff784-131">设置批处理文件</span><span class="sxs-lookup"><span data-stu-id="ff784-131">Setup Batch File</span></span>

<span data-ttu-id="ff784-132">通过运行此示例随附的 Setup.bat 批处理文件，可以用相关的证书将服务器配置为运行需要基于服务器证书的安全性的自承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="ff784-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="ff784-133">必须修改此批处理文件，以便跨计算机或在非承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="ff784-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="ff784-134">下面提供了批处理文件不同节的简要概述，以便可以修改批处理文件从而在相应的配置中运行：</span><span class="sxs-lookup"><span data-stu-id="ff784-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="ff784-135">创建服务器证书：</span><span class="sxs-lookup"><span data-stu-id="ff784-135">Creating the server certificate:</span></span>

     <span data-ttu-id="ff784-136">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ff784-137">%SERVER_NAME% 变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="ff784-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="ff784-138">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="ff784-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ff784-139">默认值为 localhost。</span><span class="sxs-lookup"><span data-stu-id="ff784-139">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="ff784-140">将服务器证书安装到客户端的受信任证书存储区中：</span><span class="sxs-lookup"><span data-stu-id="ff784-140">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="ff784-141">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="ff784-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ff784-142">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="ff784-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ff784-143">如果您已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="ff784-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="ff784-144">创建客户端证书：</span><span class="sxs-lookup"><span data-stu-id="ff784-144">Creating the client certificate:</span></span>

     <span data-ttu-id="ff784-145">Setup.bat 批处理文件中的以下行创建将要使用的客户端证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="ff784-146">%USER_NAME% 变量指定客户端名称。</span><span class="sxs-lookup"><span data-stu-id="ff784-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="ff784-147">此值设置为“test1”，因为这是客户端代码查找的名称。</span><span class="sxs-lookup"><span data-stu-id="ff784-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="ff784-148">如果更改 %USER_NAME% 的值，必须更改 Client.cs 源文件中对应的值并重新生成客户端。</span><span class="sxs-lookup"><span data-stu-id="ff784-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="ff784-149">证书存储在 CurrentUser 存储位置下的 My（个人）存储区中。</span><span class="sxs-lookup"><span data-stu-id="ff784-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="ff784-150">将客户端证书安装到服务器的受信任证书存储区中：</span><span class="sxs-lookup"><span data-stu-id="ff784-150">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="ff784-151">Setup.bat 批处理文件中的以下行将客户端证书复制到受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="ff784-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="ff784-152">因为服务器系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="ff784-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="ff784-153">如果您已经拥有一个证书，该证书来源于受信任的根证书（例如由 Microsoft 颁发的证书），则不需要执行使用客户端证书填充服务器证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="ff784-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ff784-154">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="ff784-154">To set up and build the sample</span></span>

1. <span data-ttu-id="ff784-155">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ff784-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="ff784-156">若要用单一计算机配置或跨计算机配置来运行示例，请按照下列说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ff784-156">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ff784-157">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="ff784-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="ff784-158">从使用管理员特权打开的 Visual Studio 2012 命令提示符下的示例安装文件夹中运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="ff784-158">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ff784-159">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-159">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ff784-160">设置 bat 批处理文件设计为在 Visual Studio 2012 命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="ff784-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="ff784-161">在 Visual Studio 2012 命令提示符中设置的 PATH 环境变量指向包含安装程序 bat 脚本所需的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="ff784-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="ff784-162">启动 service\bin 中的 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="ff784-162">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="ff784-163">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="ff784-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ff784-164">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="ff784-164">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="ff784-165">如果客户端和服务无法进行通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="ff784-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ff784-166">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="ff784-166">To run the sample across computers</span></span>

1. <span data-ttu-id="ff784-167">在服务计算机上创建目录。</span><span class="sxs-lookup"><span data-stu-id="ff784-167">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="ff784-168">从 \service\bin 中将服务程序文件复制到服务计算机上的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="ff784-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="ff784-169">另外，将 Setup.bat、Cleanup.bat、GetComputerName.vbs 和 ImportClientCert.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="ff784-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="ff784-170">在客户端计算机上为这些客户端二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="ff784-170">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="ff784-171">将客户端程序文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="ff784-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="ff784-172">另外，将 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 文件复制到客户端上。</span><span class="sxs-lookup"><span data-stu-id="ff784-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="ff784-173">在服务器上， `setup.bat service` 在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="ff784-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="ff784-174">使用参数运行将使用 `setup.bat` `service` 计算机的完全限定的域名创建一个服务证书，并将服务证书导出到名为的文件。</span><span class="sxs-lookup"><span data-stu-id="ff784-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="ff784-175">编辑 setup.exe，以反映新的证书名称（在的属性中），该名称与 `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 计算机的完全限定域名相同。</span><span class="sxs-lookup"><span data-stu-id="ff784-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="ff784-176">还要将元素中的计算机名 \<service> / \<baseAddresses> 从 localhost 更改为服务计算机的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="ff784-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="ff784-177">将服务目录中的 Service.cer 文件复制到客户端计算机上的客户端目录中。</span><span class="sxs-lookup"><span data-stu-id="ff784-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="ff784-178">在客户端上， `setup.bat client` 在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="ff784-178">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="ff784-179">如果使用 `setup.bat` 自变量运行 `client`，则会创建一个名为 client.com 的客户端证书，并将此客户端证书导出到名为 Client.cer 的文件中。</span><span class="sxs-lookup"><span data-stu-id="ff784-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="ff784-180">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="ff784-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="ff784-181">通过用服务器的完全限定域名替换 localhost 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ff784-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="ff784-182">将客户端目录中的 Client.cer 文件复制到服务器上的服务目录中。</span><span class="sxs-lookup"><span data-stu-id="ff784-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="ff784-183">在客户端上，在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行 Importservicecert.bat。</span><span class="sxs-lookup"><span data-stu-id="ff784-183">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="ff784-184">这会将 Service.cer 文件中的服务证书导入 CurrentUser – TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="ff784-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="ff784-185">在服务器上，在使用管理员特权打开的 Visual Studio 开发人员命令提示中运行 Importclientcert.bat。</span><span class="sxs-lookup"><span data-stu-id="ff784-185">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="ff784-186">这会将 Client.cer 文件中的客户端证书导入 LocalMachine - TrustedPeople 存储区。</span><span class="sxs-lookup"><span data-stu-id="ff784-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="ff784-187">在服务器计算机上，从命令提示窗口中启动 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="ff784-187">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="ff784-188">在客户端计算机上，从命令提示窗口中启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="ff784-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="ff784-189">如果客户端和服务无法进行通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="ff784-189">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ff784-190">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="ff784-190">To clean up after the sample</span></span>

1. <span data-ttu-id="ff784-191">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="ff784-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="ff784-192">这将从证书存储区中移除服务器和客户端证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-192">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="ff784-193">此脚本不会在跨计算机运行此示例时移除客户端上的服务证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="ff784-194">如果你已运行跨计算机使用证书 Windows Communication Foundation （WCF）示例，请确保清除已安装在 CurrentUser-TrustedPeople 存储中的服务证书。</span><span class="sxs-lookup"><span data-stu-id="ff784-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="ff784-195">为此，请使用以下命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="ff784-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
