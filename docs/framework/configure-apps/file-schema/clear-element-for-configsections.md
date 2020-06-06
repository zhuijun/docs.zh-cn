---
title: <configSections> 的 <clear> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155422"
---
# <a name="clear-element-for-configsections"></a>\<configSections> 的 \<clear> 元素

清除所有之前定义的部分和节组。

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>语法

```xml
<clear/>
```

## <a name="attribute"></a>属性

|           | 说明 |
| --------- | ----------- |
| **name**  | 必需的特性。<br><br>指定要删除的节或节组的名称。 |

## <a name="parent-element"></a>父元素

|     | 说明 |
| --- | ----------- |
| [**\<configSections>** Element](configsections-element-for-configuration.md) | 包含配置节和命名空间声明。 |

## <a name="child-elements"></a>子元素

无

## <a name="remarks"></a>备注

**\<clear>** 元素从你的应用程序中删除之前在当前配置文件中或在配置文件层次结构中的更高级别定义的所有节和节组。

## <a name="example"></a>示例

此示例定义了计算机配置文件和应用程序配置文件，并演示了如何使用 **\<clear>** 应用程序配置文件中的元素清除之前在计算机配置文件中定义的部分。

以下计算机配置文件代码声明了两个部分，即在 **\<sampleSection>** **\<anotherSampleSection>** 应用程序配置文件之前读取的部分：

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

以下应用程序配置文件代码将清除以前声明的所有部分。 应用程序不能使用或检索在计算机配置文件中声明的任一部分中的设置。 但是，它可以使用中的设置， **\<anotherSection>** 因为它位于 **\<clear>** 元素之后。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>配置文件

此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*

## <a name="see-also"></a>另请参阅

- [.NET Framework 的配置文件架构](index.md)
