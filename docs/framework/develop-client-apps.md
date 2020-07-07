---
title: 使用 .NET Framework 开发基于 Windows 的客户端应用程序
description: 利用 .NET 开发基于 Windows 的应用程序。 可以使用通用 Windows 平台 (UWP)、Windows Presentation Foundation (WPF) 或 Windows 窗体。
ms.date: 01/09/2018
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
ms.openlocfilehash: 5920ecfae60274a8a504e4d300e531fd8b512901
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619385"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="89057-104">使用 .NET Framework 开发客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="89057-104">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="89057-105">可通过多种方法使用 .NET Framework 开发基于 Windows 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="89057-105">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="89057-106">可使用以下任意工具和框架：</span><span class="sxs-lookup"><span data-stu-id="89057-106">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="89057-107">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="89057-107">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="89057-108">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="89057-108">Windows Presentation Foundation (WPF)</span></span>](./wpf/index.md)
- [<span data-ttu-id="89057-109">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="89057-109">Windows Forms</span></span>](./winforms/index.md)

<span data-ttu-id="89057-110">本节包含的文章说明了如何使用 Windows Presentation Foundation 或 Windows 窗体创建基于 Windows 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="89057-110">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="89057-111">但是，还可利用 .NET Framework 创建 Web 应用程序，以及创建可通过 Microsoft Store（UWP 应用）发布的面向计算机或设备的客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="89057-111">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="89057-112">相关章节</span><span class="sxs-lookup"><span data-stu-id="89057-112">Related sections</span></span>

<span data-ttu-id="89057-113">[通用 Windows 平台](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="89057-113">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="89057-114">介绍如何创建可以通过 Microsoft Store 向用户提供的 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="89057-114">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="89057-115">[适用于 UWP 应用的 .NET API](/dotnet/api/index?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="89057-115">[.NET API for UWP apps](/dotnet/api/index?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="89057-116">支持 UWP 应用的 .NET 类型参考。</span><span class="sxs-lookup"><span data-stu-id="89057-116">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="89057-117">[多平台开发](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="89057-117">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="89057-118">介绍可以针对多个客户端应用类型使用 .NET Framework 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="89057-118">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="89057-119">[ASP.NET 网站入门](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="89057-119">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="89057-120">介绍使用 ASP.NET 开发 Web 应用的方法。</span><span class="sxs-lookup"><span data-stu-id="89057-120">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="89057-121">[适用于 Windows Phone Silverlight 的 .NET API](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="89057-121">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="89057-122">列出使用 Windows Phone Silverlight 构建应用时可使用的 .NET Framework API。</span><span class="sxs-lookup"><span data-stu-id="89057-122">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="89057-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="89057-123">See also</span></span>

- [<span data-ttu-id="89057-124">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="89057-124">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="89057-125">概述</span><span class="sxs-lookup"><span data-stu-id="89057-125">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="89057-126">开发指南</span><span class="sxs-lookup"><span data-stu-id="89057-126">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="89057-127">Windows 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="89057-127">Windows Service Applications</span></span>](./windows-services/index.md)
