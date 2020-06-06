---
title: <providerOption> 元素
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155396"
---
# <a name="provideroption-element"></a>\<providerOption> 元素
指定语言提供程序的编译器版本特性。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a>语法  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|`name`|必需的特性。<br /><br /> 指定选项的名称;例如 "CompilerVersion"。|  
|`value`|必需的特性。<br /><br /> 指定选项的值;例如，"v 3.5"。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<configuration>Element](../configuration-element.md)|公共语言运行库和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|[\<system.codedom>Element](system-codedom-element.md)|指定可用语言提供程序的编译器配置设置。|  
|[\<compilers>Element](compilers-element.md)|编译器配置元素的容器;包含零个或多个 `<compiler>` 元素。|  
|[\<compiler>Element](compiler-element.md)|指定语言提供程序的编译器配置属性。|  
  
## <a name="remarks"></a>注解  
 在 .NET Framework 版本3.5 中，代码文档对象模型（CodeDOM）代码提供程序可以使用元素支持特定于提供程序的选项 `<providerOption>` 。  
  
 3.5 .NET Framework 包括更新的 .NET Framework 2.0 程序集，并提供包含新类型的3.5 版本的新程序集。 Microsoft c # 和 Visual Basic 代码提供程序包含在 .NET Framework 2.0 程序集中，但已更新为支持版本3.5 编译器。 默认情况下，更新的代码提供程序为版本2.0 编译器生成代码。 您可以使用 `<providerOption>` 元素将目标编译器版本更改为3.5。 为此，请将属性指定为 "CompilerVersion" `name` ，并为属性指定 "v 3.5" `value` 。 必须在版本号前面加上小写 "v"。  
  
 可以通过将 `<providerOption>` 元素添加到 .NET Framework 2.0 machine.config 或根 web.config 文件来使版本规范成为全局版本。 如果在 machine.config 文件中将默认编译器版本更新为3.5，则可使用 `<providerOption>` 应用程序配置文件中的元素，将其更改为每个应用程序的2.0。  
  
 CodeDOM 代码提供程序实现者可以通过提供采用类型为的参数的构造函数来处理自定义选项 `providerOptions` <xref:System.Collections.Generic.IDictionary%602> 。  
  
## <a name="example"></a>示例  
 下面的示例演示如何指定应使用 c # 代码提供程序的3.5 版。  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [配置文件架构](../index.md)
- [\<compilers>Element](compilers-element.md)
- [指定完全限定的类型名称](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [compilation 的 compilers 的 compiler 元素（ASP.NET 设置架构）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
