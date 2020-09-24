---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 6ba97adfa696e00b4d6b75faf104c31436e25447
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151125"
---
# \<bindingElementExtensions>

<span data-ttu-id="34075-101">本节为使用计算机或应用程序配置文件中的自定义绑定元素提供支持。</span><span class="sxs-lookup"><span data-stu-id="34075-101">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="34075-102">通过使用 `add` 关键字，然后将元素的 `type` 属性设置为绑定元素扩展，并将 `name` 属性设置为自定义绑定元素，你可以向此集合添加自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="34075-102">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="34075-103">用户可以使用绑定扩展来创建用户定义的绑定元素，并将其作为自定义绑定的一部分来使用。</span><span class="sxs-lookup"><span data-stu-id="34075-103">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="34075-104">从编程角度来看，绑定扩展是一个实现抽象类 <xref:System.ServiceModel.Channels.BindingElement> 的类型。</span><span class="sxs-lookup"><span data-stu-id="34075-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="34075-105">在配置文件中，`bindingElementExtensions` 节用于定义扩展元素。</span><span class="sxs-lookup"><span data-stu-id="34075-105">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="34075-106">下面的示例使用 `add` 元素以及 `name` 属性将绑定扩展添加到配置文件的 `bindingElementExtensions` 节。</span><span class="sxs-lookup"><span data-stu-id="34075-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="34075-107">若要向元素添加配置功能，用户需要编写和注册 `bindingElementExtensionSection` 元素。</span><span class="sxs-lookup"><span data-stu-id="34075-107">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="34075-108">有关这方面的更多信息，请参见 <xref:System.Configuration> 文档。</span><span class="sxs-lookup"><span data-stu-id="34075-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="34075-109">在定义元素及其配置类型之后，可以将扩展用作自定义绑定的一部分，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="34075-109">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="34075-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="34075-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="34075-111">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="34075-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
