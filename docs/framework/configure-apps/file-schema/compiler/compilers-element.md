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
ms.openlocfilehash: 1aa096e185ae7f5957f173c03e221a31f30d5200
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172939"
---
# <a name="compilers-element"></a><span data-ttu-id="07613-102">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="07613-102">\<compilers> Element</span></span>

<span data-ttu-id="07613-103">编译器配置元素的容器;包含零个或多个 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="07613-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="07613-104">语法</span><span class="sxs-lookup"><span data-stu-id="07613-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07613-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="07613-105">Attributes and Elements</span></span>  

 <span data-ttu-id="07613-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="07613-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07613-107">特性</span><span class="sxs-lookup"><span data-stu-id="07613-107">Attributes</span></span>  

 <span data-ttu-id="07613-108">无。</span><span class="sxs-lookup"><span data-stu-id="07613-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="07613-109">子元素</span><span class="sxs-lookup"><span data-stu-id="07613-109">Child Elements</span></span>  
  
|<span data-ttu-id="07613-110">元素</span><span class="sxs-lookup"><span data-stu-id="07613-110">Element</span></span>|<span data-ttu-id="07613-111">描述</span><span class="sxs-lookup"><span data-stu-id="07613-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07613-112">\<compiler> 元素</span><span class="sxs-lookup"><span data-stu-id="07613-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="07613-113">指定语言提供程序的编译器配置属性。</span><span class="sxs-lookup"><span data-stu-id="07613-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07613-114">父元素</span><span class="sxs-lookup"><span data-stu-id="07613-114">Parent Elements</span></span>  
  
|<span data-ttu-id="07613-115">元素</span><span class="sxs-lookup"><span data-stu-id="07613-115">Element</span></span>|<span data-ttu-id="07613-116">描述</span><span class="sxs-lookup"><span data-stu-id="07613-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07613-117">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="07613-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="07613-118">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="07613-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="07613-119">\<system.codedom> 元素</span><span class="sxs-lookup"><span data-stu-id="07613-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="07613-120">指定可用语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="07613-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07613-121">备注</span><span class="sxs-lookup"><span data-stu-id="07613-121">Remarks</span></span>  

 <span data-ttu-id="07613-122">[\<compilers>](compilers-element.md)元素包含计算机上的语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="07613-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="07613-123">每个 [\<compiler>](compiler-element.md) 元素指定特定语言提供程序的编译器配置特性。</span><span class="sxs-lookup"><span data-stu-id="07613-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="07613-124">.NET Framework 在计算机配置文件中定义初始编译器和语言提供程序设置 ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="07613-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="07613-125">开发人员和编译器供应商可以添加新 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 实现的配置设置。</span><span class="sxs-lookup"><span data-stu-id="07613-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="07613-126">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以编程方式枚举计算机上的语言提供程序和编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="07613-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="07613-127">配置文件</span><span class="sxs-lookup"><span data-stu-id="07613-127">Configuration File</span></span>  

 <span data-ttu-id="07613-128">此元素可在计算机配置文件和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="07613-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07613-129">示例</span><span class="sxs-lookup"><span data-stu-id="07613-129">Example</span></span>  

 <span data-ttu-id="07613-130">以下示例说明典型的编译器配置元素。</span><span class="sxs-lookup"><span data-stu-id="07613-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07613-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="07613-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="07613-132">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="07613-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="07613-133">编译器和语言提供程序设置架构</span><span class="sxs-lookup"><span data-stu-id="07613-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="07613-134">\<compiler> 元素</span><span class="sxs-lookup"><span data-stu-id="07613-134">\<compiler> Element</span></span>](compiler-element.md)
