---
title: 如何：使用 SSL 配置承载 IIS 的 WCF 服务
description: 了解如何设置 IIS 承载的 WCF 服务以使用 HTTP 传输安全，这需要使用 IIS 注册的证书。
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 8dc4692863d93e407a122c0ba93ae38323b8b213
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245253"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="e9ff6-103">如何：使用 SSL 配置承载 IIS 的 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="e9ff6-103">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="e9ff6-104">本主题介绍如何设置 IIS 承载的 WCF 服务以使用 HTTP 传输安全性。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-104">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="e9ff6-105">HTTP 传输安全性要求 SSL 证书以便向 IIS 注册。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-105">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="e9ff6-106">如果你没有 SSL 证书，则可以使用 IIS 生成测试证书。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-106">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="e9ff6-107">接下来，您必须将一个 SSL 绑定添加到网站，并且配置该网站的身份验证属性。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-107">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="e9ff6-108">最后，您需要配置 WCF 服务以使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-108">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="e9ff6-109">创建自签名证书</span><span class="sxs-lookup"><span data-stu-id="e9ff6-109">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="e9ff6-110">打开 Internet 信息服务管理器 (inetmgr.exe)，在左侧树视图中选择您的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-110">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="e9ff6-111">在屏幕的右侧选择“服务器证书”</span><span class="sxs-lookup"><span data-stu-id="e9ff6-111">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="e9ff6-112">![IIS 管理器主屏幕](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-112">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="e9ff6-113">在 "服务器证书" 窗口中，单击 "**创建自签名证书 ...** "。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-113">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="e9ff6-114">链接。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-114">Link.</span></span>  
  
     <span data-ttu-id="e9ff6-115">![使用 IIS 创建自&#45;签名证书](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-115">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="e9ff6-116">输入自签名证书的友好名称，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-116">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="e9ff6-117">!["创建自&#45;签名证书" 对话框](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-117">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="e9ff6-118">新创建的自签名证书详细信息现在显示在 "**服务器证书**" 窗口中。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-118">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="e9ff6-119">![服务器证书窗口](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-119">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="e9ff6-120">生成的证书将安装在“受信任的根证书颁发机构”存储区中。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-120">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="e9ff6-121">添加 SSL 绑定</span><span class="sxs-lookup"><span data-stu-id="e9ff6-121">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="e9ff6-122">在 Internet Information Services 管理器中，展开 "**站点**" 文件夹，然后在屏幕左侧的树视图中展开 "**默认**网站" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-122">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="e9ff6-123">单击 "**绑定 ...** "。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-123">Click the **Bindings….**</span></span> <span data-ttu-id="e9ff6-124">在窗口右上角的 "**操作**" 部分中的链接。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-124">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="e9ff6-125">![添加 SSL 绑定](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-125">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="e9ff6-126">在 "站点绑定" 窗口中，单击 "**添加**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-126">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="e9ff6-127">![“站点绑定”对话框](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-127">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="e9ff6-128">在 "**添加站点绑定**" 对话框中，选择 "https" 作为 "类型"，并选择你刚创建的自签名证书的友好名称。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-128">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="e9ff6-129">![站点绑定示例](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-129">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="e9ff6-130">配置 SSL 的虚拟目录</span><span class="sxs-lookup"><span data-stu-id="e9ff6-130">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="e9ff6-131">仍在 Internet 信息服务管理器中，选择包含您 WCF 安全服务的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-131">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="e9ff6-132">在窗口的中心窗格中，选择 "IIS" 部分中的 " **SSL 设置**"。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-132">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="e9ff6-133">![虚拟目录的 SSL 设置](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-133">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="e9ff6-134">在 "SSL 设置" 窗格中，选中 "**需要 SSL** " 复选框，并在屏幕右侧的 "**操作**" 部分中单击 "**应用**" 链接。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-134">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="e9ff6-135">![虚拟目录 SSL 设置](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="e9ff6-135">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="e9ff6-136">为 HTTP 传输安全配置 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="e9ff6-136">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="e9ff6-137">在 WCF 服务的 web.config 中，配置 HTTP 绑定以便使用传输安全，如下面的 XML 中所示。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-137">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2. <span data-ttu-id="e9ff6-138">指定您的服务和服务终结点，如下面的 XML 中所示。</span><span class="sxs-lookup"><span data-stu-id="e9ff6-138">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="e9ff6-139">示例</span><span class="sxs-lookup"><span data-stu-id="e9ff6-139">Example</span></span>  
 <span data-ttu-id="e9ff6-140">以下是使用 HTTP 传输安全的 WCF 服务的 web.config 文件的完整示例</span><span class="sxs-lookup"><span data-stu-id="e9ff6-140">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9ff6-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="e9ff6-141">See also</span></span>

- [<span data-ttu-id="e9ff6-142">在 Internet 信息服务中承载</span><span class="sxs-lookup"><span data-stu-id="e9ff6-142">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="e9ff6-143">Internet 信息服务承载说明</span><span class="sxs-lookup"><span data-stu-id="e9ff6-143">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="e9ff6-144">Internet 信息服务承载最佳实践</span><span class="sxs-lookup"><span data-stu-id="e9ff6-144">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="e9ff6-145">使用内联代码的 IIS 承载</span><span class="sxs-lookup"><span data-stu-id="e9ff6-145">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
