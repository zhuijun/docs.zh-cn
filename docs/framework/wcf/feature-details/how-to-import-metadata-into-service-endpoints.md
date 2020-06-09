---
title: 如何：将元数据导入服务终结点
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597054"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="eead5-102">如何：将元数据导入服务终结点</span><span class="sxs-lookup"><span data-stu-id="eead5-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="eead5-103">本主题说明如何将元数据导入服务终结点的集合，并使用在[入门](../samples/getting-started-sample.md)中定义的服务。</span><span class="sxs-lookup"><span data-stu-id="eead5-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../samples/getting-started-sample.md).</span></span> <span data-ttu-id="eead5-104">本主题演示如何创建从服务中导入元数据的客户端应用程序，以及之后如何对该服务调用 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="eead5-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="eead5-105">将元数据导入服务终结点</span><span class="sxs-lookup"><span data-stu-id="eead5-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="eead5-106">声明 <xref:System.ServiceModel.EndpointAddress> 对象，并使用服务的元数据交换 (MEX) 地址的统一资源标识符 (URI) 对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="eead5-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="eead5-107">创建 <xref:System.ServiceModel.Description.MetadataExchangeClient>、传入 MEX 地址并调用 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>。</span><span class="sxs-lookup"><span data-stu-id="eead5-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="eead5-108">此操作将从服务中检索元数据。</span><span class="sxs-lookup"><span data-stu-id="eead5-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="eead5-109">创建 <xref:System.ServiceModel.Description.WsdlImporter>、传入先前检索的元数据并调用 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>。</span><span class="sxs-lookup"><span data-stu-id="eead5-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="eead5-110">此操作将生成 <xref:System.ServiceModel.Description.ContractDescription> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="eead5-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="eead5-111">您还可以根据需要调用 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> 或 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>。</span><span class="sxs-lookup"><span data-stu-id="eead5-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="eead5-112">导入元数据后，将无法创建客户端通道或导出元数据。</span><span class="sxs-lookup"><span data-stu-id="eead5-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="eead5-113">这是因为此时没有可用的类型信息。</span><span class="sxs-lookup"><span data-stu-id="eead5-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="eead5-114">在实际与服务进行交互或导出元数据时需要类型信息。</span><span class="sxs-lookup"><span data-stu-id="eead5-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="eead5-115">若要生成类型信息，需要生成代码，如步骤 4 和 5 所示。</span><span class="sxs-lookup"><span data-stu-id="eead5-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="eead5-116">或者可以使用 <xref:System.ServiceModel.Description.MetadataResolver> 帮助器类。</span><span class="sxs-lookup"><span data-stu-id="eead5-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="eead5-117">有关详细信息，请参阅[如何：使用 MetadataResolver 动态获取绑定元数据](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)。</span><span class="sxs-lookup"><span data-stu-id="eead5-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="eead5-118">为每个协定生成类型信息。</span><span class="sxs-lookup"><span data-stu-id="eead5-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="eead5-119">现在，您可以使用此信息。</span><span class="sxs-lookup"><span data-stu-id="eead5-119">Now you can use this information.</span></span> <span data-ttu-id="eead5-120">下面的示例生成 C# 源代码。</span><span class="sxs-lookup"><span data-stu-id="eead5-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="eead5-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eead5-121">See also</span></span>

- [<span data-ttu-id="eead5-122">元数据</span><span class="sxs-lookup"><span data-stu-id="eead5-122">Metadata</span></span>](metadata.md)
- [<span data-ttu-id="eead5-123">入门</span><span class="sxs-lookup"><span data-stu-id="eead5-123">Getting Started</span></span>](../samples/getting-started-sample.md)
