---
title: 配置节架构
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441656"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="8e26b-102">配置节架构</span><span class="sxs-lookup"><span data-stu-id="8e26b-102">Configuration sections schema</span></span>

<span data-ttu-id="8e26b-103">配置节架构包含用于在配置文件中定义自定义设置的元素。</span><span class="sxs-lookup"><span data-stu-id="8e26b-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="8e26b-104">有关配置文件和架构的一般信息，请参阅[.NET Framework 的配置文件架构](index.md)。</span><span class="sxs-lookup"><span data-stu-id="8e26b-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="8e26b-105">说明</span><span class="sxs-lookup"><span data-stu-id="8e26b-105">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="8e26b-106">包含配置节和命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="8e26b-106">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="8e26b-107">**\<section>** 对于 **\<configSections>** 和**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="8e26b-107">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="8e26b-108">包含配置节声明。</span><span class="sxs-lookup"><span data-stu-id="8e26b-108">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="8e26b-109">**\<sectionGroup>** 进行**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="8e26b-109">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="8e26b-110">定义配置节的命名空间。</span><span class="sxs-lookup"><span data-stu-id="8e26b-110">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="8e26b-111">未实现元素</span><span class="sxs-lookup"><span data-stu-id="8e26b-111">Unimplemented elements</span></span>

<span data-ttu-id="8e26b-112">以下元素不会有任何影响，因此不应使用：</span><span class="sxs-lookup"><span data-stu-id="8e26b-112">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
