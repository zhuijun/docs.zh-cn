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
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="60614-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="60614-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="60614-103">未能通过 HTTP 通道接收消息。</span><span class="sxs-lookup"><span data-stu-id="60614-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="60614-104">描述</span><span class="sxs-lookup"><span data-stu-id="60614-104">Description</span></span>  
 <span data-ttu-id="60614-105">此跟踪可作为警告或错误发出。</span><span class="sxs-lookup"><span data-stu-id="60614-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="60614-106">在这两种情况下，跟踪都是在未找到传入 HTTP 请求的兼容侦听器并丢弃了该 HTTP 请求时发出的。</span><span class="sxs-lookup"><span data-stu-id="60614-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="60614-107">之所以会发生此情况，原因在于任何 HTTP 侦听器都未能识别请求的 HTTP 谓词，或是没有任何侦听器在请求的目标地址上进行侦听。</span><span class="sxs-lookup"><span data-stu-id="60614-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="60614-108">在自承载情况下，跟踪会作为警告发出，如果服务是在 IIS 中承载的，则跟踪会作为错误发出。</span><span class="sxs-lookup"><span data-stu-id="60614-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60614-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60614-109">See also</span></span>

- [<span data-ttu-id="60614-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="60614-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="60614-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="60614-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="60614-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="60614-112">Administration and Diagnostics</span></span>](../index.md)
