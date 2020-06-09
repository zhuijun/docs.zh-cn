---
title: 如何：创建基本 Atom 源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 0317e7b42f589b31f5c77b89d26cb46815f13054
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599043"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="f1d67-102">如何：创建基本 Atom 源</span><span class="sxs-lookup"><span data-stu-id="f1d67-102">How to: Create a Basic Atom Feed</span></span>
<span data-ttu-id="f1d67-103">Windows Communication Foundation （WCF）允许您创建公开联合源的服务。</span><span class="sxs-lookup"><span data-stu-id="f1d67-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="f1d67-104">本主题讨论如何创建公开 Atom 联合源的联合服务。</span><span class="sxs-lookup"><span data-stu-id="f1d67-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="f1d67-105">创建基本联合服务</span><span class="sxs-lookup"><span data-stu-id="f1d67-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="f1d67-106">使用通过 <xref:System.ServiceModel.Web.WebGetAttribute> 属性标记的接口定义服务协定。</span><span class="sxs-lookup"><span data-stu-id="f1d67-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="f1d67-107">作为联合源公开的每个操作应返回 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> 对象。</span><span class="sxs-lookup"><span data-stu-id="f1d67-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="f1d67-108">应用 <xref:System.ServiceModel.Web.WebGetAttribute> 的所有服务操作将映射到 HTTP GET 请求。</span><span class="sxs-lookup"><span data-stu-id="f1d67-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="f1d67-109">若要将操作映射到不同的 HTTP 方法，请改用 <xref:System.ServiceModel.Web.WebInvokeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="f1d67-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="f1d67-110">有关详细信息，请参阅[如何：创建基本 WCF WEB HTTP 服务](how-to-create-a-basic-wcf-web-http-service.md)。</span><span class="sxs-lookup"><span data-stu-id="f1d67-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="f1d67-111">实现服务协定。</span><span class="sxs-lookup"><span data-stu-id="f1d67-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="f1d67-112">创建 <xref:System.ServiceModel.Syndication.SyndicationFeed> 对象，并添加作者、类别和说明。</span><span class="sxs-lookup"><span data-stu-id="f1d67-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="f1d67-113">创建若干 <xref:System.ServiceModel.Syndication.SyndicationItem> 对象。</span><span class="sxs-lookup"><span data-stu-id="f1d67-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="f1d67-114">向源中添加 <xref:System.ServiceModel.Syndication.SyndicationItem> 对象。</span><span class="sxs-lookup"><span data-stu-id="f1d67-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="f1d67-115">返回源。</span><span class="sxs-lookup"><span data-stu-id="f1d67-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="f1d67-116">承载服务</span><span class="sxs-lookup"><span data-stu-id="f1d67-116">To host the service</span></span>  
  
1. <span data-ttu-id="f1d67-117">创建 <xref:System.ServiceModel.Web.WebServiceHost> 对象。</span><span class="sxs-lookup"><span data-stu-id="f1d67-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="f1d67-118">打开服务主机，从服务加载源，显示源，然后等待用户按 Enter。</span><span class="sxs-lookup"><span data-stu-id="f1d67-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="f1d67-119">使用 HTTP GET 调用 GetBlog()</span><span class="sxs-lookup"><span data-stu-id="f1d67-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="f1d67-120">打开 Internet Explorer，键入以下 URL，然后按 ENTER：`http://localhost:8000/BlogService/GetBlog`</span><span class="sxs-lookup"><span data-stu-id="f1d67-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`</span></span>  
  
     <span data-ttu-id="f1d67-121">URL 包含服务的基址（ `http://localhost:8000/BlogService` ）、终结点的相对地址以及要调用的服务操作。</span><span class="sxs-lookup"><span data-stu-id="f1d67-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="f1d67-122">从代码中调用 GetBlog()</span><span class="sxs-lookup"><span data-stu-id="f1d67-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="f1d67-123">使用基址和调用的方法创建 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="f1d67-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="f1d67-124">调用静态 <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> 方法，同时传入刚刚创建的 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="f1d67-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="f1d67-125">这将调用服务操作，并用从服务操作返回的格式化程序填充新的 <xref:System.ServiceModel.Syndication.SyndicationFeed>。</span><span class="sxs-lookup"><span data-stu-id="f1d67-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="f1d67-126">访问源对象。</span><span class="sxs-lookup"><span data-stu-id="f1d67-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="f1d67-127">示例</span><span class="sxs-lookup"><span data-stu-id="f1d67-127">Example</span></span>  
 <span data-ttu-id="f1d67-128">下面列出了此示例的完整代码。</span><span class="sxs-lookup"><span data-stu-id="f1d67-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f1d67-129">编译代码</span><span class="sxs-lookup"><span data-stu-id="f1d67-129">Compiling the Code</span></span>  
 <span data-ttu-id="f1d67-130">编译前面的代码时，请引用 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。</span><span class="sxs-lookup"><span data-stu-id="f1d67-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d67-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1d67-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
