---
title: <configSections> 的 <sectionGroup> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215264"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="2918f-102">\<configSections> 的 \<sectionGroup> 元素</span><span class="sxs-lookup"><span data-stu-id="2918f-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="2918f-103">定义配置节的命名空间。</span><span class="sxs-lookup"><span data-stu-id="2918f-103">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="2918f-104">语法</span><span class="sxs-lookup"><span data-stu-id="2918f-104">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="2918f-105">属性</span><span class="sxs-lookup"><span data-stu-id="2918f-105">Attribute</span></span>

|           | <span data-ttu-id="2918f-106">说明</span><span class="sxs-lookup"><span data-stu-id="2918f-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="2918f-107">**name**</span><span class="sxs-lookup"><span data-stu-id="2918f-107">**name**</span></span>  | <span data-ttu-id="2918f-108">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="2918f-108">Required attribute.</span></span><br><br><span data-ttu-id="2918f-109">指定正在定义的节组的名称。</span><span class="sxs-lookup"><span data-stu-id="2918f-109">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="2918f-110">父元素</span><span class="sxs-lookup"><span data-stu-id="2918f-110">Parent element</span></span>

|     | <span data-ttu-id="2918f-111">说明</span><span class="sxs-lookup"><span data-stu-id="2918f-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2918f-112">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="2918f-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="2918f-113">包含配置节和命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="2918f-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2918f-114">子元素</span><span class="sxs-lookup"><span data-stu-id="2918f-114">Child elements</span></span>

|     | <span data-ttu-id="2918f-115">说明</span><span class="sxs-lookup"><span data-stu-id="2918f-115">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="2918f-116">包含配置节声明。</span><span class="sxs-lookup"><span data-stu-id="2918f-116">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2918f-117">注解</span><span class="sxs-lookup"><span data-stu-id="2918f-117">Remarks</span></span>

<span data-ttu-id="2918f-118">声明节组将为配置节创建容器标记，并确保与其他人定义的配置节之间没有命名冲突。</span><span class="sxs-lookup"><span data-stu-id="2918f-118">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="2918f-119">可以在彼此 **\<sectionGroup>** 之间嵌套元素。</span><span class="sxs-lookup"><span data-stu-id="2918f-119">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="2918f-120">示例</span><span class="sxs-lookup"><span data-stu-id="2918f-120">Example</span></span>

<span data-ttu-id="2918f-121">下面的示例演示如何声明一个节组，并在节组中声明部分：</span><span class="sxs-lookup"><span data-stu-id="2918f-121">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="2918f-122">配置文件</span><span class="sxs-lookup"><span data-stu-id="2918f-122">Configuration file</span></span>

<span data-ttu-id="2918f-123">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="2918f-123">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2918f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2918f-124">See also</span></span>

- [<span data-ttu-id="2918f-125">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="2918f-125">Configuration file schema for the .NET Framework</span></span>](index.md)
