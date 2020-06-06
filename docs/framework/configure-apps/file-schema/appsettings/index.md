---
title: 应用设置架构
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215429"
---
# <a name="app-settings-schema"></a><span data-ttu-id="f2f30-102">应用设置架构</span><span class="sxs-lookup"><span data-stu-id="f2f30-102">App Settings schema</span></span>

<span data-ttu-id="f2f30-103">包含自定义应用程序设置，如文件路径、XML Web service URL 或应用程序的任何其他自定义配置信息。</span><span class="sxs-lookup"><span data-stu-id="f2f30-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="f2f30-104">元素</span><span class="sxs-lookup"><span data-stu-id="f2f30-104">Element</span></span> | <span data-ttu-id="f2f30-105">说明</span><span class="sxs-lookup"><span data-stu-id="f2f30-105">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="f2f30-106">包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 标记以控制应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="f2f30-106">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f2f30-107">具有可选的“file”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-107">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="f2f30-108">定义设置。</span><span class="sxs-lookup"><span data-stu-id="f2f30-108">Defines a setting.</span></span> <span data-ttu-id="f2f30-109">的子项 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="f2f30-109">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f2f30-110">需要“key”\*\*\*\* 和“value”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-110">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="f2f30-111">清除所有设置。</span><span class="sxs-lookup"><span data-stu-id="f2f30-111">Clears all settings.</span></span> <span data-ttu-id="f2f30-112">的子项 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="f2f30-112">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f2f30-113">不具有属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-113">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="f2f30-114">删除设置。</span><span class="sxs-lookup"><span data-stu-id="f2f30-114">Removes a setting.</span></span> <span data-ttu-id="f2f30-115">的子项 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="f2f30-115">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f2f30-116">需要“key”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-116">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="f2f30-117">\<appSettings> 元素</span><span class="sxs-lookup"><span data-stu-id="f2f30-117">\<appSettings> element</span></span>

<span data-ttu-id="f2f30-118">此元素包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 标记以控制应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="f2f30-118">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f2f30-119">它定义“file”\*\*\*\* 的一个可选属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-119">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="f2f30-120">\<add> 元素</span><span class="sxs-lookup"><span data-stu-id="f2f30-120">\<add> element</span></span>

<span data-ttu-id="f2f30-121">将自定义应用程序设置作为名称/值对添加到应用程序设置集合。</span><span class="sxs-lookup"><span data-stu-id="f2f30-121">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="f2f30-122">它定义“key”\*\*\*\* 和“value”\*\*\*\* 的属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-122">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="f2f30-123">\<clear> 元素</span><span class="sxs-lookup"><span data-stu-id="f2f30-123">\<clear> element</span></span>

<span data-ttu-id="f2f30-124">删除所有对继承的自定义应用程序设置的引用，并仅允许元素后面由元素添加的引用 **\<add>** **\<clear>** 。</span><span class="sxs-lookup"><span data-stu-id="f2f30-124">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="f2f30-125">未定义任何属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-125">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="f2f30-126">\<remove> 元素</span><span class="sxs-lookup"><span data-stu-id="f2f30-126">\<remove> element</span></span>

<span data-ttu-id="f2f30-127">删除对应用程序设置集合中继承的自定义应用程序设置的引用。</span><span class="sxs-lookup"><span data-stu-id="f2f30-127">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="f2f30-128">定义“key”\*\*\*\* 的属性。</span><span class="sxs-lookup"><span data-stu-id="f2f30-128">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="f2f30-129">示例</span><span class="sxs-lookup"><span data-stu-id="f2f30-129">Example</span></span>

<span data-ttu-id="f2f30-130">下面的示例演示外部应用程序设置文件 (custom.config\*\*)，该文件定义自定义应用程序设置：</span><span class="sxs-lookup"><span data-stu-id="f2f30-130">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="f2f30-131">下面的示例演示使用外部设置文件中的设置并自行设置应用程序设置的应用程序配置文件：</span><span class="sxs-lookup"><span data-stu-id="f2f30-131">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f2f30-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2f30-132">See also</span></span>

- [<span data-ttu-id="f2f30-133">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="f2f30-133">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="f2f30-134">应用程序设置体系结构</span><span class="sxs-lookup"><span data-stu-id="f2f30-134">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
