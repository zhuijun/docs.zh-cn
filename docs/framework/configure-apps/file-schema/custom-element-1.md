---
title: SingleTagSectionHandler 的自定义元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635402"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="9be0b-102">SingleTagSectionHandler 的自定义元素</span><span class="sxs-lookup"><span data-stu-id="9be0b-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="9be0b-103">定义自定义配置节中由 \<section> 元素定义并使用类的设置 <xref:System.Configuration.SingleTagSectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="9be0b-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="9be0b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="9be0b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="9be0b-105">语法</span><span class="sxs-lookup"><span data-stu-id="9be0b-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="9be0b-106">特性</span><span class="sxs-lookup"><span data-stu-id="9be0b-106">Attributes</span></span>

<span data-ttu-id="9be0b-107">属性和属性值是用户定义的。</span><span class="sxs-lookup"><span data-stu-id="9be0b-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="9be0b-108">父元素</span><span class="sxs-lookup"><span data-stu-id="9be0b-108">Parent element</span></span>

|     | <span data-ttu-id="9be0b-109">描述</span><span class="sxs-lookup"><span data-stu-id="9be0b-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="9be0b-110">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="9be0b-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9be0b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9be0b-111">Child elements</span></span>

<span data-ttu-id="9be0b-112">无</span><span class="sxs-lookup"><span data-stu-id="9be0b-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="9be0b-113">备注</span><span class="sxs-lookup"><span data-stu-id="9be0b-113">Remarks</span></span>

<span data-ttu-id="9be0b-114">**\<sectionName>** 元素是由元素中的标记定义的自定义元素 [**\<section>**](section-element.md) [**\<configSections>**](configsections-element-for-configuration.md) 。</span><span class="sxs-lookup"><span data-stu-id="9be0b-114">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="9be0b-115">调用时，配置系统返回 <xref:System.Collections.IDictionary> 对象 <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9be0b-115">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="9be0b-116">示例</span><span class="sxs-lookup"><span data-stu-id="9be0b-116">Example</span></span>

<span data-ttu-id="9be0b-117">下面的示例声明一个名为的自定义元素 **\<sampleSection>** ，该元素包含由类读取的设置 <xref:System.Configuration.SingleTagSectionHandler> ：</span><span class="sxs-lookup"><span data-stu-id="9be0b-117">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="9be0b-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="9be0b-118">Configuration file</span></span>

<span data-ttu-id="9be0b-119">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别*的 web.config 文件*。</span><span class="sxs-lookup"><span data-stu-id="9be0b-119">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="9be0b-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9be0b-120">See also</span></span>

- [<span data-ttu-id="9be0b-121">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="9be0b-121">Configuration file schema for the .NET Framework</span></span>](index.md)
