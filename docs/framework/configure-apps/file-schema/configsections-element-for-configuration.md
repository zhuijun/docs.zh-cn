---
title: <configuration> 的 <configSections> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 1e4bb7a7cfb0b140ca6d13c162708c3c30bd496d
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441682"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="72108-102">\<configuration> 的 \<configSections> 元素</span><span class="sxs-lookup"><span data-stu-id="72108-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="72108-103">包含配置节和命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="72108-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="72108-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="72108-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="72108-105">属性</span><span class="sxs-lookup"><span data-stu-id="72108-105">Attributes</span></span>

<span data-ttu-id="72108-106">无</span><span class="sxs-lookup"><span data-stu-id="72108-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="72108-107">父元素</span><span class="sxs-lookup"><span data-stu-id="72108-107">Parent element</span></span>

|     | <span data-ttu-id="72108-108">描述</span><span class="sxs-lookup"><span data-stu-id="72108-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="72108-109">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="72108-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="72108-110">子元素</span><span class="sxs-lookup"><span data-stu-id="72108-110">Child elements</span></span>

|     | <span data-ttu-id="72108-111">说明</span><span class="sxs-lookup"><span data-stu-id="72108-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="72108-112">包含配置节声明。</span><span class="sxs-lookup"><span data-stu-id="72108-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="72108-113">定义配置节的命名空间。</span><span class="sxs-lookup"><span data-stu-id="72108-113">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="72108-114">备注</span><span class="sxs-lookup"><span data-stu-id="72108-114">Remarks</span></span>

<span data-ttu-id="72108-115">如果此元素在配置文件中，则它必须是元素的第一个子元素 **\<configuration>** 。</span><span class="sxs-lookup"><span data-stu-id="72108-115">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="72108-116">示例</span><span class="sxs-lookup"><span data-stu-id="72108-116">Example</span></span>

<span data-ttu-id="72108-117">下面的示例演示如何定义配置节并定义该部分的设置：</span><span class="sxs-lookup"><span data-stu-id="72108-117">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="72108-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="72108-118">Configuration file</span></span>

<span data-ttu-id="72108-119">此元素可用于应用程序配置文件、计算机配置文件（*Machine.config*）以及不在应用程序目录级别的*Web.config*文件。</span><span class="sxs-lookup"><span data-stu-id="72108-119">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="72108-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="72108-120">See also</span></span>

- [<span data-ttu-id="72108-121">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="72108-121">Configuration file schema for the .NET Framework</span></span>](index.md)
