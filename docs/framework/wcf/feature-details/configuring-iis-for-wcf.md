---
title: 为 Windows Communication Foundation 配置 Internet Information Services 7.0
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 6343049e2a21b06965a8c7851d891303a49c82b5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597561"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="d8bce-102">为 Windows Communication Foundation 配置 Internet Information Services 7.0</span><span class="sxs-lookup"><span data-stu-id="d8bce-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="d8bce-103">Internet Information Services (IIS) 7.0 具有模块化设计，允许有选择地安装需要的组件。</span><span class="sxs-lookup"><span data-stu-id="d8bce-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="d8bce-104">此设计基于 Windows Vista 中引入的新的清单驱动组件化技术。</span><span class="sxs-lookup"><span data-stu-id="d8bce-104">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="d8bce-105">IIS 7.0 的40多个独立功能组件可以独立安装。</span><span class="sxs-lookup"><span data-stu-id="d8bce-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="d8bce-106">这使 IT 专业人士能够轻松地按需要自定义安装。</span><span class="sxs-lookup"><span data-stu-id="d8bce-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="d8bce-107">本主题讨论如何配置 IIS 7.0 以用于 Windows Communication Foundation （WCF），并确定所需的组件。</span><span class="sxs-lookup"><span data-stu-id="d8bce-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="d8bce-108">最小安装：安装 WAS</span><span class="sxs-lookup"><span data-stu-id="d8bce-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="d8bce-109">整个 IIS 7.0 包的最小安装是安装 Windows 进程激活服务（WAS）。</span><span class="sxs-lookup"><span data-stu-id="d8bce-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="d8bce-110">WAS 是一项独立功能，并且是 IIS 7.0 中唯一适用于所有 Windows Vista 操作系统（Home Basic、Home Premium、Business 和旗舰版和企业版）的功能。</span><span class="sxs-lookup"><span data-stu-id="d8bce-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="d8bce-111">在 "控制面板" 中，单击 "**程序**"，然后单击 "**程序和功能**" 下的 "**打开或关闭 Windows 功能**"，WAS 组件显示在列表中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d8bce-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="d8bce-112">![打开或关闭功能对话框](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="d8bce-112">![Turn Features On or Off Dialog](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="d8bce-113">此功能具有下列子组件：</span><span class="sxs-lookup"><span data-stu-id="d8bce-113">This feature has the following sub-components:</span></span>

- <span data-ttu-id="d8bce-114">.NET 环境</span><span class="sxs-lookup"><span data-stu-id="d8bce-114">.NET Environment</span></span>

- <span data-ttu-id="d8bce-115">配置 API</span><span class="sxs-lookup"><span data-stu-id="d8bce-115">Configuration APIs</span></span>

- <span data-ttu-id="d8bce-116">进程模型</span><span class="sxs-lookup"><span data-stu-id="d8bce-116">Process Model</span></span>

 <span data-ttu-id="d8bce-117">如果选择的根节点为，则默认情况下仅检查 "**进程模型**" 子节点。</span><span class="sxs-lookup"><span data-stu-id="d8bce-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="d8bce-118">请注意，使用此安装时，你将只安装 WAS，因为没有用于 Web 服务器的支持功能。</span><span class="sxs-lookup"><span data-stu-id="d8bce-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="d8bce-119">若要使 WCF 或任何 ASP.NET 应用程序正常工作，请选中 " **.Net 环境**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="d8bce-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="d8bce-120">这意味着，所有 WAS 组件都需要使 WCF 和 ASP.NET 能够正常运行。</span><span class="sxs-lookup"><span data-stu-id="d8bce-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="d8bce-121">您安装其中任何组件后，会自动选中这些组件。</span><span class="sxs-lookup"><span data-stu-id="d8bce-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="d8bce-122">IIS 7.0：默认安装</span><span class="sxs-lookup"><span data-stu-id="d8bce-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="d8bce-123">通过检查**Internet Information Services**功能，会自动检查某些子节点，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d8bce-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="d8bce-124">![IIS 7.0 功能的默认设置](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="d8bce-124">![Default settings for IIS 7.0 features](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="d8bce-125">这是 IIS 7.0 的默认安装。</span><span class="sxs-lookup"><span data-stu-id="d8bce-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="d8bce-126">使用此安装，可以使用 IIS 7.0 为静态内容（如 HTML 页面和其他内容）提供服务。</span><span class="sxs-lookup"><span data-stu-id="d8bce-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="d8bce-127">但是，不能运行 ASP.NET 或 CGI 应用程序，也不能托管 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="d8bce-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="d8bce-128">IIS 7.0：带 ASP.NET 支持的安装</span><span class="sxs-lookup"><span data-stu-id="d8bce-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="d8bce-129">必须安装 ASP.NET 才能在 IIS 7.0 上进行 ASP.NET 工作。</span><span class="sxs-lookup"><span data-stu-id="d8bce-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="d8bce-130">检查**ASP.NET**后，屏幕应如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d8bce-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="d8bce-131">![Asp.NET 需要的设置](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="d8bce-131">![Asp.NET required settings](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="d8bce-132">这是 WCF 和 ASP.NET 应用程序在 IIS 7.0 中工作的最小环境。</span><span class="sxs-lookup"><span data-stu-id="d8bce-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="d8bce-133">IIS 7.0：带 IIS 6.0 兼容组件的安装</span><span class="sxs-lookup"><span data-stu-id="d8bce-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="d8bce-134">在使用 Visual Studio 2005 的系统上安装 IIS 7.0，或在配置使用 IIS 6.0 元数据库 API 的虚拟应用程序的其他一些自动化脚本或工具（如 Adsutil.vbs）时，请确保检查 IIS 6.0**脚本工具**。</span><span class="sxs-lookup"><span data-stu-id="d8bce-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="d8bce-135">这会自动检查 IIS 6.0**管理兼容性**的其他子节点。</span><span class="sxs-lookup"><span data-stu-id="d8bce-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="d8bce-136">下图显示了完成此操作后的屏幕：</span><span class="sxs-lookup"><span data-stu-id="d8bce-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="d8bce-137">![IIS 6.0 管理兼容性设置](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="d8bce-137">![IIS 6.0 Management Compatibility Settings](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="d8bce-138">通过此安装，你可以使用 Web 上提供的 IIS 7.0、ASP.NET 和 WCF 功能和示例所需的一切。</span><span class="sxs-lookup"><span data-stu-id="d8bce-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="d8bce-139">请求限制</span><span class="sxs-lookup"><span data-stu-id="d8bce-139">Request Limits</span></span>
 <span data-ttu-id="d8bce-140">在带有 IIS 7 的 Windows Vista 上，和设置的默认值已 `maxUri` `maxQueryStringSize` 更改。</span><span class="sxs-lookup"><span data-stu-id="d8bce-140">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="d8bce-141">默认情况下，IIS 7.0 中的请求筛选功能允许 URL 的长度为 4096 个字符，查询字符串的长度为 2048 个字符。</span><span class="sxs-lookup"><span data-stu-id="d8bce-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="d8bce-142">更改这些默认值，可将以下 XML 添加到 App.config 文件中。</span><span class="sxs-lookup"><span data-stu-id="d8bce-142">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="d8bce-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8bce-143">See also</span></span>

- [<span data-ttu-id="d8bce-144">WAS 激活体系结构</span><span class="sxs-lookup"><span data-stu-id="d8bce-144">WAS Activation Architecture</span></span>](was-activation-architecture.md)
- [<span data-ttu-id="d8bce-145">配置 WAS 以用于 WCF</span><span class="sxs-lookup"><span data-stu-id="d8bce-145">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="d8bce-146">如何：安装和配置 WCF 激活组件</span><span class="sxs-lookup"><span data-stu-id="d8bce-146">How to: Install and Configure WCF Activation Components</span></span>](how-to-install-and-configure-wcf-activation-components.md)
- <span data-ttu-id="d8bce-147">[Windows Server App Fabric 承载功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d8bce-147">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
