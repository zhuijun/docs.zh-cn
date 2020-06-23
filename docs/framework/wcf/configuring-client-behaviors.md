---
title: 配置客户端行为
description: 了解 WCF 在应用程序配置文件中或从调用应用程序以编程方式配置行为的两种方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 4b83862221cf249455478c3ade159a3101062f3e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245435"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="54f48-103">配置客户端行为</span><span class="sxs-lookup"><span data-stu-id="54f48-103">Configuring Client Behaviors</span></span>
<span data-ttu-id="54f48-104">Windows Communication Foundation （WCF）通过以下两种方式配置行为：通过引用在 `<behavior>` 客户端应用程序配置文件的部分中定义的行为配置，或在调用应用程序中以编程方式定义。</span><span class="sxs-lookup"><span data-stu-id="54f48-104">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="54f48-105">本主题将介绍这两种方式。</span><span class="sxs-lookup"><span data-stu-id="54f48-105">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="54f48-106">在使用配置文件时，行为配置为配置设置的命名集合。</span><span class="sxs-lookup"><span data-stu-id="54f48-106">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="54f48-107">每个行为配置的名称都必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="54f48-107">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="54f48-108">在终结点配置的 `behaviorConfiguration` 属性中，此字符串用来将终结点链接到该行为。</span><span class="sxs-lookup"><span data-stu-id="54f48-108">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54f48-109">示例</span><span class="sxs-lookup"><span data-stu-id="54f48-109">Example</span></span>  
 <span data-ttu-id="54f48-110">下面的配置代码定义了一个称为 `myBehavior` 的行为。</span><span class="sxs-lookup"><span data-stu-id="54f48-110">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="54f48-111">客户端终结点在 `behaviorConfiguration` 属性中引用该行为。</span><span class="sxs-lookup"><span data-stu-id="54f48-111">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="54f48-112">以编程方式使用行为</span><span class="sxs-lookup"><span data-stu-id="54f48-112">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="54f48-113">还可以通过在 `Behaviors` 打开客户端之前，通过在 Windows Communication Foundation （WCF）客户端对象或客户端通道工厂对象上查找适当的属性，以编程方式配置或插入行为。</span><span class="sxs-lookup"><span data-stu-id="54f48-113">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54f48-114">示例</span><span class="sxs-lookup"><span data-stu-id="54f48-114">Example</span></span>  
 <span data-ttu-id="54f48-115">下面的代码示例演示如何在创建通道对象之前访问从 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 属性返回的 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 属性，从而以编程方式插入行为。</span><span class="sxs-lookup"><span data-stu-id="54f48-115">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="54f48-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="54f48-116">See also</span></span>

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
