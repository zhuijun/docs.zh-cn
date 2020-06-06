---
title: <compilers> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155409"
---
# <a name="compilers-element"></a><span data-ttu-id="b2f62-102">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="b2f62-102">\<compilers> Element</span></span>
<span data-ttu-id="b2f62-103">编译器配置元素的容器;包含零个或多个 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="b2f62-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="b2f62-104">语法</span><span class="sxs-lookup"><span data-stu-id="b2f62-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2f62-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b2f62-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b2f62-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b2f62-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2f62-107">特性</span><span class="sxs-lookup"><span data-stu-id="b2f62-107">Attributes</span></span>  
 <span data-ttu-id="b2f62-108">无。</span><span class="sxs-lookup"><span data-stu-id="b2f62-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2f62-109">子元素</span><span class="sxs-lookup"><span data-stu-id="b2f62-109">Child Elements</span></span>  
  
|<span data-ttu-id="b2f62-110">元素</span><span class="sxs-lookup"><span data-stu-id="b2f62-110">Element</span></span>|<span data-ttu-id="b2f62-111">说明</span><span class="sxs-lookup"><span data-stu-id="b2f62-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2f62-112">\<compiler>Element</span><span class="sxs-lookup"><span data-stu-id="b2f62-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="b2f62-113">指定语言提供程序的编译器配置属性。</span><span class="sxs-lookup"><span data-stu-id="b2f62-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2f62-114">父元素</span><span class="sxs-lookup"><span data-stu-id="b2f62-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b2f62-115">元素</span><span class="sxs-lookup"><span data-stu-id="b2f62-115">Element</span></span>|<span data-ttu-id="b2f62-116">说明</span><span class="sxs-lookup"><span data-stu-id="b2f62-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2f62-117">\<configuration>Element</span><span class="sxs-lookup"><span data-stu-id="b2f62-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="b2f62-118">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="b2f62-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="b2f62-119">\<system.codedom>Element</span><span class="sxs-lookup"><span data-stu-id="b2f62-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="b2f62-120">指定可用语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="b2f62-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2f62-121">注解</span><span class="sxs-lookup"><span data-stu-id="b2f62-121">Remarks</span></span>  
 <span data-ttu-id="b2f62-122">[\<compilers>](compilers-element.md)元素包含计算机上的语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="b2f62-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="b2f62-123">每个 [\<compiler>](compiler-element.md) 元素指定特定语言提供程序的编译器配置特性。</span><span class="sxs-lookup"><span data-stu-id="b2f62-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="b2f62-124">.NET Framework 在计算机配置文件（machine.config）中定义初始编译器和语言提供程序设置。</span><span class="sxs-lookup"><span data-stu-id="b2f62-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="b2f62-125">开发人员和编译器供应商可以添加新 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 实现的配置设置。</span><span class="sxs-lookup"><span data-stu-id="b2f62-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="b2f62-126">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以编程方式枚举计算机上的语言提供程序和编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="b2f62-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b2f62-127">配置文件</span><span class="sxs-lookup"><span data-stu-id="b2f62-127">Configuration File</span></span>  
 <span data-ttu-id="b2f62-128">此元素可在计算机配置文件和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="b2f62-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2f62-129">示例</span><span class="sxs-lookup"><span data-stu-id="b2f62-129">Example</span></span>  
 <span data-ttu-id="b2f62-130">以下示例说明典型的编译器配置元素。</span><span class="sxs-lookup"><span data-stu-id="b2f62-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler
          language="c#;cs;csharp"
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2f62-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="b2f62-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="b2f62-132">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="b2f62-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b2f62-133">编译器和语言提供程序设置架构</span><span class="sxs-lookup"><span data-stu-id="b2f62-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b2f62-134">\<compiler>Element</span><span class="sxs-lookup"><span data-stu-id="b2f62-134">\<compiler> Element</span></span>](compiler-element.md)
