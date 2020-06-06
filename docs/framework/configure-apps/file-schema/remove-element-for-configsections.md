---
title: <configSections> 的 <remove> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154525"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="644bd-102">\<configSections> 的 \<remove> 元素</span><span class="sxs-lookup"><span data-stu-id="644bd-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="644bd-103">删除预定义的节或节组。</span><span class="sxs-lookup"><span data-stu-id="644bd-103">Removes a predefined section or section group.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="644bd-104">语法</span><span class="sxs-lookup"><span data-stu-id="644bd-104">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="644bd-105">属性</span><span class="sxs-lookup"><span data-stu-id="644bd-105">Attribute</span></span>

|           | <span data-ttu-id="644bd-106">说明</span><span class="sxs-lookup"><span data-stu-id="644bd-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="644bd-107">**name**</span><span class="sxs-lookup"><span data-stu-id="644bd-107">**name**</span></span>  | <span data-ttu-id="644bd-108">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="644bd-108">Required attribute.</span></span><br><br><span data-ttu-id="644bd-109">指定要删除的节或节组的名称。</span><span class="sxs-lookup"><span data-stu-id="644bd-109">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="644bd-110">父元素</span><span class="sxs-lookup"><span data-stu-id="644bd-110">Parent element</span></span>

|     | <span data-ttu-id="644bd-111">说明</span><span class="sxs-lookup"><span data-stu-id="644bd-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="644bd-112">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="644bd-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="644bd-113">包含配置节和命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="644bd-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="644bd-114">子元素</span><span class="sxs-lookup"><span data-stu-id="644bd-114">Child elements</span></span>

<span data-ttu-id="644bd-115">无</span><span class="sxs-lookup"><span data-stu-id="644bd-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="644bd-116">备注</span><span class="sxs-lookup"><span data-stu-id="644bd-116">Remarks</span></span>

<span data-ttu-id="644bd-117">你可以使用 **\<remove>** 元素从你的应用程序中删除在配置文件层次结构中较高级别上定义的部分和节组。</span><span class="sxs-lookup"><span data-stu-id="644bd-117">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="644bd-118">示例</span><span class="sxs-lookup"><span data-stu-id="644bd-118">Example</span></span>

<span data-ttu-id="644bd-119">下面的示例演示如何使用 **\<remove>** 应用程序配置文件中的元素删除之前在计算机配置文件中定义的部分。</span><span class="sxs-lookup"><span data-stu-id="644bd-119">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="644bd-120">以下计算机配置文件代码声明了节 **\<sampleSection>** ：</span><span class="sxs-lookup"><span data-stu-id="644bd-120">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="644bd-121">以下应用程序配置文件代码将删除 **\<sampleSection>** 节。</span><span class="sxs-lookup"><span data-stu-id="644bd-121">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="644bd-122">删除后，应用程序无法检索中的设置 **\<sampleSection>** 。</span><span class="sxs-lookup"><span data-stu-id="644bd-122">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="644bd-123">配置文件</span><span class="sxs-lookup"><span data-stu-id="644bd-123">Configuration file</span></span>

<span data-ttu-id="644bd-124">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="644bd-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="644bd-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="644bd-125">See also</span></span>

- [<span data-ttu-id="644bd-126">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="644bd-126">Configuration file schema for the .NET Framework</span></span>](index.md)
