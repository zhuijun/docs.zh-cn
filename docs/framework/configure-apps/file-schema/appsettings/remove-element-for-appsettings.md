---
title: <appSettings> 的 <remove> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215495"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="0ebfd-102">\<appSettings> 的 \<remove> 元素</span><span class="sxs-lookup"><span data-stu-id="0ebfd-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="0ebfd-103">删除自定义应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="0ebfd-103">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="0ebfd-104">语法</span><span class="sxs-lookup"><span data-stu-id="0ebfd-104">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="0ebfd-105">属性</span><span class="sxs-lookup"><span data-stu-id="0ebfd-105">Attribute</span></span>

|         | <span data-ttu-id="0ebfd-106">说明</span><span class="sxs-lookup"><span data-stu-id="0ebfd-106">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="0ebfd-107">**键**</span><span class="sxs-lookup"><span data-stu-id="0ebfd-107">**key**</span></span> | <span data-ttu-id="0ebfd-108">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="0ebfd-108">Required attribute.</span></span><br><br><span data-ttu-id="0ebfd-109">指定要删除的密钥的名称。</span><span class="sxs-lookup"><span data-stu-id="0ebfd-109">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="0ebfd-110">父元素</span><span class="sxs-lookup"><span data-stu-id="0ebfd-110">Parent element</span></span>

|     | <span data-ttu-id="0ebfd-111">说明</span><span class="sxs-lookup"><span data-stu-id="0ebfd-111">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="0ebfd-112">包含自定义应用程序设置，如文件路径、XML Web service URL 或应用程序的任何其他自定义配置信息。</span><span class="sxs-lookup"><span data-stu-id="0ebfd-112">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0ebfd-113">子元素</span><span class="sxs-lookup"><span data-stu-id="0ebfd-113">Child elements</span></span>

<span data-ttu-id="0ebfd-114">无</span><span class="sxs-lookup"><span data-stu-id="0ebfd-114">None</span></span>

## <a name="example"></a><span data-ttu-id="0ebfd-115">示例</span><span class="sxs-lookup"><span data-stu-id="0ebfd-115">Example</span></span>

<span data-ttu-id="0ebfd-116">下面的示例演示如何删除的自定义配置设置 `ApplicationName` ：</span><span class="sxs-lookup"><span data-stu-id="0ebfd-116">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="0ebfd-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ebfd-117">See also</span></span>

- [<span data-ttu-id="0ebfd-118">.NET Framework 的配置文件架构</span><span class="sxs-lookup"><span data-stu-id="0ebfd-118">Configuration file schema for the .NET Framework</span></span>](../index.md)
