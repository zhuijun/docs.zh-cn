---
title: <configuration> 的 <assemblyBinding> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155474"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="da21b-102">\<configuration> 的 \<assemblyBinding> 元素</span><span class="sxs-lookup"><span data-stu-id="da21b-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="da21b-103">指定配置级的程序集绑定策略。</span><span class="sxs-lookup"><span data-stu-id="da21b-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="da21b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="da21b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="da21b-105">语法</span><span class="sxs-lookup"><span data-stu-id="da21b-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="da21b-106">属性</span><span class="sxs-lookup"><span data-stu-id="da21b-106">Attribute</span></span>

|           | <span data-ttu-id="da21b-107">说明</span><span class="sxs-lookup"><span data-stu-id="da21b-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="da21b-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="da21b-108">**xmlns**</span></span> | <span data-ttu-id="da21b-109">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="da21b-109">Required attribute.</span></span><br><br><span data-ttu-id="da21b-110">指定程序集绑定所需的 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="da21b-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="da21b-111">使用字符串“urn: 架构-microsoft-com:asm.v1”作为值。</span><span class="sxs-lookup"><span data-stu-id="da21b-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="da21b-112">父元素</span><span class="sxs-lookup"><span data-stu-id="da21b-112">Parent element</span></span>

|     | <span data-ttu-id="da21b-113">说明</span><span class="sxs-lookup"><span data-stu-id="da21b-113">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="da21b-114">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="da21b-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="da21b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="da21b-115">Child element</span></span>

|     | <span data-ttu-id="da21b-116">描述</span><span class="sxs-lookup"><span data-stu-id="da21b-116">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="da21b-117">指定要包含的配置文件。</span><span class="sxs-lookup"><span data-stu-id="da21b-117">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="da21b-118">注解</span><span class="sxs-lookup"><span data-stu-id="da21b-118">Remarks</span></span>

<span data-ttu-id="da21b-119">[**\<linkedConfiguration>**](linkedconfiguration-element.md)元素通过允许应用程序配置文件在众所周知的位置包含程序集配置文件，而不是复制程序集配置设置，从而简化了组件程序集的管理。</span><span class="sxs-lookup"><span data-stu-id="da21b-119">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="da21b-120">**\<linkedConfiguration>** 具有 Windows 并行清单的应用程序不支持该元素。</span><span class="sxs-lookup"><span data-stu-id="da21b-120">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="da21b-121">示例</span><span class="sxs-lookup"><span data-stu-id="da21b-121">Example</span></span>

<span data-ttu-id="da21b-122">下面的示例演示如何在本地硬盘上包含配置文件：</span><span class="sxs-lookup"><span data-stu-id="da21b-122">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="da21b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da21b-123">See also</span></span>

- [<span data-ttu-id="da21b-124">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="da21b-124">Configuration file schema for the .NET Framework</span></span>](index.md)
