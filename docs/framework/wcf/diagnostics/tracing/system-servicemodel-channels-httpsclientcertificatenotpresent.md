---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 3e3bedca7a46f147ee3d9e143cea7e57095c99d1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602033"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="72230-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="72230-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="72230-103">需要客户端证书。</span><span class="sxs-lookup"><span data-stu-id="72230-103">Client certificate is required.</span></span> <span data-ttu-id="72230-104">在请求中未找到任何证书。</span><span class="sxs-lookup"><span data-stu-id="72230-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="72230-105">描述</span><span class="sxs-lookup"><span data-stu-id="72230-105">Description</span></span>  
 <span data-ttu-id="72230-106">此跟踪指示 HTTPS 侦听器收到与客户端证书无关的 HTTPS 请求。</span><span class="sxs-lookup"><span data-stu-id="72230-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="72230-107">因为侦听器被配置为对所有 HTTPS 请求都要求提供客户端证书，所以侦听器未能验证该客户端的真实性。</span><span class="sxs-lookup"><span data-stu-id="72230-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72230-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72230-108">See also</span></span>

- [<span data-ttu-id="72230-109">跟踪</span><span class="sxs-lookup"><span data-stu-id="72230-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="72230-110">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="72230-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="72230-111">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="72230-111">Administration and Diagnostics</span></span>](../index.md)
