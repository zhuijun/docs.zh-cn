---
title: 如何：从服务终结点导出元数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 58e86e5566775048e081bfb4ac217a7747b98a35
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579405"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="869c6-102">如何：从服务终结点导出元数据</span><span class="sxs-lookup"><span data-stu-id="869c6-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="869c6-103">本主题介绍如何从服务终结点导出元数据。</span><span class="sxs-lookup"><span data-stu-id="869c6-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="869c6-104">从服务终结点导出元数据</span><span class="sxs-lookup"><span data-stu-id="869c6-104">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="869c6-105">创建一个新的 Visual Studio 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="869c6-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="869c6-106">在生成的 Program.cs 文件的 main() 方法中添加下列步骤所示的代码。</span><span class="sxs-lookup"><span data-stu-id="869c6-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="869c6-107">创建 <xref:System.ServiceModel.Description.WsdlExporter>。</span><span class="sxs-lookup"><span data-stu-id="869c6-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="869c6-108">将 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 属性设置为 <xref:System.ServiceModel.Description.PolicyVersion> 枚举值之一。</span><span class="sxs-lookup"><span data-stu-id="869c6-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="869c6-109">此示例将该值设置为与 WS-Policy 1.5 对应的 <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>。</span><span class="sxs-lookup"><span data-stu-id="869c6-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="869c6-110">创建 <xref:System.ServiceModel.Description.ServiceEndpoint> 对象的数组。</span><span class="sxs-lookup"><span data-stu-id="869c6-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="869c6-111">为每个服务终结点导出元数据。</span><span class="sxs-lookup"><span data-stu-id="869c6-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="869c6-112">检查以确保在导出过程中不会发生任何错误，并检索元数据。</span><span class="sxs-lookup"><span data-stu-id="869c6-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="869c6-113">现在可以使用元数据，例如通过调用 <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> 方法将它写入文件。</span><span class="sxs-lookup"><span data-stu-id="869c6-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="869c6-114">示例</span><span class="sxs-lookup"><span data-stu-id="869c6-114">Example</span></span>  
 <span data-ttu-id="869c6-115">下面列出了此示例的完整代码。</span><span class="sxs-lookup"><span data-stu-id="869c6-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="869c6-116">编译代码</span><span class="sxs-lookup"><span data-stu-id="869c6-116">Compiling the Code</span></span>  
 <span data-ttu-id="869c6-117">编译 Program.cs 时引用 System.ServiceModel.dll。</span><span class="sxs-lookup"><span data-stu-id="869c6-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="869c6-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="869c6-118">See also</span></span>

- [<span data-ttu-id="869c6-119">元数据体系结构概述</span><span class="sxs-lookup"><span data-stu-id="869c6-119">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="869c6-120">使用元数据</span><span class="sxs-lookup"><span data-stu-id="869c6-120">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="869c6-121">终结点：地址、绑定和协定</span><span class="sxs-lookup"><span data-stu-id="869c6-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
