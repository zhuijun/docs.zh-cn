---
title: <system.codedom> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155383"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="85b21-102">\<system.codedom> 元素</span><span class="sxs-lookup"><span data-stu-id="85b21-102">\<system.codedom> Element</span></span>
<span data-ttu-id="85b21-103">指定可用语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="85b21-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="85b21-104">语法</span><span class="sxs-lookup"><span data-stu-id="85b21-104">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85b21-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="85b21-105">Attributes and Elements</span></span>  
 <span data-ttu-id="85b21-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="85b21-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85b21-107">特性</span><span class="sxs-lookup"><span data-stu-id="85b21-107">Attributes</span></span>  
 <span data-ttu-id="85b21-108">无。</span><span class="sxs-lookup"><span data-stu-id="85b21-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85b21-109">子元素</span><span class="sxs-lookup"><span data-stu-id="85b21-109">Child Elements</span></span>  
  
|<span data-ttu-id="85b21-110">元素</span><span class="sxs-lookup"><span data-stu-id="85b21-110">Element</span></span>|<span data-ttu-id="85b21-111">说明</span><span class="sxs-lookup"><span data-stu-id="85b21-111">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="85b21-112">编译器配置元素的容器;包含零个或多个 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="85b21-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85b21-113">父元素</span><span class="sxs-lookup"><span data-stu-id="85b21-113">Parent Elements</span></span>  
  
|<span data-ttu-id="85b21-114">元素</span><span class="sxs-lookup"><span data-stu-id="85b21-114">Element</span></span>|<span data-ttu-id="85b21-115">说明</span><span class="sxs-lookup"><span data-stu-id="85b21-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="85b21-116">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="85b21-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85b21-117">注解</span><span class="sxs-lookup"><span data-stu-id="85b21-117">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="85b21-118">.NET Framework 版本2。0</span><span class="sxs-lookup"><span data-stu-id="85b21-118">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="85b21-119">[\<system.codedom>](system-codedom-element.md)元素包含计算机上安装的语言提供程序的编译器配置设置，以及随 .NET Framework 安装的默认提供程序，例如 <xref:Microsoft.CSharp.CSharpCodeProvider> 和 <xref:Microsoft.VisualBasic.VBCodeProvider> 。</span><span class="sxs-lookup"><span data-stu-id="85b21-119">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="85b21-120">[\<compilers>](compilers-element.md)元素包含零个或多个 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="85b21-120">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="85b21-121">每个 [\<compiler>](compiler-element.md) 元素指定特定语言提供程序的编译器配置特性。</span><span class="sxs-lookup"><span data-stu-id="85b21-121">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="85b21-122">开发人员和编译器供应商可将配置设置添加到计算机配置文件（Machine.config）中以实现新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 实现。</span><span class="sxs-lookup"><span data-stu-id="85b21-122">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="85b21-123">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法以编程方式枚举计算机上编译器配置设置标识的默认语言提供程序和语言提供程序。</span><span class="sxs-lookup"><span data-stu-id="85b21-123">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85b21-124">在 .NET Framework 版本1.0 和1.1 中，在元素中标识 .NET Framework 提供的默认语言提供程序 [\<compilers>](compilers-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="85b21-124">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="85b21-125">在 .NET Framework 版本2.0 中，不会在元素中标识默认语言提供程序 [\<compilers>](compilers-element.md) ，但可以使用方法对其进行枚举 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> 。</span><span class="sxs-lookup"><span data-stu-id="85b21-125">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="85b21-126">.NET Framework 版本1.0 和1。1</span><span class="sxs-lookup"><span data-stu-id="85b21-126">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="85b21-127">[\<system.codedom>](system-codedom-element.md)元素包含计算机上的语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="85b21-127">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="85b21-128">[\<compilers>](compilers-element.md)元素包含零个或多个 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="85b21-128">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="85b21-129">每个 [\<compiler>](compiler-element.md) 元素指定特定语言提供程序的编译器配置特性。</span><span class="sxs-lookup"><span data-stu-id="85b21-129">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="85b21-130">.NET Framework 在计算机配置文件 (Machine.config) 中定义初始编译器设置。</span><span class="sxs-lookup"><span data-stu-id="85b21-130">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="85b21-131">开发人员和编译器供应商可以添加新 <xref:System.CodeDom.Compiler.CodeDomProvider> 实现的配置设置。</span><span class="sxs-lookup"><span data-stu-id="85b21-131">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="85b21-132">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以编程方式枚举计算机上的语言提供程序和编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="85b21-132">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="85b21-133">配置文件</span><span class="sxs-lookup"><span data-stu-id="85b21-133">Configuration File</span></span>  
 <span data-ttu-id="85b21-134">此元素可在计算机配置文件和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="85b21-134">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85b21-135">示例</span><span class="sxs-lookup"><span data-stu-id="85b21-135">Example</span></span>  
 <span data-ttu-id="85b21-136">下面的示例演示了一个典型的编译器配置。</span><span class="sxs-lookup"><span data-stu-id="85b21-136">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85b21-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="85b21-137">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="85b21-138">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="85b21-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="85b21-139">编译器和语言提供程序设置架构</span><span class="sxs-lookup"><span data-stu-id="85b21-139">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="85b21-140">\<compiler>Element</span><span class="sxs-lookup"><span data-stu-id="85b21-140">\<compiler> Element</span></span>](compiler-element.md)
