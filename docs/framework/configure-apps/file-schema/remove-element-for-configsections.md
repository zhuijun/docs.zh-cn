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
# <a name="remove-element-for-configsections"></a>\<configSections> 的 \<remove> 元素

删除预定义的节或节组。

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>语法

```xml
<remove name="section name or section group name" />
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

你可以使用 **\<remove>** 元素从你的应用程序中删除在配置文件层次结构中较高级别上定义的部分和节组。

## <a name="example"></a>示例

下面的示例演示如何使用 **\<remove>** 应用程序配置文件中的元素删除之前在计算机配置文件中定义的部分。

以下计算机配置文件代码声明了节 **\<sampleSection>** ：

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

以下应用程序配置文件代码将删除 **\<sampleSection>** 节。 删除后，应用程序无法检索中的设置 **\<sampleSection>** 。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>配置文件

此元素可用于应用程序配置文件、计算机配置文件（*machine.config*）和不在应用程序目录级别的*web.config 文件。*

## <a name="see-also"></a>另请参阅

- [.NET Framework 的配置文件架构](index.md)
