---
description: -target:module（C# 编译器选项）
title: -target:module（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d8691e5e4477dbbe989344469b44382d5e0e7c8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193603"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="67969-103">-target:module（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="67969-103">-target:module (C# Compiler Options)</span></span>

<span data-ttu-id="67969-104">此选项会导致编译器不生成程序集清单。</span><span class="sxs-lookup"><span data-stu-id="67969-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67969-105">语法</span><span class="sxs-lookup"><span data-stu-id="67969-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="67969-106">备注</span><span class="sxs-lookup"><span data-stu-id="67969-106">Remarks</span></span>  

 <span data-ttu-id="67969-107">默认情况下，使用此选项编译时所创建的输出文件具有扩展名 .netmodule。</span><span class="sxs-lookup"><span data-stu-id="67969-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="67969-108">.NET 运行时无法加载没有程序集清单的文件。</span><span class="sxs-lookup"><span data-stu-id="67969-108">A file that does not have an assembly manifest cannot be loaded by the .NET runtime.</span></span> <span data-ttu-id="67969-109">但是，此类文件可以通过 [-addmodule](./addmodule-compiler-option.md) 合并到程序集的程序集清单中。</span><span class="sxs-lookup"><span data-stu-id="67969-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="67969-110">如果在一次编译中创建了多个模块，某个模块中的[内部](../keywords/internal.md)类型将适用于编译中的其他模块。</span><span class="sxs-lookup"><span data-stu-id="67969-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="67969-111">如果一个模块中的代码引用另一模块中的 `internal` 类型，则两个模块必须通过 -addmodule 合并到一个程序集清单中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="67969-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="67969-112">Visual Studio 开发环境中不支持创建模块。</span><span class="sxs-lookup"><span data-stu-id="67969-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="67969-113">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="67969-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67969-114">示例</span><span class="sxs-lookup"><span data-stu-id="67969-114">Example</span></span>  

 <span data-ttu-id="67969-115">通过创建 `in.netmodule` 编译 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="67969-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="67969-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67969-116">See also</span></span>

- [<span data-ttu-id="67969-117">-target（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="67969-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="67969-118">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="67969-118">C# Compiler Options</span></span>](./index.md)
