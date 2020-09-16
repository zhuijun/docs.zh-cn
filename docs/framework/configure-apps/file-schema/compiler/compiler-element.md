---
title: <compiler> 元素
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 0abbe594754cbd70ec4732a1e7ef98e8e88bf167
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544747"
---
# <a name="compiler-element"></a><span data-ttu-id="64883-102">\<compiler> 元素</span><span class="sxs-lookup"><span data-stu-id="64883-102">\<compiler> Element</span></span>

<span data-ttu-id="64883-103">指定语言提供程序的编译器配置属性。</span><span class="sxs-lookup"><span data-stu-id="64883-103">Specifies the compiler configuration attributes for a language provider.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**

## <a name="syntax"></a><span data-ttu-id="64883-104">语法</span><span class="sxs-lookup"><span data-stu-id="64883-104">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64883-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="64883-105">Attributes and Elements</span></span>

<span data-ttu-id="64883-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="64883-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="64883-107">特性</span><span class="sxs-lookup"><span data-stu-id="64883-107">Attributes</span></span>

|<span data-ttu-id="64883-108">属性</span><span class="sxs-lookup"><span data-stu-id="64883-108">Attribute</span></span>|<span data-ttu-id="64883-109">描述</span><span class="sxs-lookup"><span data-stu-id="64883-109">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="64883-110">可选特性。</span><span class="sxs-lookup"><span data-stu-id="64883-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="64883-111">为编译指定其他特定于编译器的参数。</span><span class="sxs-lookup"><span data-stu-id="64883-111">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="64883-112">特性的值 `compilerOptions` 通常在编译器的编译器选项主题中列出。</span><span class="sxs-lookup"><span data-stu-id="64883-112">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="64883-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="64883-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="64883-114">提供语言提供程序的源文件所使用的文件扩展名的分号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="64883-114">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="64883-115">例如“.cs”。</span><span class="sxs-lookup"><span data-stu-id="64883-115">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="64883-116">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="64883-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="64883-117">提供语言提供程序支持的语言名称的分号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="64883-117">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="64883-118">例如“C#;cs;csharp”。</span><span class="sxs-lookup"><span data-stu-id="64883-118">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="64883-119">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="64883-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="64883-120">指定语言提供程序的类型名称，包括包含提供程序实现的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="64883-120">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="64883-121">类型名称必须满足 [指定完全限定的类型名称](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)中定义的要求。</span><span class="sxs-lookup"><span data-stu-id="64883-121">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="64883-122">可选特性。</span><span class="sxs-lookup"><span data-stu-id="64883-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="64883-123">指定默认编译器警告等级;确定语言提供程序将编译警告视为错误的级别。</span><span class="sxs-lookup"><span data-stu-id="64883-123">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="64883-124">子元素</span><span class="sxs-lookup"><span data-stu-id="64883-124">Child Elements</span></span>

|<span data-ttu-id="64883-125">元素</span><span class="sxs-lookup"><span data-stu-id="64883-125">Element</span></span>|<span data-ttu-id="64883-126">描述</span><span class="sxs-lookup"><span data-stu-id="64883-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64883-127">\<providerOption> 元素</span><span class="sxs-lookup"><span data-stu-id="64883-127">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="64883-128">指定语言提供程序的编译器版本特性。</span><span class="sxs-lookup"><span data-stu-id="64883-128">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="64883-129">父元素</span><span class="sxs-lookup"><span data-stu-id="64883-129">Parent Elements</span></span>

|<span data-ttu-id="64883-130">元素</span><span class="sxs-lookup"><span data-stu-id="64883-130">Element</span></span>|<span data-ttu-id="64883-131">描述</span><span class="sxs-lookup"><span data-stu-id="64883-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64883-132">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="64883-132">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="64883-133">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="64883-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="64883-134">\<system.codedom> 元素</span><span class="sxs-lookup"><span data-stu-id="64883-134">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="64883-135">指定可用语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="64883-135">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="64883-136">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="64883-136">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="64883-137">编译器配置元素的容器;包含零个或多个 `<compiler>` 元素。</span><span class="sxs-lookup"><span data-stu-id="64883-137">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="64883-138">备注</span><span class="sxs-lookup"><span data-stu-id="64883-138">Remarks</span></span>

<span data-ttu-id="64883-139">每个 `<compiler>` 元素指定特定语言提供程序的编译器配置特性。</span><span class="sxs-lookup"><span data-stu-id="64883-139">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="64883-140">提供程序为 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 特定语言扩展了类; `<compiler>` 元素定义了语言提供程序的编译器和代码生成器设置。</span><span class="sxs-lookup"><span data-stu-id="64883-140">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="64883-141">.NET Framework 在计算机配置文件 (Machine.config) 中定义初始编译器设置。</span><span class="sxs-lookup"><span data-stu-id="64883-141">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="64883-142">开发人员和编译器供应商可以添加新 <xref:System.CodeDom.Compiler.CodeDomProvider> 实现的配置设置。</span><span class="sxs-lookup"><span data-stu-id="64883-142">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="64883-143">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以编程方式枚举计算机上的语言提供程序和编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="64883-143">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="64883-144">应用程序或 Web 配置文件中的编译器元素可以补充或覆盖计算机配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="64883-144">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="64883-145">如果为相同的语言名称或相同的文件扩展名配置了多个提供程序实现，则最后一个匹配配置会重写该语言名称或文件扩展名的任何以前配置的提供程序。</span><span class="sxs-lookup"><span data-stu-id="64883-145">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="64883-146">配置文件</span><span class="sxs-lookup"><span data-stu-id="64883-146">Configuration File</span></span>

<span data-ttu-id="64883-147">此元素可在计算机配置文件和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="64883-147">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="64883-148">示例</span><span class="sxs-lookup"><span data-stu-id="64883-148">Example</span></span>

<span data-ttu-id="64883-149">下面的示例演示了一个典型的编译器配置元素：</span><span class="sxs-lookup"><span data-stu-id="64883-149">The following example illustrates a typical compiler configuration element:</span></span>

```xml
<configuration>
  <system.codedom>
    <compilers>
      <!-- zero or more compiler elements -->
      <compiler
        language="c#;cs;csharp"
        extension=".cs"
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"
        compilerOptions="/optimize"
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="64883-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="64883-150">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="64883-151">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="64883-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="64883-152">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="64883-152">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="64883-153">指定完全限定的类型名称</span><span class="sxs-lookup"><span data-stu-id="64883-153">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="64883-154">[compilation 的 compilers 的 compiler 元素（ASP.NET 设置架构）](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64883-154">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
