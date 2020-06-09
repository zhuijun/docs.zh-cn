---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601891"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ 已删除该消息。  
  
## <a name="description"></a>描述  
 该跟踪指示已丢弃 MSMQ 消息。 当 Windows Communication Foundation （WCF）（与 NetMsmqBinding 或 MsmqIntegrationBinding 一起使用时）无法处理 MSMQ 消息时，可以将其删除。 这些消息称为病毒消息。  
  
 当 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 属性设置为 `Drop` 时，将丢弃病毒消息。 丢弃的消息会从队列中移除而不再可恢复。  
  
 若要详细了解消息何时变为病毒以及如何配置服务以相应地处理这些消息，请参阅[病毒消息处理](../../feature-details/poison-message-handling.md)。  
  
## <a name="see-also"></a>另请参阅

- [跟踪](index.md)
- [使用跟踪来排除应用程序故障](using-tracing-to-troubleshoot-your-application.md)
- [管理和诊断](../index.md)
- [病毒消息处理](../../feature-details/poison-message-handling.md)
