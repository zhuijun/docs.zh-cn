---
title: 生成数据服务客户端库（WCF 数据服务）
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 050a791736e90b5daf46fd272197ca21a220afb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172614"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="b777e-102">生成数据服务客户端库（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="b777e-102">Generating the Data Service Client Library (WCF Data Services)</span></span>

<span data-ttu-id="b777e-103">实现 Open Data Protocol (OData) 的数据服务可以返回描述 OData 源公开的数据模型的服务元数据文档。</span><span class="sxs-lookup"><span data-stu-id="b777e-103">A data service that implements the Open Data Protocol (OData) can return a service metadata document that describes the data model exposed by the OData feed.</span></span> <span data-ttu-id="b777e-104">有关详细信息，请参阅 [OData：概述](https://www.odata.org/documentation/odata-version-2-0/overview/) 一文中的服务元数据文档部分。</span><span class="sxs-lookup"><span data-stu-id="b777e-104">For more information, see the Service Metadata Document section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span> <span data-ttu-id="b777e-105">您可以使用 Visual Studio 中的 " **添加服务引用** " 对话框添加对基于 OData 的服务的引用。</span><span class="sxs-lookup"><span data-stu-id="b777e-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an OData-based service.</span></span> <span data-ttu-id="b777e-106">使用此工具添加对客户端项目中 OData 源返回的元数据的引用时，它将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b777e-106">When you use this tool to add a reference to the metadata returned by an OData feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="b777e-107">从数据服务请求服务元数据文档并截获返回的元数据。</span><span class="sxs-lookup"><span data-stu-id="b777e-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b777e-108">返回的元数据作为 .edmx 文件存储在客户端项目中。</span><span class="sxs-lookup"><span data-stu-id="b777e-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="b777e-109">此 .edmx 文件无法通过实体数据模型设计器打开，因为此文件的格式与实体框架所使用的 .edmx 文件的格式不相同。</span><span class="sxs-lookup"><span data-stu-id="b777e-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="b777e-110">可以通过使用 XML 编辑器或任何文本编辑器查看此元数据文件。</span><span class="sxs-lookup"><span data-stu-id="b777e-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="b777e-111">有关详细信息，请参阅[ \[ MC-EDMX \] ：用于数据服务打包格式的实体数据模型](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16)。</span><span class="sxs-lookup"><span data-stu-id="b777e-111">For more information, see [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).</span></span>
  
- <span data-ttu-id="b777e-112">作为从 <xref:System.Data.Services.Client.DataServiceContext> 继承的实体容器类生成数据服务的表示形式。</span><span class="sxs-lookup"><span data-stu-id="b777e-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="b777e-113">此生成的实体容器类与实体数据模型工具生成的实体容器类似。</span><span class="sxs-lookup"><span data-stu-id="b777e-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="b777e-114">有关详细信息，请参阅[对象服务概述 (Entity Framework)](/previous-versions/bb386871(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="b777e-114">For more information, see [Object Services Overview (Entity Framework)](/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="b777e-115">为在服务元数据中发现的数据模型类型生成数据类。</span><span class="sxs-lookup"><span data-stu-id="b777e-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="b777e-116">在项目中添加对 `System.Data.Services.Client` 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="b777e-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="b777e-117">有关详细信息，请参阅 [如何：添加数据服务引用](how-to-add-a-data-service-reference-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b777e-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="b777e-118">还可以通过在命令提示符下使用 [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) 工具来生成客户端数据服务类。</span><span class="sxs-lookup"><span data-stu-id="b777e-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="b777e-119">有关详细信息，请参阅 [如何：手动生成客户端数据服务类](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b777e-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="b777e-120">客户端数据类型映射</span><span class="sxs-lookup"><span data-stu-id="b777e-120">Client Data Type Mapping</span></span>  

 <span data-ttu-id="b777e-121">使用 Visual Studio 中的 " **添加服务引用** " 对话框或 `DataSvcUtil.exe` 工具生成基于 OData 源的客户端数据类时，.NET Framework 数据类型将按以下方式映射到数据模型中的基元类型：</span><span class="sxs-lookup"><span data-stu-id="b777e-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an OData feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="b777e-122">数据模型类型</span><span class="sxs-lookup"><span data-stu-id="b777e-122">Data model type</span></span>|<span data-ttu-id="b777e-123">.NET framework 数据类型</span><span class="sxs-lookup"><span data-stu-id="b777e-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="b777e-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="b777e-124"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="b777e-125">有关详细信息，请参阅 [OData：概述](https://www.odata.org/documentation/odata-version-2-0/overview/) 一文中的基元数据类型部分。</span><span class="sxs-lookup"><span data-stu-id="b777e-125">For more information, see the Primitive Data Types section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b777e-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="b777e-126">See also</span></span>

- [<span data-ttu-id="b777e-127">WCF 数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="b777e-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="b777e-128">快速入门</span><span class="sxs-lookup"><span data-stu-id="b777e-128">Quickstart</span></span>](quickstart-wcf-data-services.md)
