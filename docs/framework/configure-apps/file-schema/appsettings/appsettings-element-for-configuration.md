---
title: <configuration> 的 <appSettings> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155526"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="5f24d-102">\<configuration> 的 \<appSettings> 元素</span><span class="sxs-lookup"><span data-stu-id="5f24d-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="5f24d-103">包含自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="5f24d-103">Contains custom application settings.</span></span> <span data-ttu-id="5f24d-104">这是 .NET Framework 提供的预定义的配置节。</span><span class="sxs-lookup"><span data-stu-id="5f24d-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="5f24d-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="5f24d-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5f24d-106">语法</span><span class="sxs-lookup"><span data-stu-id="5f24d-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="5f24d-107">属性</span><span class="sxs-lookup"><span data-stu-id="5f24d-107">Attribute</span></span>

|           | <span data-ttu-id="5f24d-108">说明</span><span class="sxs-lookup"><span data-stu-id="5f24d-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="5f24d-109">**文件**</span><span class="sxs-lookup"><span data-stu-id="5f24d-109">**file**</span></span>  | <span data-ttu-id="5f24d-110">可选特性。</span><span class="sxs-lookup"><span data-stu-id="5f24d-110">Optional attribute.</span></span><br><br><span data-ttu-id="5f24d-111">指定包含自定义应用程序配置设置的外部文件的相对路径。</span><span class="sxs-lookup"><span data-stu-id="5f24d-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="5f24d-112">指定的文件包含在、和元素中指定的相同类型的设置， **\<add>** **\<remove>** **\<clear>** 并使用与这些元素相同的键/值对格式。</span><span class="sxs-lookup"><span data-stu-id="5f24d-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="5f24d-113">指定的路径相对于主配置文件。</span><span class="sxs-lookup"><span data-stu-id="5f24d-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="5f24d-114">对于 Windows 窗体应用程序，这是二进制文件夹（如 */bin/debug*），而不是应用程序配置文件的位置。</span><span class="sxs-lookup"><span data-stu-id="5f24d-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="5f24d-115">对于 Web 窗体应用程序，该路径相对于在其中找到*web.config*文件的应用程序根目录。</span><span class="sxs-lookup"><span data-stu-id="5f24d-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="5f24d-116">如果找不到指定的文件，则运行时将忽略该特性。</span><span class="sxs-lookup"><span data-stu-id="5f24d-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="5f24d-117">父元素</span><span class="sxs-lookup"><span data-stu-id="5f24d-117">Parent element</span></span>

|     | <span data-ttu-id="5f24d-118">说明</span><span class="sxs-lookup"><span data-stu-id="5f24d-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5f24d-119">**\<configuration>** Element</span><span class="sxs-lookup"><span data-stu-id="5f24d-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="5f24d-120">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="5f24d-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5f24d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="5f24d-121">Child elements</span></span>

|     | <span data-ttu-id="5f24d-122">说明</span><span class="sxs-lookup"><span data-stu-id="5f24d-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="5f24d-123">添加自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="5f24d-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="5f24d-124">清除以前定义的所有应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="5f24d-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="5f24d-125">删除以前定义的应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="5f24d-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5f24d-126">注解</span><span class="sxs-lookup"><span data-stu-id="5f24d-126">Remarks</span></span>

<span data-ttu-id="5f24d-127">**\<appSettings>** 元素存储自定义应用程序配置信息，例如数据库连接字符串、文件路径、XML Web service url，或应用程序的任何其他自定义配置信息。</span><span class="sxs-lookup"><span data-stu-id="5f24d-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="5f24d-128">**\<appSettings>** 使用类在代码中访问元素中指定的键/值对 <xref:System.Configuration.ConfigurationSettings> 。</span><span class="sxs-lookup"><span data-stu-id="5f24d-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="5f24d-129">可以**file**在 web.config **\<appSettings>** 和应用程序配置文件的元素中*Web.config*使用 file 特性。</span><span class="sxs-lookup"><span data-stu-id="5f24d-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="5f24d-130">此特性指定提供其他设置或重写在元素中指定的设置的配置文件 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="5f24d-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="5f24d-131">**文件**属性可用于源代码管理团队开发方案，例如当用户想要重写应用程序配置文件中指定的项目设置时。</span><span class="sxs-lookup"><span data-stu-id="5f24d-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="5f24d-132">**文件**属性指定的配置文件的根节点必须 **\<appSettings>** 是而不是 **\<configuration>** 。</span><span class="sxs-lookup"><span data-stu-id="5f24d-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="5f24d-133">示例</span><span class="sxs-lookup"><span data-stu-id="5f24d-133">Example</span></span>

<span data-ttu-id="5f24d-134">下面的示例演示外部应用程序设置文件 (custom.config\*\*)，该文件定义自定义应用程序设置：</span><span class="sxs-lookup"><span data-stu-id="5f24d-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="5f24d-135">下面的示例演示使用外部设置文件中的设置并自行设置应用程序设置的应用程序配置文件：</span><span class="sxs-lookup"><span data-stu-id="5f24d-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="5f24d-136">配置文件</span><span class="sxs-lookup"><span data-stu-id="5f24d-136">Configuration file</span></span>

<span data-ttu-id="5f24d-137">此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*</span><span class="sxs-lookup"><span data-stu-id="5f24d-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f24d-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f24d-138">See also</span></span>

- [<span data-ttu-id="5f24d-139">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="5f24d-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
