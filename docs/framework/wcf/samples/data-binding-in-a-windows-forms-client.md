---
title: Windows 窗体客户端中的数据绑定
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d2784c86bc3ef84f99f4731f441019b3f568b321
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575480"
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="2e978-102">Windows 窗体客户端中的数据绑定</span><span class="sxs-lookup"><span data-stu-id="2e978-102">Data Binding in a Windows Forms Client</span></span>
<span data-ttu-id="2e978-103">此示例演示如何绑定到 Windows 窗体应用程序中 Windows Communication Foundation （WCF）服务返回的数据。</span><span class="sxs-lookup"><span data-stu-id="2e978-103">This sample demonstrates how to bind to data returned by a Windows Communication Foundation (WCF) service in a Windows Forms application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e978-104">本文的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="2e978-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="2e978-105">本示例演示一个服务，该服务可实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="2e978-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2e978-106">该示例包含一个客户端 Windows 窗体应用程序（.exe）和由 Internet Information Services （IIS）承载的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="2e978-106">The sample consists of a client Windows Forms application (.exe) and a WCF service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="2e978-107">协定由 `IWeatherService` 接口定义，该接口公开一个名为 `GetWeatherData` 的操作。</span><span class="sxs-lookup"><span data-stu-id="2e978-107">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="2e978-108">此操作接受一个城市数组并返回一个 `WeatherData` 对象数组，这些对象表示城市的预报高温和预报低温。</span><span class="sxs-lookup"><span data-stu-id="2e978-108">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="2e978-109">在 Windows 窗体应用程序中的客户端上进行数据绑定。</span><span class="sxs-lookup"><span data-stu-id="2e978-109">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="2e978-110">在 Windows 窗体设计器中定义一个 `DataGridView`（它是数据的图形化表示形式）。</span><span class="sxs-lookup"><span data-stu-id="2e978-110">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="2e978-111">还会创建一个名为 `BindingSource` 的中间媒介。</span><span class="sxs-lookup"><span data-stu-id="2e978-111">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="2e978-112">将 `BindingSource` 的数据源设置为由服务返回的数据数组。</span><span class="sxs-lookup"><span data-stu-id="2e978-112">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="2e978-113">`BindingSource` 的用途是提供数据与数据视图之间的间接层。</span><span class="sxs-lookup"><span data-stu-id="2e978-113">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="2e978-114">与数据的所有交互（如导航、排序、筛选和更新）都是通过调用 `BindingSource` 组件来完成的。</span><span class="sxs-lookup"><span data-stu-id="2e978-114">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="2e978-115">若要完成对 `DataGridView` 的数据绑定，请将 `datasource` 的 `DataGridView` 设置为 `BindingSource` 对象。</span><span class="sxs-lookup"><span data-stu-id="2e978-115">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="2e978-116">然后，从 WCF 服务返回的所有数据都以图形方式显示给用户。</span><span class="sxs-lookup"><span data-stu-id="2e978-116">All of the data returned from the WCF service is then displayed graphically to the user.</span></span>  <span data-ttu-id="2e978-117">每当用户单击按钮时，会在数据绑定的 `DataGridView` 中自动更新返回的数据。</span><span class="sxs-lookup"><span data-stu-id="2e978-117">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e978-118">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="2e978-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2e978-119">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2e978-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2e978-120">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2e978-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2e978-121">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2e978-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2e978-122">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="2e978-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e978-123">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="2e978-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2e978-124">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="2e978-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e978-125">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="2e978-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
