---
title: <add>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215441"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="e1209-102">\<add>NameValueSectionHandler 和 DictionarySectionHandler 的元素</span><span class="sxs-lookup"><span data-stu-id="e1209-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="e1209-103">添加自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="e1209-103">Adds custom application settings.</span></span> <span data-ttu-id="e1209-104">每个 **\<add>** 标记包含一个键/值对。</span><span class="sxs-lookup"><span data-stu-id="e1209-104">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="e1209-105">语法</span><span class="sxs-lookup"><span data-stu-id="e1209-105">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="e1209-106">特性</span><span class="sxs-lookup"><span data-stu-id="e1209-106">Attributes</span></span>

| <span data-ttu-id="e1209-107">属性</span><span class="sxs-lookup"><span data-stu-id="e1209-107">Attribute</span></span> | <span data-ttu-id="e1209-108">说明</span><span class="sxs-lookup"><span data-stu-id="e1209-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e1209-109">**键**</span><span class="sxs-lookup"><span data-stu-id="e1209-109">**key**</span></span>   | <span data-ttu-id="e1209-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="e1209-110">Required attribute.</span></span><br><br><span data-ttu-id="e1209-111">指定设置的名称。</span><span class="sxs-lookup"><span data-stu-id="e1209-111">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="e1209-112">**value**</span><span class="sxs-lookup"><span data-stu-id="e1209-112">**value**</span></span> | <span data-ttu-id="e1209-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="e1209-113">Required attribute.</span></span><br><br><span data-ttu-id="e1209-114">指定设置的值。</span><span class="sxs-lookup"><span data-stu-id="e1209-114">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e1209-115">父元素</span><span class="sxs-lookup"><span data-stu-id="e1209-115">Parent element</span></span>

| <span data-ttu-id="e1209-116">元素</span><span class="sxs-lookup"><span data-stu-id="e1209-116">Element</span></span> | <span data-ttu-id="e1209-117">描述</span><span class="sxs-lookup"><span data-stu-id="e1209-117">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="e1209-118">**\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="e1209-118">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="e1209-119">定义使用和类的自定义配置节的设置 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="e1209-119">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e1209-120">子元素</span><span class="sxs-lookup"><span data-stu-id="e1209-120">Child elements</span></span>

<span data-ttu-id="e1209-121">无</span><span class="sxs-lookup"><span data-stu-id="e1209-121">None</span></span>

## <a name="example"></a><span data-ttu-id="e1209-122">示例</span><span class="sxs-lookup"><span data-stu-id="e1209-122">Example</span></span>

<span data-ttu-id="e1209-123">下面的示例演示如何定义自定义配置节，并使用 **\<add>** 元素将设置放入部分：</span><span class="sxs-lookup"><span data-stu-id="e1209-123">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="e1209-124">配置文件</span><span class="sxs-lookup"><span data-stu-id="e1209-124">Configuration file</span></span>

<span data-ttu-id="e1209-125">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="e1209-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1209-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1209-126">See also</span></span>

- [<span data-ttu-id="e1209-127">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="e1209-127">Configuration file schema for the .NET Framework</span></span>](index.md)
