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
# <a name="security-validation-and-authentication-failures-per-second"></a>Security Validation and Authentication Failures Per Second（每秒安全验证和身份验证失败次数）
计数器名称：Security Validation and Authentication Failures Per Second（每秒安全验证和身份验证失败次数）。  
  
## <a name="description"></a>说明  
 每当消息由于“Security Calls Not Authorized”（未授权的安全调用次数）计数器中未包括的安全问题而遭到拒绝时，此计数器即会递增。 此类问题包括：  
  
- 无法从消息中读取客户端令牌。  
  
- 客户端令牌身份验证失败（如密码错误）。  
  
- 签名验证失败（如消息已被篡改）。  
  
- 消息与上一条消息重复，这种情况可能在重放攻击过程中发生。  
  
- 已发生解密失败。  
  
- 消息中缺少一些必需元素（如缺少时间戳或加密的数据块）。  
  
- TLSNEGO/SPNEGO 握手过程中已发生错误。  
  
 此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算：  
  
 (N1-N0)/((D1-D0)/F)
