---
title: 启动设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701510"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="f8684-102">启动设置架构</span><span class="sxs-lookup"><span data-stu-id="f8684-102">Startup settings schema</span></span>

<span data-ttu-id="f8684-103">启动设置会指定应运行应用程序的公共语言运行时的版本。</span><span class="sxs-lookup"><span data-stu-id="f8684-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="f8684-104">元素</span><span class="sxs-lookup"><span data-stu-id="f8684-104">Element</span></span>|<span data-ttu-id="f8684-105">说明</span><span class="sxs-lookup"><span data-stu-id="f8684-105">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="f8684-106">指定应用程序仅支持 1.0 版本的公共语言运行时。</span><span class="sxs-lookup"><span data-stu-id="f8684-106">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f8684-107">使用运行时版本1.1 生成的应用程序应使用 **\<supportedRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="f8684-107">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="f8684-108">指定应用程序支持的公共语言运行时版本。</span><span class="sxs-lookup"><span data-stu-id="f8684-108">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="f8684-109">包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="f8684-109">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8684-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="f8684-110">See also</span></span>

- [<span data-ttu-id="f8684-111">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="f8684-111">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f8684-112">如何：将应用配置为支持 .NET Framework 4 或更高版本</span><span class="sxs-lookup"><span data-stu-id="f8684-112">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
