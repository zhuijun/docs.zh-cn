---
title: <configuration> 的 <configSections> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155344"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="4560a-102">\<configuration> 的 \<configSections> 元素</span><span class="sxs-lookup"><span data-stu-id="4560a-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="4560a-103">包含配置节和命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="4560a-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="4560a-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="4560a-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="4560a-105">特性</span><span class="sxs-lookup"><span data-stu-id="4560a-105">Attributes</span></span>

<span data-ttu-id="4560a-106">无</span><span class="sxs-lookup"><span data-stu-id="4560a-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4560a-107">父元素</span><span class="sxs-lookup"><span data-stu-id="4560a-107">Parent element</span></span>

|     | <span data-ttu-id="4560a-108">描述</span><span class="sxs-lookup"><span data-stu-id="4560a-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="4560a-109">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="4560a-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4560a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4560a-110">Child elements</span></span>

|     | <span data-ttu-id="4560a-111">说明</span><span class="sxs-lookup"><span data-stu-id="4560a-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="4560a-112">包含配置节声明。</span><span class="sxs-lookup"><span data-stu-id="4560a-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="4560a-113">定义配置节的命名空间。</span><span class="sxs-lookup"><span data-stu-id="4560a-113">Defines a namespace for configuration sections.</span></span> |
| [**\<remove>**](remove-element-for-configsections.md) | <span data-ttu-id="4560a-114">删除预定义的节或节组。</span><span class="sxs-lookup"><span data-stu-id="4560a-114">Removes a predefined section or section group.</span></span> |
| [**\<clear>**](clear-element-for-configsections.md) | <span data-ttu-id="4560a-115">清除所有之前定义的部分和节组。</span><span class="sxs-lookup"><span data-stu-id="4560a-115">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4560a-116">注解</span><span class="sxs-lookup"><span data-stu-id="4560a-116">Remarks</span></span>

<span data-ttu-id="4560a-117">如果此元素在配置文件中，则它必须是元素的第一个子元素 **\<configuration>** 。</span><span class="sxs-lookup"><span data-stu-id="4560a-117">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="4560a-118">示例</span><span class="sxs-lookup"><span data-stu-id="4560a-118">Example</span></span>

<span data-ttu-id="4560a-119">下面的示例演示如何定义配置节并定义该部分的设置：</span><span class="sxs-lookup"><span data-stu-id="4560a-119">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4560a-120">配置文件</span><span class="sxs-lookup"><span data-stu-id="4560a-120">Configuration file</span></span>

<span data-ttu-id="4560a-121">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="4560a-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4560a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4560a-122">See also</span></span>

- [<span data-ttu-id="4560a-123">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="4560a-123">Configuration file schema for the .NET Framework</span></span>](index.md)
