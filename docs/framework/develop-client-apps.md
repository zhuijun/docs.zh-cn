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
ms.openlocfilehash: 33d0ca2918e4e3b00e2b09f7a47c538bbe903dba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547904"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="efffa-104">使用 .NET Framework 开发客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="efffa-104">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="efffa-105">可通过多种方法使用 .NET Framework 开发基于 Windows 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="efffa-105">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="efffa-106">可使用以下任意工具和框架：</span><span class="sxs-lookup"><span data-stu-id="efffa-106">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="efffa-107">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="efffa-107">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="efffa-108">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="efffa-108">Windows Presentation Foundation (WPF)</span></span>](/dotnet/desktop/wpf/)
- [<span data-ttu-id="efffa-109">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="efffa-109">Windows Forms</span></span>](/dotnet/desktop/winforms/)

<span data-ttu-id="efffa-110">本节包含的文章说明了如何使用 Windows Presentation Foundation 或 Windows 窗体创建基于 Windows 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="efffa-110">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="efffa-111">但是，还可利用 .NET Framework 创建 Web 应用程序，以及创建可通过 Microsoft Store（UWP 应用）发布的面向计算机或设备的客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="efffa-111">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="efffa-112">相关章节</span><span class="sxs-lookup"><span data-stu-id="efffa-112">Related sections</span></span>

<span data-ttu-id="efffa-113">[通用 Windows 平台](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="efffa-113">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="efffa-114">介绍如何创建可以通过 Microsoft Store 向用户提供的 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="efffa-114">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="efffa-115">[适用于 UWP 应用的 .NET API](../../api/index.md?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="efffa-115">[.NET API for UWP apps](../../api/index.md?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="efffa-116">支持 UWP 应用的 .NET 类型参考。</span><span class="sxs-lookup"><span data-stu-id="efffa-116">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="efffa-117">[多平台开发](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="efffa-117">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="efffa-118">介绍可以针对多个客户端应用类型使用 .NET Framework 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="efffa-118">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="efffa-119">[ASP.NET 网站入门](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="efffa-119">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="efffa-120">介绍使用 ASP.NET 开发 Web 应用的方法。</span><span class="sxs-lookup"><span data-stu-id="efffa-120">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="efffa-121">[适用于 Windows Phone Silverlight 的 .NET API](/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="efffa-121">[.NET API for Windows Phone Silverlight](/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="efffa-122">列出使用 Windows Phone Silverlight 构建应用时可使用的 .NET Framework API。</span><span class="sxs-lookup"><span data-stu-id="efffa-122">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="efffa-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="efffa-123">See also</span></span>

- [<span data-ttu-id="efffa-124">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="efffa-124">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="efffa-125">概述</span><span class="sxs-lookup"><span data-stu-id="efffa-125">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="efffa-126">开发指南</span><span class="sxs-lookup"><span data-stu-id="efffa-126">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="efffa-127">Windows 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="efffa-127">Windows Service Applications</span></span>](./windows-services/index.md)
