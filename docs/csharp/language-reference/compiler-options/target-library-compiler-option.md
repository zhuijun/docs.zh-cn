---
description: -target:library（C# 编译器选项）
title: -target:library（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0f5b1e1bec8fd601bf111e1c2c64adf22d0a064e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193720"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="77284-103">-target:library（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="77284-103">-target:library (C# Compiler Options)</span></span>

<span data-ttu-id="77284-104">-target:library 选项导致编译器创建动态链接库 (DLL) 而不是可执行文件 (EXE)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77284-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77284-105">语法</span><span class="sxs-lookup"><span data-stu-id="77284-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="77284-106">备注</span><span class="sxs-lookup"><span data-stu-id="77284-106">Remarks</span></span>  

 <span data-ttu-id="77284-107">将创建具有 .dll 扩展名的 DLL。</span><span class="sxs-lookup"><span data-stu-id="77284-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="77284-108">除非使用 [-out](./out-compiler-option.md) 选项指定，否则输出文件的名称采用第一个输入文件的名称。</span><span class="sxs-lookup"><span data-stu-id="77284-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="77284-109">在命令行中进行指定时，-out 或 -target:module 选项上所有文件都用于创建 .dll 文件\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77284-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="77284-110">生成 .dll 文件时，不需要 [ Main ](../../programming-guide/main-and-command-args/index.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="77284-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="77284-111">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="77284-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="77284-112">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="77284-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="77284-113">单击“应用程序”属性页。</span><span class="sxs-lookup"><span data-stu-id="77284-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="77284-114">修改“输出类型”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="77284-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="77284-115">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="77284-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77284-116">示例</span><span class="sxs-lookup"><span data-stu-id="77284-116">Example</span></span>  

 <span data-ttu-id="77284-117">通过创建 `in.dll` 编译 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="77284-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="77284-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77284-118">See also</span></span>

- [<span data-ttu-id="77284-119">-target（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="77284-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="77284-120">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="77284-120">C# Compiler Options</span></span>](./index.md)
