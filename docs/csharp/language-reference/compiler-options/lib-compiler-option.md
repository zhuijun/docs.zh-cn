---
description: -lib（C# 编译器选项）
title: -lib（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: e53c54dc446d9fea87a9b7a336a38ffaa31704e9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125444"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="2e17d-103">-lib（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="2e17d-103">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="2e17d-104">-lib 选项指定通过 [-reference（C# 编译器选项）](./reference-compiler-option.md)选项引用的程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="2e17d-104">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e17d-105">语法</span><span class="sxs-lookup"><span data-stu-id="2e17d-105">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e17d-106">自变量</span><span class="sxs-lookup"><span data-stu-id="2e17d-106">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="2e17d-107">在当前工作目录（调用编译器的目录）或公共语言运行时的系统目录中未找到引用的程序集时，编译器将在其中进行查找的目录。</span><span class="sxs-lookup"><span data-stu-id="2e17d-107">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="2e17d-108">要在其中搜索程序集引用的一个或多个附加目录。</span><span class="sxs-lookup"><span data-stu-id="2e17d-108">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="2e17d-109">用逗号分隔每个附加目录的名称，中间不要有空格。</span><span class="sxs-lookup"><span data-stu-id="2e17d-109">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e17d-110">备注</span><span class="sxs-lookup"><span data-stu-id="2e17d-110">Remarks</span></span>  
 <span data-ttu-id="2e17d-111">编译器按以下顺序搜索未完全限定的程序集引用：</span><span class="sxs-lookup"><span data-stu-id="2e17d-111">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="2e17d-112">当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="2e17d-112">Current working directory.</span></span> <span data-ttu-id="2e17d-113">该目录为从其调用编译器的目录。</span><span class="sxs-lookup"><span data-stu-id="2e17d-113">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="2e17d-114">公共语言运行时系统目录。</span><span class="sxs-lookup"><span data-stu-id="2e17d-114">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="2e17d-115">由 -lib 指定的目录。</span><span class="sxs-lookup"><span data-stu-id="2e17d-115">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="2e17d-116">由 LIB 环境变量指定的目录。</span><span class="sxs-lookup"><span data-stu-id="2e17d-116">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="2e17d-117">使用 -reference 指定程序集引用。</span><span class="sxs-lookup"><span data-stu-id="2e17d-117">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="2e17d-118">-lib 是累加的；每一次指定的值都追加到以前的值中。</span><span class="sxs-lookup"><span data-stu-id="2e17d-118">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="2e17d-119">另一种使用 -lib 的方法是，将任何所需的程序集复制到工作目录中；这样可以仅将程序集名称传递给 -reference 。</span><span class="sxs-lookup"><span data-stu-id="2e17d-119">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="2e17d-120">然后可以从工作目录中删除这些程序集。</span><span class="sxs-lookup"><span data-stu-id="2e17d-120">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="2e17d-121">由于程序集清单中未指定依赖程序集的路径，因此应用程序可以在目标计算机上启动，然后查找并使用全局程序集缓存中的程序集。</span><span class="sxs-lookup"><span data-stu-id="2e17d-121">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="2e17d-122">编译器可以引用程序集并不表示公共语言运行时可以在运行时找到并加载程序集。</span><span class="sxs-lookup"><span data-stu-id="2e17d-122">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="2e17d-123">有关运行时如何搜索引用的程序集的详细信息，请参阅[运行时如何定位程序集](../../../framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="2e17d-123">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2e17d-124">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="2e17d-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2e17d-125">打开项目的“属性页”  对话框。</span><span class="sxs-lookup"><span data-stu-id="2e17d-125">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="2e17d-126">单击“引用路径”\*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="2e17d-126">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="2e17d-127">修改列表框的内容。</span><span class="sxs-lookup"><span data-stu-id="2e17d-127">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="2e17d-128">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>。</span><span class="sxs-lookup"><span data-stu-id="2e17d-128">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e17d-129">示例</span><span class="sxs-lookup"><span data-stu-id="2e17d-129">Example</span></span>  
 <span data-ttu-id="2e17d-130">编译 t2.cs 以创建 .exe 文件。</span><span class="sxs-lookup"><span data-stu-id="2e17d-130">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="2e17d-131">编译器将在工作目录和 C 驱动器的根目录中查找程序集引用。</span><span class="sxs-lookup"><span data-stu-id="2e17d-131">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e17d-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e17d-132">See also</span></span>

- [<span data-ttu-id="2e17d-133">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="2e17d-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2e17d-134">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="2e17d-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
