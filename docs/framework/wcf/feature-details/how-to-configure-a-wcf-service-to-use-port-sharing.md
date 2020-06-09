---
title: 如何：配置 Windows Communication Foundation 服务以使用端口共享
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 28f2858d68de99839d7fec66b0fe4528d7e42325
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579522"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="572e3-102">如何：配置 Windows Communication Foundation 服务以使用端口共享</span><span class="sxs-lookup"><span data-stu-id="572e3-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="572e3-103">在 Windows Communication Foundation （WCF）应用程序中使用 net.tcp：//端口共享的最简单方法是使用公开服务 <xref:System.ServiceModel.NetTcpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="572e3-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="572e3-104">此绑定提供了一个 <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> 属性，该属性控制是否为配置了此绑定的服务启用 net.tcp:// 端口共享。</span><span class="sxs-lookup"><span data-stu-id="572e3-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="572e3-105">下面的过程演示如何使用 <xref:System.ServiceModel.NetTcpBinding> 类打开一个位于统一资源标识符 (URI) net.tcp://localhost/MyService 上的终结点（首先使用代码，然后使用配置元素）。</span><span class="sxs-lookup"><span data-stu-id="572e3-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="572e3-106">使用代码在 NetTcpBinding 上启用 net.tcp:// 端口共享</span><span class="sxs-lookup"><span data-stu-id="572e3-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="572e3-107">创建一个服务来实现名为的协定 `IMyService` ，并调用它 `MyService` 。</span><span class="sxs-lookup"><span data-stu-id="572e3-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="572e3-108">创建 <xref:System.ServiceModel.NetTcpBinding> 类的一个实例，并将 <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="572e3-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="572e3-109">创建一个 <xref:System.ServiceModel.ServiceHost>，并在其中为 `MyService` 添加一个服务终结点，该终结点使用启用了端口共享的 <xref:System.ServiceModel.NetTcpBinding> 并在终结点地址 URI“net.tcp://localhost/MyService”上进行侦听。</span><span class="sxs-lookup"><span data-stu-id="572e3-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="572e3-110">此示例使用默认的 TCP 端口 808，因为终结点地址 URI 未指定其他端口号。</span><span class="sxs-lookup"><span data-stu-id="572e3-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="572e3-111">由于在传输绑定上显式启用了端口共享，因此该服务可以与其他进程中的其他服务共享端口 808。</span><span class="sxs-lookup"><span data-stu-id="572e3-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="572e3-112">如果不允许使用端口共享并且其他应用程序已在使用端口 808，则该服务在打开时会引发 <xref:System.ServiceModel.AddressAlreadyInUseException>。</span><span class="sxs-lookup"><span data-stu-id="572e3-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="572e3-113">使用配置在 NetTcpBinding 上启用 net.tcp:// 端口共享</span><span class="sxs-lookup"><span data-stu-id="572e3-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="572e3-114">下面的示例演示如何使用配置元素来启用端口共享以及添加服务终结点。</span><span class="sxs-lookup"><span data-stu-id="572e3-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="572e3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="572e3-115">See also</span></span>

- [<span data-ttu-id="572e3-116">Net.TCP 端口共享</span><span class="sxs-lookup"><span data-stu-id="572e3-116">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="572e3-117">如何：启用 Net.TCP 端口共享服务</span><span class="sxs-lookup"><span data-stu-id="572e3-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](how-to-enable-the-net-tcp-port-sharing-service.md)
