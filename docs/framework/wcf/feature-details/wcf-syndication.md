---
title: WCF 联合
ms.date: 03/30/2017
helpviewer_keywords:
- syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
ms.openlocfilehash: 677e8a4b00b36c2f11b27eb65d57be8abf75d6d2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600641"
---
# <a name="wcf-syndication"></a><span data-ttu-id="102fd-102">WCF 联合</span><span class="sxs-lookup"><span data-stu-id="102fd-102">WCF Syndication</span></span>
<span data-ttu-id="102fd-103">Windows Communication Foundation （WCF）提供的支持可以轻松地使用 Atom、RSS 或其他自定义格式的联合源，这允许你读取和创建它们，还可以在服务终结点上公开它们。</span><span class="sxs-lookup"><span data-stu-id="102fd-103">Windows Communication Foundation (WCF) provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="102fd-104">本节中的主题详细描述用于联合的此种编程模型。</span><span class="sxs-lookup"><span data-stu-id="102fd-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="102fd-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="102fd-105">In This Section</span></span>  
 [<span data-ttu-id="102fd-106">WCF 联合概述</span><span class="sxs-lookup"><span data-stu-id="102fd-106">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)  
 <span data-ttu-id="102fd-107">概述 WCF 提供的联合支持。</span><span class="sxs-lookup"><span data-stu-id="102fd-107">Provides an overview of syndication support provided by WCF.</span></span>  
  
 [<span data-ttu-id="102fd-108">联合体系结构</span><span class="sxs-lookup"><span data-stu-id="102fd-108">Architecture of Syndication</span></span>](architecture-of-syndication.md)  
 <span data-ttu-id="102fd-109">描述对象模型中的类和联合的扩展性。</span><span class="sxs-lookup"><span data-stu-id="102fd-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="102fd-110">WCF 联合对象模型如何映射到 Atom 和 RSS</span><span class="sxs-lookup"><span data-stu-id="102fd-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="102fd-111">描述源在 WCF 联合对象模型中的表示方式以及如何将它们转换为 RSS 和 Atom 源。</span><span class="sxs-lookup"><span data-stu-id="102fd-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="102fd-112">如何：创建基本 RSS 源</span><span class="sxs-lookup"><span data-stu-id="102fd-112">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="102fd-113">演示如何创建可使基本 RSS 源可用的服务。</span><span class="sxs-lookup"><span data-stu-id="102fd-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="102fd-114">如何：创建基本 Atom 源</span><span class="sxs-lookup"><span data-stu-id="102fd-114">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="102fd-115">演示如何创建可使基本 ATOM 源可用的服务。</span><span class="sxs-lookup"><span data-stu-id="102fd-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="102fd-116">如何：作为 Atom 和 RSS 公开源</span><span class="sxs-lookup"><span data-stu-id="102fd-116">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="102fd-117">演示如何创建可将同一个源用于 ATOM 和 RSS 的服务。</span><span class="sxs-lookup"><span data-stu-id="102fd-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="102fd-118">联合扩展性</span><span class="sxs-lookup"><span data-stu-id="102fd-118">Syndication Extensibility</span></span>](syndication-extensibility.md)  
 <span data-ttu-id="102fd-119">描述向联合源添加自定义元素和属性的方法。</span><span class="sxs-lookup"><span data-stu-id="102fd-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="102fd-120">参考</span><span class="sxs-lookup"><span data-stu-id="102fd-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="102fd-121">相关章节</span><span class="sxs-lookup"><span data-stu-id="102fd-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="102fd-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="102fd-122">See also</span></span>

- [<span data-ttu-id="102fd-123">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="102fd-123">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="102fd-124">部分信任</span><span class="sxs-lookup"><span data-stu-id="102fd-124">Partial Trust</span></span>](partial-trust.md)
