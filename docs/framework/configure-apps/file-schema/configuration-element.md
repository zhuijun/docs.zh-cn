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
ms.openlocfilehash: 8f79981a55d0bc9b1cd522e45f5606fda102c72c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544683"
---
# <a name="configuration-element"></a><span data-ttu-id="c6ca5-102">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="c6ca5-102">\<configuration> element</span></span>

<span data-ttu-id="c6ca5-103">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="c6ca5-104">语法</span><span class="sxs-lookup"><span data-stu-id="c6ca5-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="c6ca5-105">特性</span><span class="sxs-lookup"><span data-stu-id="c6ca5-105">Attributes</span></span>

<span data-ttu-id="c6ca5-106">无</span><span class="sxs-lookup"><span data-stu-id="c6ca5-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="c6ca5-107">父元素</span><span class="sxs-lookup"><span data-stu-id="c6ca5-107">Parent element</span></span>

<span data-ttu-id="c6ca5-108">无</span><span class="sxs-lookup"><span data-stu-id="c6ca5-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="c6ca5-109">子元素</span><span class="sxs-lookup"><span data-stu-id="c6ca5-109">Child elements</span></span>

|     | <span data-ttu-id="c6ca5-110">说明</span><span class="sxs-lookup"><span data-stu-id="c6ca5-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="c6ca5-111">指定配置级的程序集绑定策略。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="c6ca5-112">**\<startup>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="c6ca5-113">启动设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="c6ca5-114">**\<runtime>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="c6ca5-115">运行时设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="c6ca5-116">[**\<system.runtime.remoting>** 设置架构](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c6ca5-116">[**\<system.runtime.remoting>** Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="c6ca5-117">远程处理设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="c6ca5-118">**\<system.Net>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="c6ca5-119">网络设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="c6ca5-120">**\<cryptographySettings>** 设置架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="c6ca5-121">加密设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="c6ca5-122">**\<configuration>** 节架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="c6ca5-123">配置节设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="c6ca5-124">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="c6ca5-125">跟踪和调试设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="c6ca5-126">[ASP.NET 配置设置架构](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c6ca5-126">[ASP.NET Configuration Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="c6ca5-127">ASP.NET 配置架构中的所有元素，包括用于配置 ASP.NET 网站和应用程序的元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="c6ca5-128">用于 *Web.config* 文件中。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="c6ca5-129">[**\<webServices>** 设置架构](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c6ca5-129">[**\<webServices>** Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="c6ca5-130">Web 服务设置架构中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="c6ca5-131">Web 设置架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="c6ca5-132">Web 设置架构中的所有元素，包括用于配置 ASP.NET 如何与主机应用程序（如 IIS）一起工作的元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="c6ca5-133">用于 *aspnet.config* 文件中。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c6ca5-134">备注</span><span class="sxs-lookup"><span data-stu-id="c6ca5-134">Remarks</span></span>

<span data-ttu-id="c6ca5-135">每个配置文件必须仅包含一个 **\<configuration>** 元素。</span><span class="sxs-lookup"><span data-stu-id="c6ca5-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6ca5-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="c6ca5-136">See also</span></span>

- [<span data-ttu-id="c6ca5-137">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c6ca5-137">Configuration file schema for the .NET Framework</span></span>](index.md)
