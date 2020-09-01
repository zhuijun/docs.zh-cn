---
description: -define（C# 编译器选项）
title: -define（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 3b7a1c6e92d2c60ce289f29044774c3aa42ca84f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125873"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="56fbf-103">-define（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="56fbf-103">-define (C# Compiler Options)</span></span>
<span data-ttu-id="56fbf-104">-define 选项将 `name` 定义为程序中所有源代码文件的符号\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56fbf-104">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fbf-105">语法</span><span class="sxs-lookup"><span data-stu-id="56fbf-105">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="56fbf-106">自变量</span><span class="sxs-lookup"><span data-stu-id="56fbf-106">Arguments</span></span>  
 <span data-ttu-id="56fbf-107">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="56fbf-107">`name`, `name2`</span></span>  
 <span data-ttu-id="56fbf-108">一个或多个要定义的符号的名称。</span><span class="sxs-lookup"><span data-stu-id="56fbf-108">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56fbf-109">备注</span><span class="sxs-lookup"><span data-stu-id="56fbf-109">Remarks</span></span>  
 <span data-ttu-id="56fbf-110">-define 选项具有与使用 [#define](../preprocessor-directives/preprocessor-define.md) 预处理器指令相同的效果，但编译器选项对项目中的所有文件都有效\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56fbf-110">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="56fbf-111">符号在源文件中保持已定义状态，直到源文件中的 [#undef](../preprocessor-directives/preprocessor-undef.md) 指令删除该定义。</span><span class="sxs-lookup"><span data-stu-id="56fbf-111">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="56fbf-112">使用 -define 选项时，一个文件中的 `#undef` 指令不影响项目中其他的源代码文件。</span><span class="sxs-lookup"><span data-stu-id="56fbf-112">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="56fbf-113">可以将由此选项创建的符号同 [#if](../preprocessor-directives/preprocessor-if.md)、[#else](../preprocessor-directives/preprocessor-else.md)、[#elif](../preprocessor-directives/preprocessor-elif.md) 和 [#endif](../preprocessor-directives/preprocessor-endif.md) 一起使用，对源文件进行条件编译。</span><span class="sxs-lookup"><span data-stu-id="56fbf-113">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="56fbf-114">-d 是 -define 的缩写形式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56fbf-114">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="56fbf-115">通过使用分号或逗号分隔符号名称，可用 -define 定义多个符号\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56fbf-115">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="56fbf-116">例如：</span><span class="sxs-lookup"><span data-stu-id="56fbf-116">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="56fbf-117">C# 编译器本身不定义源代码中使用的符号或宏；所有符号定义必须都是用户定义的。</span><span class="sxs-lookup"><span data-stu-id="56fbf-117">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56fbf-118">同 C++ 等语言一样，C# `#define` 不允许为符号赋值。</span><span class="sxs-lookup"><span data-stu-id="56fbf-118">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="56fbf-119">例如，`#define` 不能用于创建宏或定义常数。</span><span class="sxs-lookup"><span data-stu-id="56fbf-119">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="56fbf-120">如果需要定义一个常数，请使用 `enum` 变量。</span><span class="sxs-lookup"><span data-stu-id="56fbf-120">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="56fbf-121">若要创建 C++ 风格的宏，请考虑泛型等替代项。</span><span class="sxs-lookup"><span data-stu-id="56fbf-121">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="56fbf-122">由于宏非常容易出错，所以 C# 不允许使用宏，但提供了更安全的替代项。</span><span class="sxs-lookup"><span data-stu-id="56fbf-122">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="56fbf-123">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="56fbf-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="56fbf-124">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="56fbf-124">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="56fbf-125">在“生成”选项卡上，键入要在“条件编译符号”框中定义的符号\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56fbf-125">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="56fbf-126">例如，如果使用以下代码示例，只需在文本框中键入 `xx`。</span><span class="sxs-lookup"><span data-stu-id="56fbf-126">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="56fbf-127">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>。</span><span class="sxs-lookup"><span data-stu-id="56fbf-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56fbf-128">示例</span><span class="sxs-lookup"><span data-stu-id="56fbf-128">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="56fbf-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56fbf-129">See also</span></span>

- [<span data-ttu-id="56fbf-130">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="56fbf-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="56fbf-131">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="56fbf-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
