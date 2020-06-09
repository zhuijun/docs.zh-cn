---
title: 通道扩展性
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 9dbae26a548bdc8a8cfb05a3dd90db91475b55ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600628"
---
# <a name="channels-extensibility"></a>通道扩展性
本节包含演示自定义通道的示例。  
  
## <a name="in-this-section"></a>本节内容  
 [本地通道](local-channel.md)  
 演示本地通道，它是用于在同一个应用程序域内进行通信的 WCF 传输通道。  
  
 [可靠安全配置文件](reliable-secure-profile.md)  
 演示如何撰写 WCF 和可靠安全配置文件（RSP）。  
  
 [自定义通道调度程序](custom-channel-dispatcher.md)  
 演示如何通过直接实现 <xref:System.ServiceModel.ServiceHostBase> 以自定义方式生成通道堆栈，以及如何在 Web 主机环境中创建自定义通道调度程序。  
  
 [通道分块](chunking-channel.md)  
 演示如何限制用于缓冲使用 WCF 发送的大型消息的内存量。
  
 [HttpCookieSession](httpcookiesession.md)  
 演示如何生成自定义协议通道，以便使用 HTTP Cookie 进行会话管理。  
  
 [自定义消息拦截器](custom-message-interceptor.md)  
 演示如何实现可创建通道工厂和通道侦听器的自定义绑定元素，以便在运行时堆栈的特定点截获所有传入和传出消息。
