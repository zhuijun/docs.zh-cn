---
title: <configuration> 的 <configSections> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155344"
---
# <a name="configsections-element-for-configuration"></a>\<configuration> 的 \<configSections> 元素

包含配置节和命名空间声明。

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**

## <a name="attributes"></a>特性

无

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | 公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。 |

## <a name="child-elements"></a>子元素

|     | 说明 |
| --- | ----------- |
| [**\<section>**](section-element.md) | 包含配置节声明。 |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | 定义配置节的命名空间。 |
| [**\<remove>**](remove-element-for-configsections.md) | 删除预定义的节或节组。 |
| [**\<clear>**](clear-element-for-configsections.md) | 清除所有之前定义的部分和节组。 |

## <a name="remarks"></a>注解

如果此元素在配置文件中，则它必须是元素的第一个子元素 **\<configuration>** 。

## <a name="example"></a>示例

下面的示例演示如何定义配置节并定义该部分的设置：

```xml
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

## <a name="configuration-file"></a>配置文件

此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*

## <a name="see-also"></a>另请参阅

- [.NET Framework 的配置文件架构](index.md)
