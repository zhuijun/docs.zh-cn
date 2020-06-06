---
title: NameValueSectionHandler 和 DictionarySectionHandler 的自定义元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215476"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="74a82-102">NameValueSectionHandler 和 DictionarySectionHandler 的自定义元素</span><span class="sxs-lookup"><span data-stu-id="74a82-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="74a82-103">定义使用和类的自定义配置节的设置 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="74a82-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="74a82-104">特性</span><span class="sxs-lookup"><span data-stu-id="74a82-104">Attributes</span></span>

<span data-ttu-id="74a82-105">无</span><span class="sxs-lookup"><span data-stu-id="74a82-105">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="74a82-106">父元素</span><span class="sxs-lookup"><span data-stu-id="74a82-106">Parent element</span></span>

|     | <span data-ttu-id="74a82-107">描述</span><span class="sxs-lookup"><span data-stu-id="74a82-107">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="74a82-108">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="74a82-108">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="74a82-109">子元素</span><span class="sxs-lookup"><span data-stu-id="74a82-109">Child elements</span></span>

|     | <span data-ttu-id="74a82-110">说明</span><span class="sxs-lookup"><span data-stu-id="74a82-110">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="74a82-111">[**\<add>**](add-element-for-custom-2.md)对于 <xref:System.Configuration.NameValueSectionHandler> 和<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="74a82-111">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="74a82-112">添加自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="74a82-112">Adds custom application settings.</span></span> |
| <span data-ttu-id="74a82-113">[**\<remove>**](remove-element-for-custom-2.md)对于 <xref:System.Configuration.NameValueSectionHandler> 和<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="74a82-113">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="74a82-114">删除以前定义的设置。</span><span class="sxs-lookup"><span data-stu-id="74a82-114">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="74a82-115">[**\<clear>**](clear-element-for-custom-2.md)对于 <xref:System.Configuration.NameValueSectionHandler> 和<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="74a82-115">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="74a82-116">清除节中所有先前定义的设置。</span><span class="sxs-lookup"><span data-stu-id="74a82-116">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="74a82-117">注解</span><span class="sxs-lookup"><span data-stu-id="74a82-117">Remarks</span></span>

<span data-ttu-id="74a82-118">**\<sectionName>** 元素是由元素中的标记定义的自定义元素 **\<section>** **\<configSections>** 。</span><span class="sxs-lookup"><span data-stu-id="74a82-118">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="74a82-119">下表显示 ConfigurationSettings. GetConfig 方法为每个配置节处理程序返回的对象类型：</span><span class="sxs-lookup"><span data-stu-id="74a82-119">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="74a82-120">配置节处理程序</span><span class="sxs-lookup"><span data-stu-id="74a82-120">Configuration section handler</span></span>                        | <span data-ttu-id="74a82-121">返回类型</span><span class="sxs-lookup"><span data-stu-id="74a82-121">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="74a82-122">示例</span><span class="sxs-lookup"><span data-stu-id="74a82-122">Example</span></span>

<span data-ttu-id="74a82-123">下面的示例演示如何声明使用和类的节 <xref:System.Configuration.DictionarySectionHandler> <xref:System.Configuration.NameValueSectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="74a82-123">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="74a82-124">第一个自定义元素为 **\<dictionarySample>** ，其中包含由 <xref:System.Configuration.DictionarySectionHandler> 程序集中的类读取的设置 `System.dll` 。</span><span class="sxs-lookup"><span data-stu-id="74a82-124">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="74a82-125">第二个自定义元素为 **\<mySection>** ，其中包含由 <xref:System.Configuration.NameValueSectionHandler> 程序集中的类读取的设置 `System.dll` 。</span><span class="sxs-lookup"><span data-stu-id="74a82-125">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="74a82-126">配置文件</span><span class="sxs-lookup"><span data-stu-id="74a82-126">Configuration file</span></span>

<span data-ttu-id="74a82-127">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="74a82-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="74a82-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74a82-128">See also</span></span>

- [<span data-ttu-id="74a82-129">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="74a82-129">Configuration file schema for the .NET Framework</span></span>](index.md)
