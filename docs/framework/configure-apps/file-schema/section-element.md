---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153720"
---
# <a name="section-element"></a><span data-ttu-id="c92e8-102">\<section> 元素</span><span class="sxs-lookup"><span data-stu-id="c92e8-102">\<section> element</span></span>

<span data-ttu-id="c92e8-103">包含配置节声明。</span><span class="sxs-lookup"><span data-stu-id="c92e8-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="c92e8-104">语法</span><span class="sxs-lookup"><span data-stu-id="c92e8-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="c92e8-105">必需属性</span><span class="sxs-lookup"><span data-stu-id="c92e8-105">Required attributes</span></span>

|           | <span data-ttu-id="c92e8-106">说明</span><span class="sxs-lookup"><span data-stu-id="c92e8-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c92e8-107">**name**</span><span class="sxs-lookup"><span data-stu-id="c92e8-107">**name**</span></span>  | <span data-ttu-id="c92e8-108">指定配置节的名称。</span><span class="sxs-lookup"><span data-stu-id="c92e8-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="c92e8-109">type</span><span class="sxs-lookup"><span data-stu-id="c92e8-109">**type**</span></span>  | <span data-ttu-id="c92e8-110">指定从配置文件读取节的配置节处理程序类的名称。</span><span class="sxs-lookup"><span data-stu-id="c92e8-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="c92e8-111">类型值具有语法 "完全限定的节-名称、简单程序集名称"。</span><span class="sxs-lookup"><span data-stu-id="c92e8-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="c92e8-112">简单程序集名称是没有 *.dll*文件扩展名的根文件名。</span><span class="sxs-lookup"><span data-stu-id="c92e8-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="c92e8-113">可选属性</span><span class="sxs-lookup"><span data-stu-id="c92e8-113">Optional attributes</span></span>

<span data-ttu-id="c92e8-114">以下属性仅适用于 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="c92e8-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="c92e8-115">对于其他应用程序类型，配置系统将忽略这些属性。</span><span class="sxs-lookup"><span data-stu-id="c92e8-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="c92e8-116">说明</span><span class="sxs-lookup"><span data-stu-id="c92e8-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="c92e8-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="c92e8-117">**allowDefinition**</span></span> | <span data-ttu-id="c92e8-118">指定可在其中使用节的配置文件。</span><span class="sxs-lookup"><span data-stu-id="c92e8-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="c92e8-119">使用以下值之一：</span><span class="sxs-lookup"><span data-stu-id="c92e8-119">Use one of the following values:</span></span><br><br><span data-ttu-id="c92e8-120">**无处不在**</span><span class="sxs-lookup"><span data-stu-id="c92e8-120">**Everywhere**</span></span><br><span data-ttu-id="c92e8-121">允许在任何配置文件中使用节。</span><span class="sxs-lookup"><span data-stu-id="c92e8-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="c92e8-122">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="c92e8-122">This is the default.</span></span><br><span data-ttu-id="c92e8-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="c92e8-123">**MachineOnly**</span></span><br><span data-ttu-id="c92e8-124">允许部分仅在计算机配置文件（*machine.config*）中使用。</span><span class="sxs-lookup"><span data-stu-id="c92e8-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="c92e8-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="c92e8-125">**MachineToApplication**</span></span><br><span data-ttu-id="c92e8-126">允许在计算机配置文件或应用程序配置文件中使用部分。</span><span class="sxs-lookup"><span data-stu-id="c92e8-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="c92e8-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="c92e8-127">**allowLocation**</span></span>   | <span data-ttu-id="c92e8-128">确定是否可以在元素中使用节 **\<location>** 。</span><span class="sxs-lookup"><span data-stu-id="c92e8-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="c92e8-129">使用以下值之一：</span><span class="sxs-lookup"><span data-stu-id="c92e8-129">Use one of the following values:</span></span><br><br><span data-ttu-id="c92e8-130">true</span><span class="sxs-lookup"><span data-stu-id="c92e8-130">**true**</span></span><br><span data-ttu-id="c92e8-131">允许在元素中使用节 **\<location>** 。</span><span class="sxs-lookup"><span data-stu-id="c92e8-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="c92e8-132">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="c92e8-132">This is the default.</span></span><br><span data-ttu-id="c92e8-133">**false**</span><span class="sxs-lookup"><span data-stu-id="c92e8-133">**false**</span></span><br><span data-ttu-id="c92e8-134">不允许在元素中使用节 **\<location>** 。</span><span class="sxs-lookup"><span data-stu-id="c92e8-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="c92e8-135">父元素</span><span class="sxs-lookup"><span data-stu-id="c92e8-135">Parent elements</span></span>

|     | <span data-ttu-id="c92e8-136">说明</span><span class="sxs-lookup"><span data-stu-id="c92e8-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c92e8-137">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="c92e8-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="c92e8-138">包含配置节和命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="c92e8-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="c92e8-139">**\<sectionGroup>** Element</span><span class="sxs-lookup"><span data-stu-id="c92e8-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c92e8-140">定义配置节的命名空间。</span><span class="sxs-lookup"><span data-stu-id="c92e8-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="c92e8-141">**\<section>** 元素是或中的子元素， **\<configSections>** **\<sectionGroup>** 而不是同时为两者。</span><span class="sxs-lookup"><span data-stu-id="c92e8-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="c92e8-142">子元素</span><span class="sxs-lookup"><span data-stu-id="c92e8-142">Child elements</span></span>

<span data-ttu-id="c92e8-143">无</span><span class="sxs-lookup"><span data-stu-id="c92e8-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="c92e8-144">备注</span><span class="sxs-lookup"><span data-stu-id="c92e8-144">Remarks</span></span>

<span data-ttu-id="c92e8-145">声明配置节本质上定义了配置文件的新元素。</span><span class="sxs-lookup"><span data-stu-id="c92e8-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="c92e8-146">新元素包含配置节处理程序（即实现接口的类）的设置 <xref:System.Configuration.IConfigurationSectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="c92e8-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="c92e8-147">你定义的节的特性和子元素取决于用于读取设置的部分处理程序。</span><span class="sxs-lookup"><span data-stu-id="c92e8-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="c92e8-148">通过在*machine.config*文件中声明配置节处理程序，你可以使用该计算机上任何应用程序配置文件中的配置节，除非**allowDefinition**属性指定了其他内容。</span><span class="sxs-lookup"><span data-stu-id="c92e8-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="c92e8-149">示例</span><span class="sxs-lookup"><span data-stu-id="c92e8-149">Example</span></span>

<span data-ttu-id="c92e8-150">下面的示例演示如何定义配置节并定义该部分的设置：</span><span class="sxs-lookup"><span data-stu-id="c92e8-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c92e8-151">配置文件</span><span class="sxs-lookup"><span data-stu-id="c92e8-151">Configuration file</span></span>

<span data-ttu-id="c92e8-152">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="c92e8-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c92e8-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c92e8-153">See also</span></span>

- [<span data-ttu-id="c92e8-154">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c92e8-154">Configuration file schema for the .NET Framework</span></span>](index.md)
