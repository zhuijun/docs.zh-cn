---
title: <remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214760"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="ef854-102">\<remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素</span><span class="sxs-lookup"><span data-stu-id="ef854-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="ef854-103">删除以前定义的设置。</span><span class="sxs-lookup"><span data-stu-id="ef854-103">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="ef854-104">语法</span><span class="sxs-lookup"><span data-stu-id="ef854-104">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="ef854-105">属性</span><span class="sxs-lookup"><span data-stu-id="ef854-105">Attribute</span></span>

|           | <span data-ttu-id="ef854-106">说明</span><span class="sxs-lookup"><span data-stu-id="ef854-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ef854-107">**键**</span><span class="sxs-lookup"><span data-stu-id="ef854-107">**key**</span></span>   | <span data-ttu-id="ef854-108">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="ef854-108">Required attribute.</span></span><br><br><span data-ttu-id="ef854-109">指定要删除的设置的名称。</span><span class="sxs-lookup"><span data-stu-id="ef854-109">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ef854-110">父元素</span><span class="sxs-lookup"><span data-stu-id="ef854-110">Parent element</span></span>

| <span data-ttu-id="ef854-111">元素</span><span class="sxs-lookup"><span data-stu-id="ef854-111">Element</span></span> | <span data-ttu-id="ef854-112">描述</span><span class="sxs-lookup"><span data-stu-id="ef854-112">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="ef854-113">**\<sectionName>** Element</span><span class="sxs-lookup"><span data-stu-id="ef854-113">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="ef854-114">定义使用和类的自定义配置节的设置 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="ef854-114">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ef854-115">子元素</span><span class="sxs-lookup"><span data-stu-id="ef854-115">Child elements</span></span>

<span data-ttu-id="ef854-116">无</span><span class="sxs-lookup"><span data-stu-id="ef854-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ef854-117">备注</span><span class="sxs-lookup"><span data-stu-id="ef854-117">Remarks</span></span>

<span data-ttu-id="ef854-118">你可以使用 **\<remove>** 元素从你的应用程序中删除在配置文件层次结构中较高级别上定义的设置。</span><span class="sxs-lookup"><span data-stu-id="ef854-118">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="ef854-119">示例</span><span class="sxs-lookup"><span data-stu-id="ef854-119">Example</span></span>

<span data-ttu-id="ef854-120">下面的示例演示如何使用 **\<remove>** 应用程序配置文件中的元素删除以前在计算机配置文件中定义的设置。</span><span class="sxs-lookup"><span data-stu-id="ef854-120">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="ef854-121">以下计算机配置文件代码声明节， **\<mySection>** 并向其中添加两个 `key1` 设置 `key2` ：</span><span class="sxs-lookup"><span data-stu-id="ef854-121">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="ef854-122">以下应用程序配置文件代码将删除以下 `key2` 设置 **\<mySection>** ：</span><span class="sxs-lookup"><span data-stu-id="ef854-122">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ef854-123">配置文件</span><span class="sxs-lookup"><span data-stu-id="ef854-123">Configuration file</span></span>

<span data-ttu-id="ef854-124">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="ef854-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef854-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef854-125">See also</span></span>

- [<span data-ttu-id="ef854-126">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="ef854-126">Configuration file schema for the .NET Framework</span></span>](index.md)
