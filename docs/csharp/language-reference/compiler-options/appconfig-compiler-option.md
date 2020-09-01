---
description: -appconfig（C# 编译器选项）
title: -appconfig（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 287d41105199057add1dad78d480b083adb745b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126107"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="7f944-103">-appconfig（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="7f944-103">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="7f944-104">-appconfig 编译器选项让 C# 应用程序能够在程序集绑定时将程序集的应用程序配置 (app.config) 文件的位置指定为公共语言运行时 (CLR)。</span><span class="sxs-lookup"><span data-stu-id="7f944-104">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f944-105">语法</span><span class="sxs-lookup"><span data-stu-id="7f944-105">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f944-106">自变量</span><span class="sxs-lookup"><span data-stu-id="7f944-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="7f944-107">必需。</span><span class="sxs-lookup"><span data-stu-id="7f944-107">Required.</span></span> <span data-ttu-id="7f944-108">包含程序集绑定设置的应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="7f944-108">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f944-109">备注</span><span class="sxs-lookup"><span data-stu-id="7f944-109">Remarks</span></span>  
 <span data-ttu-id="7f944-110">-appconfig 的一种用途是处理高级情形；在该情形中，程序集必须同时引用特定引用程序集的 .NET Framework 版本和 .NET Framework for Silverlight 版本。</span><span class="sxs-lookup"><span data-stu-id="7f944-110">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="7f944-111">例如，在 Windows Presentation Foundation (WPF) 中编写的 XAML 设计器可能需要为设计器用户界面引用 WPF 桌面以及随附于 Silverlight 的 WPF 子集。</span><span class="sxs-lookup"><span data-stu-id="7f944-111">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="7f944-112">同一设计器程序集必须访问这两个程序集。</span><span class="sxs-lookup"><span data-stu-id="7f944-112">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="7f944-113">默认情况下，单独引用会导致编译器错误，因为程序集绑定将这两个程序集视为等效。</span><span class="sxs-lookup"><span data-stu-id="7f944-113">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="7f944-114">通过使用 -appconfig 编译器选项，可通过使用 `<supportPortability>` 标记指定某个 app.config 文件的位置，该文件会禁用默认行为，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="7f944-114">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="7f944-115">编译器将文件的位置传递给 CLR 的程序集绑定逻辑。</span><span class="sxs-lookup"><span data-stu-id="7f944-115">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f944-116">如果使用 Microsoft 生成引擎 (MSBuild) 生成应用程序，则可以通过将属性标记添加到 .csproj 文件来设置 -appconfig 编译器选项。</span><span class="sxs-lookup"><span data-stu-id="7f944-116">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="7f944-117">若要使用已在项目中设置的 app.config 文件，请将属性标记 `<UseAppConfigForCompiler>` 添加到 .csproj 文件，并将其值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="7f944-117">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="7f944-118">若要指定不同的 app.config 文件，请添加属性标记 `<AppConfigForCompiler>` 并将其值设置为该文件的位置。</span><span class="sxs-lookup"><span data-stu-id="7f944-118">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f944-119">示例</span><span class="sxs-lookup"><span data-stu-id="7f944-119">Example</span></span>  
 <span data-ttu-id="7f944-120">以下示例展示一个 app.config 文件，通过使用该文件，应用程序能够同时引用任何 .NET Framework 程序集（同时存在于后述两个实现中）的 .NET Framework 实现和 .NET Framework for Silverlight 实现。</span><span class="sxs-lookup"><span data-stu-id="7f944-120">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="7f944-121">-appconfig 编译器选项指定此 app.config 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="7f944-121">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f944-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f944-122">See also</span></span>

- [<span data-ttu-id="7f944-123">\<supportPortability> 元素</span><span class="sxs-lookup"><span data-stu-id="7f944-123">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="7f944-124">按字母顺序列出的 C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="7f944-124">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
