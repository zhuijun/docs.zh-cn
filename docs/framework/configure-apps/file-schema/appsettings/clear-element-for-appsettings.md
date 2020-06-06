---
title: <appSettings> 的 <clear> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214814"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="ee689-102">\<appSettings> 的 \<clear> 元素</span><span class="sxs-lookup"><span data-stu-id="ee689-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="ee689-103">清除自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="ee689-103">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="ee689-104">语法</span><span class="sxs-lookup"><span data-stu-id="ee689-104">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="ee689-105">特性</span><span class="sxs-lookup"><span data-stu-id="ee689-105">Attributes</span></span>

<span data-ttu-id="ee689-106">无</span><span class="sxs-lookup"><span data-stu-id="ee689-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="ee689-107">父元素</span><span class="sxs-lookup"><span data-stu-id="ee689-107">Parent element</span></span>

|     | <span data-ttu-id="ee689-108">描述</span><span class="sxs-lookup"><span data-stu-id="ee689-108">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="ee689-109">包含自定义应用程序设置，如文件路径、XML Web service Url 或任何其他自定义应用程序配置信息。</span><span class="sxs-lookup"><span data-stu-id="ee689-109">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ee689-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ee689-110">Child elements</span></span>

<span data-ttu-id="ee689-111">无</span><span class="sxs-lookup"><span data-stu-id="ee689-111">None</span></span>

## <a name="example"></a><span data-ttu-id="ee689-112">示例</span><span class="sxs-lookup"><span data-stu-id="ee689-112">Example</span></span>

<span data-ttu-id="ee689-113">下面的示例演示如何清除自定义配置设置：</span><span class="sxs-lookup"><span data-stu-id="ee689-113">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="ee689-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee689-114">See also</span></span>

- [<span data-ttu-id="ee689-115">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="ee689-115">Configuration file schema for the .NET Framework</span></span>](../index.md)
