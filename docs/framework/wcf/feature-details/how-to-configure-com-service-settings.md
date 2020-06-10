---
title: 如何：配置 COM+ 服务设置
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 3fb4b31038845d223248e72d32b3e7413f2aef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597171"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="7d6da-102">如何：配置 COM+ 服务设置</span><span class="sxs-lookup"><span data-stu-id="7d6da-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="7d6da-103">使用 COM+ 服务配置工具添加或移除应用程序接口时，应用程序配置文件中的 Web 服务配置将更新。</span><span class="sxs-lookup"><span data-stu-id="7d6da-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="7d6da-104">在 COM + 托管模式下，将应用程序 .config 文件放在应用程序根目录中（ \\ 默认情况下%Programfiles%\complus applications\ 应用程序 {appid}）。</span><span class="sxs-lookup"><span data-stu-id="7d6da-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="7d6da-105">无论在哪种 Web 宿主模式中，Web.config 文件均放置在指定的 vroot 目录中。</span><span class="sxs-lookup"><span data-stu-id="7d6da-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d6da-106">应使用消息签名来防止客户端和服务器之间的消息被篡改。</span><span class="sxs-lookup"><span data-stu-id="7d6da-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="7d6da-107">另外，还应该使用消息或传输层加密来防止客户端和服务器之间的消息发生信息泄漏。</span><span class="sxs-lookup"><span data-stu-id="7d6da-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="7d6da-108">与 Windows Communication Foundation （WCF）服务一样，您应该使用限制来限制并发调用、连接、实例和挂起的操作的数量。</span><span class="sxs-lookup"><span data-stu-id="7d6da-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="7d6da-109">这有助于防止过度消耗资源。</span><span class="sxs-lookup"><span data-stu-id="7d6da-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="7d6da-110">您可以通过设置服务配置文件来指定遏制行为。</span><span class="sxs-lookup"><span data-stu-id="7d6da-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d6da-111">示例</span><span class="sxs-lookup"><span data-stu-id="7d6da-111">Example</span></span>  
 <span data-ttu-id="7d6da-112">假设有一个实现以下接口的组件：</span><span class="sxs-lookup"><span data-stu-id="7d6da-112">Consider a component that implements the following interface:</span></span>  
  
```csharp
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="7d6da-113">如果该组件作为 Web 服务公开，则公开的且客户端应遵循的相应服务协定如下：</span><span class="sxs-lookup"><span data-stu-id="7d6da-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
```csharp
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="7d6da-114">IID 是该协定的初始命名空间的一部分。</span><span class="sxs-lookup"><span data-stu-id="7d6da-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="7d6da-115">使用此服务的客户端应用程序需要遵循此协定，并使用一个与应用程序配置中指定的绑定相兼容的绑定。</span><span class="sxs-lookup"><span data-stu-id="7d6da-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="7d6da-116">下面的代码示例演示了默认的配置文件。</span><span class="sxs-lookup"><span data-stu-id="7d6da-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="7d6da-117">作为 Windows Communication Foundation （WCF） Web 服务，这符合标准服务模型配置架构，并可按与其他 WCF 服务配置文件相同的方式进行编辑。</span><span class="sxs-lookup"><span data-stu-id="7d6da-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="7d6da-118">典型的修改包括：</span><span class="sxs-lookup"><span data-stu-id="7d6da-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="7d6da-119">将终结点地址从默认的 ApplicationName/ComponentName/InterfaceName 形式更改为更可用的形式。</span><span class="sxs-lookup"><span data-stu-id="7d6da-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="7d6da-120">将服务的命名空间从默认 `http://tempuri.org/InterfaceID` 窗体修改为更相关的窗体。</span><span class="sxs-lookup"><span data-stu-id="7d6da-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="7d6da-121">将终结点更改为使用其他传输绑定。</span><span class="sxs-lookup"><span data-stu-id="7d6da-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="7d6da-122">在 COM+ 宿主模式中，默认使用命名管道传输，但也可以改用无线传输（如 TCP）。</span><span class="sxs-lookup"><span data-stu-id="7d6da-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d6da-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d6da-123">See also</span></span>

- [<span data-ttu-id="7d6da-124">与 COM + 应用程序集成</span><span class="sxs-lookup"><span data-stu-id="7d6da-124">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
