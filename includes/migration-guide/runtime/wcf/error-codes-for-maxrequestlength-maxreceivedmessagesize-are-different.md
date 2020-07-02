---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619862"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="cd4d1-101">maxRequestLength 或 maxReceivedMessageSize 的错误代码是不同的</span><span class="sxs-lookup"><span data-stu-id="cd4d1-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

#### <a name="details"></a><span data-ttu-id="cd4d1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cd4d1-102">Details</span></span>

<span data-ttu-id="cd4d1-103">Internet Information Services (IIS) 或 ASP.NET 开发服务器承载的 WCF Web 服务中的消息如果超过 maxRequestLength（在 ASP.NET 中）或 maxReceivedMessageSize（在 WCF 中），则有不同的错误代码。HTTP 状态代码已从 400（错误请求）更改为 413（请求实体太大），并且超过 maxRequestLength 或 maxReceivedMessageSize 设置的消息引发了 <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="cd4d1-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="cd4d1-104">这包括转换模式为“流式处理”的情况。</span><span class="sxs-lookup"><span data-stu-id="cd4d1-104">This includes cases in which the transfer mode is Streamed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cd4d1-105">建议</span><span class="sxs-lookup"><span data-stu-id="cd4d1-105">Suggestion</span></span>

<span data-ttu-id="cd4d1-106">在消息长度超过 ASP.NET 或 WCF 所允许的限制的情况下，此更改有利于调试。必须基于 HTTP 400 状态代码修改执行处理的任何代码。</span><span class="sxs-lookup"><span data-stu-id="cd4d1-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>

| <span data-ttu-id="cd4d1-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="cd4d1-107">Name</span></span>    | <span data-ttu-id="cd4d1-108">“值”</span><span class="sxs-lookup"><span data-stu-id="cd4d1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cd4d1-109">范围</span><span class="sxs-lookup"><span data-stu-id="cd4d1-109">Scope</span></span>   |<span data-ttu-id="cd4d1-110">边缘</span><span class="sxs-lookup"><span data-stu-id="cd4d1-110">Edge</span></span>|
|<span data-ttu-id="cd4d1-111">Version</span><span class="sxs-lookup"><span data-stu-id="cd4d1-111">Version</span></span>|<span data-ttu-id="cd4d1-112">4.5</span><span class="sxs-lookup"><span data-stu-id="cd4d1-112">4.5</span></span>|
|<span data-ttu-id="cd4d1-113">类型</span><span class="sxs-lookup"><span data-stu-id="cd4d1-113">Type</span></span>|<span data-ttu-id="cd4d1-114">运行时</span><span class="sxs-lookup"><span data-stu-id="cd4d1-114">Runtime</span></span>|
