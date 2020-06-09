---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: e11b376924ee74e5d0d67da0cac59af41655dc44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594070"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
未能通过 HTTP 通道接收消息。  
  
## <a name="description"></a>描述  
 此跟踪可作为警告或错误发出。 在这两种情况下，跟踪都是在未找到传入 HTTP 请求的兼容侦听器并丢弃了该 HTTP 请求时发出的。 之所以会发生此情况，原因在于任何 HTTP 侦听器都未能识别请求的 HTTP 谓词，或是没有任何侦听器在请求的目标地址上进行侦听。 在自承载情况下，跟踪会作为警告发出，如果服务是在 IIS 中承载的，则跟踪会作为错误发出。  
  
## <a name="see-also"></a>另请参阅

- [跟踪](index.md)
- [使用跟踪来排除应用程序故障](using-tracing-to-troubleshoot-your-application.md)
- [管理和诊断](../index.md)
