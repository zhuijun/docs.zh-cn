---
title: 元数据格式
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a304b6026ae9b8bc9506bfa82ab6eaa3c80b2a42
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679372"
---
# <a name="metadata-formats"></a><span data-ttu-id="c7de6-102">元数据格式</span><span class="sxs-lookup"><span data-stu-id="c7de6-102">Metadata formats</span></span>

<span data-ttu-id="c7de6-103">Windows Communication Foundation (WCF) 支持下表中的元数据格式。</span><span class="sxs-lookup"><span data-stu-id="c7de6-103">Windows Communication Foundation (WCF) supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="c7de6-104">元数据的规范和用法</span><span class="sxs-lookup"><span data-stu-id="c7de6-104">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="c7de6-105">协议</span><span class="sxs-lookup"><span data-stu-id="c7de6-105">Protocol</span></span>|<span data-ttu-id="c7de6-106">规范和用法</span><span class="sxs-lookup"><span data-stu-id="c7de6-106">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="c7de6-107">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="c7de6-107">WSDL 1.1</span></span>|[<span data-ttu-id="c7de6-108">Web 服务描述语言 (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="c7de6-108">Web Services Description Language (WSDL) 1.1</span></span>](https://www.w3.org/TR/wsdl/)<br /><br /> <span data-ttu-id="c7de6-109">WCF 使用 Web 服务描述语言 (WSDL) 来描述服务。</span><span class="sxs-lookup"><span data-stu-id="c7de6-109">WCF uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="c7de6-110">XML 架构</span><span class="sxs-lookup"><span data-stu-id="c7de6-110">XML Schema</span></span>|<span data-ttu-id="c7de6-111">[XML 架构第2部分：数据类型第二版](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) 和 [XML 架构第1部分：结构第二版](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)</span><span class="sxs-lookup"><span data-stu-id="c7de6-111">[XML Schema Part 2: Datatypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) and [XML Schema Part 1: Structures Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)</span></span><br /><br /> <span data-ttu-id="c7de6-112">WCF 使用 XML 架构描述消息中使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c7de6-112">WCF uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="c7de6-113">WS Policy</span><span class="sxs-lookup"><span data-stu-id="c7de6-113">WS Policy</span></span>|[<span data-ttu-id="c7de6-114">Web 服务策略 1.2 - 框架 (WS-Policy)</span><span class="sxs-lookup"><span data-stu-id="c7de6-114">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [<span data-ttu-id="c7de6-115">Web 服务策略 1.5 - 框架</span><span class="sxs-lookup"><span data-stu-id="c7de6-115">Web Services Policy 1.5 - Framework</span></span>](https://www.w3.org/TR/ws-policy/)<br /><br /> <span data-ttu-id="c7de6-116">WCF 使用 WS 策略1.2 或1.5 规范和域特定断言来描述服务要求和功能。</span><span class="sxs-lookup"><span data-stu-id="c7de6-116">WCF uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="c7de6-117">WS Policy 附件</span><span class="sxs-lookup"><span data-stu-id="c7de6-117">WS Policy Attachments</span></span>|[<span data-ttu-id="c7de6-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)（Web 服务策略 1.2 - 附件 (WS-PolicyAttachment)）</span><span class="sxs-lookup"><span data-stu-id="c7de6-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> <span data-ttu-id="c7de6-119">WCF 实现 WS 策略附件，以在 WSDL 中的不同范围内附加策略表达式。</span><span class="sxs-lookup"><span data-stu-id="c7de6-119">WCF implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="c7de6-120">WS 元数据交换</span><span class="sxs-lookup"><span data-stu-id="c7de6-120">WS Metadata Exchange</span></span>|[<span data-ttu-id="c7de6-121">Web 服务元数据交换 (Ws-metadataexchange) </span><span class="sxs-lookup"><span data-stu-id="c7de6-121">Web Services Metadata Exchange (WS-MetadataExchange)</span></span>](https://www.w3.org/TR/ws-metadata-exchange/)<br /><br /> <span data-ttu-id="c7de6-122">WCF 实现 Ws-metadataexchange 来检索 XML 架构、WSDL 和 WS 策略。</span><span class="sxs-lookup"><span data-stu-id="c7de6-122">WCF implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="c7de6-123">WSDL 的 WS 寻址绑定</span><span class="sxs-lookup"><span data-stu-id="c7de6-123">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="c7de6-124">Web 服务寻址 1.0 - WSDL 绑定</span><span class="sxs-lookup"><span data-stu-id="c7de6-124">Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> <span data-ttu-id="c7de6-125">WCF 为 WSDL 实现 WS-ADDRESSING 绑定以在 WSDL 中附加寻址信息。</span><span class="sxs-lookup"><span data-stu-id="c7de6-125">WCF implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7de6-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="c7de6-126">See also</span></span>

- [<span data-ttu-id="c7de6-127">系统提供的互操作性绑定支持的 Web 服务协议</span><span class="sxs-lookup"><span data-stu-id="c7de6-127">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [<span data-ttu-id="c7de6-128">WSDL 和策略</span><span class="sxs-lookup"><span data-stu-id="c7de6-128">WSDL and Policy</span></span>](wsdl-and-policy.md)
