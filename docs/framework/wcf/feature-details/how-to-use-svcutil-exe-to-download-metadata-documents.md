---
title: 如何：使用 Svcutil.exe 下载元数据文档
description: 了解如何使用 Svcutil.exe 从正在运行的服务下载元数据并将元数据保存到本地文件。
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246761"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="4e52c-103">如何：使用 Svcutil.exe 下载元数据文档</span><span class="sxs-lookup"><span data-stu-id="4e52c-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="4e52c-104">您可以使用 Svcutil.exe 从正在运行的服务中下载元数据并将元数据保存到本地文件。</span><span class="sxs-lookup"><span data-stu-id="4e52c-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="4e52c-105">对于 HTTP 和 HTTPS URL 方案，Svcutil.exe 尝试使用 Ws-metadataexchange 和[XML Web Service 发现](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))检索元数据。</span><span class="sxs-lookup"><span data-stu-id="4e52c-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="4e52c-106">对于所有其他 URL 架构，Svcutil.exe 仅使用 WS-MetadataExchange。</span><span class="sxs-lookup"><span data-stu-id="4e52c-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="4e52c-107">默认情况下，Svcutil.exe 使用 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 类中定义的绑定。</span><span class="sxs-lookup"><span data-stu-id="4e52c-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="4e52c-108">若要配置用于 WS-MetadataExchange 的绑定，必须在 Svcutil.exe 的配置文件 (svcutil.exe.config) 中定义一个客户端终结点，使该终结点使用 `IMetadataExchange` 约定，并具有与元数据终结点地址的统一资源标识符 (URI) 架构相同的名称。</span><span class="sxs-lookup"><span data-stu-id="4e52c-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="4e52c-109">当运行 Svcutil.exe 获取提供两个不同服务协定的服务的元数据时，每个服务协定分别包含同一名称的操作，Svcutil.exe 显示一个错误，指出 "无法从 ... 中获取元数据 ..."。例如，如果你有一个服务，该服务公开一个名为的服务协定，该协定 `ICarService` 具有一个操作， `Get(Car c)` 并且该服务公开了一个 `IBookService` 具有操作的名为的服务协定 `Get(Book b)` 。</span><span class="sxs-lookup"><span data-stu-id="4e52c-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="4e52c-110">要解决此问题，请执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="4e52c-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="4e52c-111">重命名其中的一项操作。</span><span class="sxs-lookup"><span data-stu-id="4e52c-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="4e52c-112">将 <xref:System.ServiceModel.OperationContractAttribute.Name%2A> 设置为其他名称。</span><span class="sxs-lookup"><span data-stu-id="4e52c-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="4e52c-113">使用 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 属性将其中一项操作的命名空间设置为其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="4e52c-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="4e52c-114">使用 Svcutil.exe 下载元数据</span><span class="sxs-lookup"><span data-stu-id="4e52c-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="4e52c-115">在以下位置找到 Svcutil.exe 工具：</span><span class="sxs-lookup"><span data-stu-id="4e52c-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="4e52c-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="4e52c-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="4e52c-117">在命令提示符处，使用下面的格式启动该工具。</span><span class="sxs-lookup"><span data-stu-id="4e52c-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="4e52c-118">您必须指定 `/t:metadata` 选项才能下载元数据。</span><span class="sxs-lookup"><span data-stu-id="4e52c-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="4e52c-119">否则，会生成客户端代码和配置。</span><span class="sxs-lookup"><span data-stu-id="4e52c-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="4e52c-120"><`url`>参数指定提供元数据的服务终结点的 URL 或联机托管的元数据文档。</span><span class="sxs-lookup"><span data-stu-id="4e52c-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="4e52c-121"><`epr`> 参数指定一个 XML 文件的路径，该文件包含 `EndpointAddress` 支持 ws-metadataexchange 的服务终结点的 ws-addressing。</span><span class="sxs-lookup"><span data-stu-id="4e52c-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="4e52c-122">有关使用此工具进行元数据下载的更多选项， [Svcutil.exe](../servicemodel-metadata-utility-tool-svcutil-exe.md)请参阅 ""</span><span class="sxs-lookup"><span data-stu-id="4e52c-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e52c-123">示例</span><span class="sxs-lookup"><span data-stu-id="4e52c-123">Example</span></span>  
 <span data-ttu-id="4e52c-124">下面的命令从正在运行的服务中下载元数据文档。</span><span class="sxs-lookup"><span data-stu-id="4e52c-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e52c-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e52c-125">See also</span></span>

- [<span data-ttu-id="4e52c-126">ServiceModel 元数据实用工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="4e52c-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
