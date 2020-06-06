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
# <a name="app-settings-schema"></a>应用设置架构

包含自定义应用程序设置，如文件路径、XML Web service URL 或应用程序的任何其他自定义配置信息。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| 元素 | 说明 |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | 包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 标记以控制应用程序设置。 具有可选的“file”**** 属性。 |
| [**\<add>**](add-element-for-appsettings.md) | 定义设置。 的子项 **\<appSettings>** 。 需要“key”**** 和“value”**** 属性。 |
| [**\<clear>**](clear-element-for-appsettings.md) | 清除所有设置。 的子项 **\<appSettings>** 。 不具有属性。 |
| [**\<remove>**](remove-element-for-appsettings.md) | 删除设置。 的子项 **\<appSettings>** 。 需要“key”**** 属性。 |

## <a name="appsettings-element"></a>\<appSettings> 元素

此元素包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 标记以控制应用程序设置。 它定义“file”**** 的一个可选属性。

## <a name="add-element"></a>\<add> 元素

将自定义应用程序设置作为名称/值对添加到应用程序设置集合。 它定义“key”**** 和“value”**** 的属性。

## <a name="clear-element"></a>\<clear> 元素

删除所有对继承的自定义应用程序设置的引用，并仅允许元素后面由元素添加的引用 **\<add>** **\<clear>** 。 未定义任何属性。

## <a name="remove-element"></a>\<remove> 元素

删除对应用程序设置集合中继承的自定义应用程序设置的引用。 定义“key”**** 的属性。

## <a name="example"></a>示例

下面的示例演示外部应用程序设置文件 (custom.config**)，该文件定义自定义应用程序设置：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

下面的示例演示使用外部设置文件中的设置并自行设置应用程序设置的应用程序配置文件：

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>另请参阅

- [应用程序设置概述](../../../winforms/advanced/application-settings-overview.md)
- [应用程序设置体系结构](../../../winforms/advanced/application-settings-architecture.md)
