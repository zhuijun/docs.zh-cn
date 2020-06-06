---
title: <codeBase> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: 475b7df55ed509157c1da0aeb8f979de238c72b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70971887"
---
# <a name="codebase-element"></a><span data-ttu-id="f5810-102">\<codeBase> 元素</span><span class="sxs-lookup"><span data-stu-id="f5810-102">\<codeBase> Element</span></span>

<span data-ttu-id="f5810-103">指定公共语言运行时可在何处找到程序集。</span><span class="sxs-lookup"><span data-stu-id="f5810-103">Specifies where the common language runtime can find an assembly.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**

## <a name="syntax"></a><span data-ttu-id="f5810-104">语法</span><span class="sxs-lookup"><span data-stu-id="f5810-104">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5810-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f5810-105">Attributes and Elements</span></span>

<span data-ttu-id="f5810-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f5810-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5810-107">特性</span><span class="sxs-lookup"><span data-stu-id="f5810-107">Attributes</span></span>

|<span data-ttu-id="f5810-108">属性</span><span class="sxs-lookup"><span data-stu-id="f5810-108">Attribute</span></span>|<span data-ttu-id="f5810-109">说明</span><span class="sxs-lookup"><span data-stu-id="f5810-109">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="f5810-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="f5810-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="f5810-111">指定运行时可在其中找到程序集的指定版本的 URL。</span><span class="sxs-lookup"><span data-stu-id="f5810-111">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="f5810-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="f5810-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="f5810-113">指定基本代码所应用的程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="f5810-113">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="f5810-114">程序集版本号的格式为 "主要版本. 次要版本. 内部版本.*修订*版本"。</span><span class="sxs-lookup"><span data-stu-id="f5810-114">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="f5810-115">version 特性</span><span class="sxs-lookup"><span data-stu-id="f5810-115">version Attribute</span></span>

|<span data-ttu-id="f5810-116">值</span><span class="sxs-lookup"><span data-stu-id="f5810-116">Value</span></span>|<span data-ttu-id="f5810-117">说明</span><span class="sxs-lookup"><span data-stu-id="f5810-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="f5810-118">版本号的每个部分的有效值为0至65535。</span><span class="sxs-lookup"><span data-stu-id="f5810-118">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="f5810-119">不适用。</span><span class="sxs-lookup"><span data-stu-id="f5810-119">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f5810-120">子元素</span><span class="sxs-lookup"><span data-stu-id="f5810-120">Child Elements</span></span>

<span data-ttu-id="f5810-121">无。</span><span class="sxs-lookup"><span data-stu-id="f5810-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5810-122">父元素</span><span class="sxs-lookup"><span data-stu-id="f5810-122">Parent Elements</span></span>

|<span data-ttu-id="f5810-123">元素</span><span class="sxs-lookup"><span data-stu-id="f5810-123">Element</span></span>|<span data-ttu-id="f5810-124">描述</span><span class="sxs-lookup"><span data-stu-id="f5810-124">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="f5810-125">定义用于编译自定义资源文件的生成提供程序的集合。</span><span class="sxs-lookup"><span data-stu-id="f5810-125">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="f5810-126">您可以拥有任意数量的生成提供程序。</span><span class="sxs-lookup"><span data-stu-id="f5810-126">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="f5810-127">配置 ASP.NET 使用的所有编译设置。</span><span class="sxs-lookup"><span data-stu-id="f5810-127">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="f5810-128">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="f5810-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="f5810-129">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="f5810-129">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5810-130">注解</span><span class="sxs-lookup"><span data-stu-id="f5810-130">Remarks</span></span>

<span data-ttu-id="f5810-131">为了使运行时 **\<codeBase>** 在计算机配置文件或发布服务器策略文件中使用该设置，该文件还必须重定向程序集版本。</span><span class="sxs-lookup"><span data-stu-id="f5810-131">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="f5810-132">应用程序配置文件可以具有基本代码设置，而不会重定向程序集版本。</span><span class="sxs-lookup"><span data-stu-id="f5810-132">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="f5810-133">确定要使用的程序集版本后，运行时将从确定版本的文件应用基本代码设置。</span><span class="sxs-lookup"><span data-stu-id="f5810-133">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="f5810-134">如果未指定基本代码，则运行时以常规方式探测程序集。</span><span class="sxs-lookup"><span data-stu-id="f5810-134">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="f5810-135">如果程序集具有强名称，则基本代码设置可以是本地 intranet 或 Internet 上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="f5810-135">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="f5810-136">如果程序集是私有程序集，则 codebase 设置必须是相对于应用程序目录的路径。</span><span class="sxs-lookup"><span data-stu-id="f5810-136">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="f5810-137">对于没有强名称的程序集，将忽略版本，加载程序将使用内部的第一个外观 \<codebase> \<dependentAssembly> 。</span><span class="sxs-lookup"><span data-stu-id="f5810-137">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="f5810-138">如果应用程序配置文件中存在重定向绑定到另一个程序集的条目，则即使程序集版本与绑定请求不匹配，重定向也将优先。</span><span class="sxs-lookup"><span data-stu-id="f5810-138">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="f5810-139">示例</span><span class="sxs-lookup"><span data-stu-id="f5810-139">Example</span></span>

<span data-ttu-id="f5810-140">下面的示例演示如何指定运行时在何处可以找到程序集。</span><span class="sxs-lookup"><span data-stu-id="f5810-140">The following example shows how to specify where the runtime can find an assembly.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f5810-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5810-141">See also</span></span>

- [<span data-ttu-id="f5810-142">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="f5810-142">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="f5810-143">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="f5810-143">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="f5810-144">指定程序集的位置</span><span class="sxs-lookup"><span data-stu-id="f5810-144">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="f5810-145">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="f5810-145">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
