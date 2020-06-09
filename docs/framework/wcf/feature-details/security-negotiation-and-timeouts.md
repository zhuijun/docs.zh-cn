---
title: 安全协商和超时
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600992"
---
# <a name="security-negotiation-and-timeouts"></a>安全协商和超时
当客户端和服务进行身份验证时，Windows Communication Foundation （WCF）支持一种模式，在该模式下，将在身份验证过程中协商服务凭据。 在这种情况下，客户端和服务之间将进行潜在多路交换，以便将服务凭据传播到客户端。 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 属性控制多路交换需要多长时间才能完成。 但此超时仅在交换实际经过的时间超过单个请求响应的时间时才适用。 如果协商在一次往返中完成，则该超时不适用。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [如何：设置最大时钟偏差](how-to-set-a-max-clock-skew.md)
