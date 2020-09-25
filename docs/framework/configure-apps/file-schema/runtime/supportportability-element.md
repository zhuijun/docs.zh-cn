---
title: <supportPortability> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 05ce6943b9456d4fd380ea8d6cf354d197b92f96
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183944"
---
# <a name="supportportability-element"></a><span data-ttu-id="e4144-102">\<supportPortability> 元素</span><span class="sxs-lookup"><span data-stu-id="e4144-102">\<supportPortability> Element</span></span>

<span data-ttu-id="e4144-103">通过禁用将程序集视为等效于应用程序可移植性用途的默认行为来指定应用程序可以在两种不同的 .NET Framework 实现中引用同一程序集。</span><span class="sxs-lookup"><span data-stu-id="e4144-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a><span data-ttu-id="e4144-104">语法</span><span class="sxs-lookup"><span data-stu-id="e4144-104">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4144-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e4144-105">Attributes and Elements</span></span>  

<span data-ttu-id="e4144-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4144-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4144-107">特性</span><span class="sxs-lookup"><span data-stu-id="e4144-107">Attributes</span></span>  
  
|<span data-ttu-id="e4144-108">属性</span><span class="sxs-lookup"><span data-stu-id="e4144-108">Attribute</span></span>|<span data-ttu-id="e4144-109">描述</span><span class="sxs-lookup"><span data-stu-id="e4144-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4144-110">PKT</span><span class="sxs-lookup"><span data-stu-id="e4144-110">PKT</span></span>|<span data-ttu-id="e4144-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="e4144-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4144-112">以字符串的形式指定受影响的程序集的公钥标记。</span><span class="sxs-lookup"><span data-stu-id="e4144-112">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="e4144-113">enabled</span><span class="sxs-lookup"><span data-stu-id="e4144-113">enabled</span></span>|<span data-ttu-id="e4144-114">可选特性。</span><span class="sxs-lookup"><span data-stu-id="e4144-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e4144-115">指定是否应启用指定 .NET Framework 程序集的实现之间的可移植性支持。</span><span class="sxs-lookup"><span data-stu-id="e4144-115">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e4144-116">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="e4144-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e4144-117">值</span><span class="sxs-lookup"><span data-stu-id="e4144-117">Value</span></span>|<span data-ttu-id="e4144-118">描述</span><span class="sxs-lookup"><span data-stu-id="e4144-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e4144-119">是</span><span class="sxs-lookup"><span data-stu-id="e4144-119">true</span></span>|<span data-ttu-id="e4144-120">支持指定 .NET Framework 程序集的实现之间的可移植性。</span><span class="sxs-lookup"><span data-stu-id="e4144-120">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="e4144-121">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="e4144-121">This is the default.</span></span>|  
|<span data-ttu-id="e4144-122">false</span><span class="sxs-lookup"><span data-stu-id="e4144-122">false</span></span>|<span data-ttu-id="e4144-123">禁用支持指定 .NET Framework 程序集的实现之间的可移植性。</span><span class="sxs-lookup"><span data-stu-id="e4144-123">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="e4144-124">这使应用程序可以引用指定程序集的多个实现。</span><span class="sxs-lookup"><span data-stu-id="e4144-124">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4144-125">子元素</span><span class="sxs-lookup"><span data-stu-id="e4144-125">Child Elements</span></span>  

<span data-ttu-id="e4144-126">无。</span><span class="sxs-lookup"><span data-stu-id="e4144-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4144-127">父元素</span><span class="sxs-lookup"><span data-stu-id="e4144-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e4144-128">元素</span><span class="sxs-lookup"><span data-stu-id="e4144-128">Element</span></span>|<span data-ttu-id="e4144-129">描述</span><span class="sxs-lookup"><span data-stu-id="e4144-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4144-130">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e4144-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e4144-131">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="e4144-131">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="e4144-132">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="e4144-132">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4144-133">备注</span><span class="sxs-lookup"><span data-stu-id="e4144-133">Remarks</span></span>  

<span data-ttu-id="e4144-134">从 .NET Framework 4 开始，将自动为可以使用两种 .NET Framework 实现的应用程序（例如，.NET Framework 实现或 Silverlight 实现的 .NET Framework）提供支持。</span><span class="sxs-lookup"><span data-stu-id="e4144-134">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="e4144-135">特定 .NET Framework 程序集的两个实现被视为等效于程序集联编程序。</span><span class="sxs-lookup"><span data-stu-id="e4144-135">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="e4144-136">在少数情况下，此应用程序可移植性功能会导致问题。</span><span class="sxs-lookup"><span data-stu-id="e4144-136">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="e4144-137">在这些情况下， `<supportPortability>` 可以使用元素来禁用该功能。</span><span class="sxs-lookup"><span data-stu-id="e4144-137">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="e4144-138">这种情况是必须同时引用特定引用程序集的 Silverlight 实现的 .NET Framework 实现和 .NET Framework 的程序集。</span><span class="sxs-lookup"><span data-stu-id="e4144-138">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="e4144-139">例如，在 Windows Presentation Foundation () WPF 中编写的 XAML 设计器可能需要引用 WPF 桌面实现、设计器的用户界面和 Silverlight 实现中包含的 WPF 子集。</span><span class="sxs-lookup"><span data-stu-id="e4144-139">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="e4144-140">默认情况下，单独引用会导致编译器错误，因为程序集绑定将这两个程序集视为等效。</span><span class="sxs-lookup"><span data-stu-id="e4144-140">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="e4144-141">此元素禁用默认行为，并允许编译成功。</span><span class="sxs-lookup"><span data-stu-id="e4144-141">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e4144-142">为了使编译器能够将信息传递到公共语言运行时的程序集绑定逻辑，必须使用 `/appconfig` 编译器选项来指定包含此元素的 app.config 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="e4144-142">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4144-143">示例</span><span class="sxs-lookup"><span data-stu-id="e4144-143">Example</span></span>  

<span data-ttu-id="e4144-144">下面的示例使应用程序能够同时引用在两个实现中都存在的任何 .NET Framework 程序集的 .NET Framework 实现和 Silverlight 实现 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="e4144-144">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="e4144-145">`/appconfig`必须使用编译器选项指定此 app.config 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="e4144-145">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4144-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="e4144-146">See also</span></span>

- [<span data-ttu-id="e4144-147">-appconfig（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="e4144-147">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="e4144-148">[.NET Framework 程序集统一概述](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e4144-148">[.NET Framework Assembly Unification Overview](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
