---
title: Web 设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: 030841330ff37cddb0c9e3e466a55a4be098e784
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088792"
---
# <a name="web-settings-schema"></a><span data-ttu-id="c0205-102">Web 设置架构</span><span class="sxs-lookup"><span data-stu-id="c0205-102">Web Settings Schema</span></span>
<span data-ttu-id="c0205-103">Web 设置指定 CPU 和执行级别 ASP.NET 设置，后者应用于由 ASP.NET 承载层托管的进程范围行为。</span><span class="sxs-lookup"><span data-stu-id="c0205-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="c0205-104">这些设置与 ASP.NET 应用程序的 Web.config 文件中指定的应用程序域类型设置不同。</span><span class="sxs-lookup"><span data-stu-id="c0205-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="c0205-105">Web 设置包含在 Aspnet.config 文件中，该文件位于各版本 .NET Framework 的安装文件夹内。</span><span class="sxs-lookup"><span data-stu-id="c0205-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="c0205-106">例如，.NET Framework 2.0 的 Aspnet .config 文件位于以下文件夹中：</span><span class="sxs-lookup"><span data-stu-id="c0205-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="c0205-107">其他任何配置文件（如 machine.config 文件、根 Web.config 或应用程序级别的 Web.config 文件）中都不使用 Web 设置。</span><span class="sxs-lookup"><span data-stu-id="c0205-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|<span data-ttu-id="c0205-108">元素</span><span class="sxs-lookup"><span data-stu-id="c0205-108">Element</span></span>|<span data-ttu-id="c0205-109">说明</span><span class="sxs-lookup"><span data-stu-id="c0205-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="c0205-110">包含 ASP.NET 承载层使用的信息。</span><span class="sxs-lookup"><span data-stu-id="c0205-110">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="c0205-111">指定 CPU 和执行级别 ASP.NET 设置，后者应用于由 ASP.NET 承载层托管的进程范围行为。</span><span class="sxs-lookup"><span data-stu-id="c0205-111">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0205-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="c0205-112">See also</span></span>

- [<span data-ttu-id="c0205-113">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c0205-113">Configuration File Schema</span></span>](../index.md)
