---
title: <configuration> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921252"
---
# <a name="configuration-element"></a><span data-ttu-id="58e18-102">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="58e18-102">\<configuration> element</span></span>

<span data-ttu-id="58e18-103">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="58e18-104">语法</span><span class="sxs-lookup"><span data-stu-id="58e18-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="58e18-105">特性</span><span class="sxs-lookup"><span data-stu-id="58e18-105">Attributes</span></span>

<span data-ttu-id="58e18-106">无</span><span class="sxs-lookup"><span data-stu-id="58e18-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="58e18-107">父元素</span><span class="sxs-lookup"><span data-stu-id="58e18-107">Parent element</span></span>

<span data-ttu-id="58e18-108">无</span><span class="sxs-lookup"><span data-stu-id="58e18-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="58e18-109">子元素</span><span class="sxs-lookup"><span data-stu-id="58e18-109">Child elements</span></span>

|     | <span data-ttu-id="58e18-110">说明</span><span class="sxs-lookup"><span data-stu-id="58e18-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="58e18-111">指定配置级的程序集绑定策略。</span><span class="sxs-lookup"><span data-stu-id="58e18-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="58e18-112">**\<startup>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="58e18-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="58e18-113">启动设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="58e18-114">**\<runtime>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="58e18-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="58e18-115">运行时设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="58e18-116">[**\<system.runtime.remoting>** 设置架构](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58e18-116">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="58e18-117">远程处理设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="58e18-118">**\<system.Net>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="58e18-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="58e18-119">网络设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="58e18-120">**\<cryptographySettings>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="58e18-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="58e18-121">加密设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="58e18-122">**\<configuration>** 节架构</span><span class="sxs-lookup"><span data-stu-id="58e18-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="58e18-123">配置节设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="58e18-124">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="58e18-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="58e18-125">跟踪和调试设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="58e18-126">[ASP.NET 配置设置架构](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58e18-126">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="58e18-127">ASP.NET 配置架构中的所有元素，包括用于配置 ASP.NET 网站和应用程序的元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="58e18-128">在 web.config 文件中*使用。*</span><span class="sxs-lookup"><span data-stu-id="58e18-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="58e18-129">[**\<webServices>** 设置架构](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="58e18-129">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="58e18-130">Web 服务设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="58e18-131">Web 设置架构</span><span class="sxs-lookup"><span data-stu-id="58e18-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="58e18-132">Web 设置架构中的所有元素，包括用于配置 ASP.NET 如何与主机应用程序（如 IIS）一起工作的元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="58e18-133">用于*aspnet .config*文件中。</span><span class="sxs-lookup"><span data-stu-id="58e18-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="58e18-134">注解</span><span class="sxs-lookup"><span data-stu-id="58e18-134">Remarks</span></span>

<span data-ttu-id="58e18-135">每个配置文件必须仅包含一个 **\<configuration>** 元素。</span><span class="sxs-lookup"><span data-stu-id="58e18-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="58e18-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58e18-136">See also</span></span>

- [<span data-ttu-id="58e18-137">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="58e18-137">Configuration file schema for the .NET Framework</span></span>](index.md)
