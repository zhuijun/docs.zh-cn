---
title: Security Validation and Authentication Failures Per Second（每秒安全验证和身份验证失败次数）
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 7d680e9a5b03943fdec212c509b6d80a2d60246c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559130"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="9e663-102">Security Validation and Authentication Failures Per Second（每秒安全验证和身份验证失败次数）</span><span class="sxs-lookup"><span data-stu-id="9e663-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="9e663-103">计数器名称：Security Validation and Authentication Failures Per Second（每秒安全验证和身份验证失败次数）。</span><span class="sxs-lookup"><span data-stu-id="9e663-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e663-104">说明</span><span class="sxs-lookup"><span data-stu-id="9e663-104">Description</span></span>  
 <span data-ttu-id="9e663-105">每当消息由于“Security Calls Not Authorized”（未授权的安全调用次数）计数器中未包括的安全问题而遭到拒绝时，此计数器即会递增。</span><span class="sxs-lookup"><span data-stu-id="9e663-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="9e663-106">此类问题包括：</span><span class="sxs-lookup"><span data-stu-id="9e663-106">Such problems include:</span></span>  
  
- <span data-ttu-id="9e663-107">无法从消息中读取客户端令牌。</span><span class="sxs-lookup"><span data-stu-id="9e663-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="9e663-108">客户端令牌身份验证失败（如密码错误）。</span><span class="sxs-lookup"><span data-stu-id="9e663-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="9e663-109">签名验证失败（如消息已被篡改）。</span><span class="sxs-lookup"><span data-stu-id="9e663-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="9e663-110">消息与上一条消息重复，这种情况可能在重放攻击过程中发生。</span><span class="sxs-lookup"><span data-stu-id="9e663-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="9e663-111">已发生解密失败。</span><span class="sxs-lookup"><span data-stu-id="9e663-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="9e663-112">消息中缺少一些必需元素（如缺少时间戳或加密的数据块）。</span><span class="sxs-lookup"><span data-stu-id="9e663-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="9e663-113">TLSNEGO/SPNEGO 握手过程中已发生错误。</span><span class="sxs-lookup"><span data-stu-id="9e663-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="9e663-114">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算：</span><span class="sxs-lookup"><span data-stu-id="9e663-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="9e663-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="9e663-115">(N1-N0)/((D1-D0)/F)</span></span>
