---
description: -resource（C# 编译器选项）
title: -resource（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 963004820f56272b4f1b1d92ccc4d0a60493a4a0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128694"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="25a1f-103">-resource（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="25a1f-103">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="25a1f-104">将指定资源嵌入输出文件。</span><span class="sxs-lookup"><span data-stu-id="25a1f-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a1f-105">语法</span><span class="sxs-lookup"><span data-stu-id="25a1f-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="25a1f-106">自变量</span><span class="sxs-lookup"><span data-stu-id="25a1f-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="25a1f-107">要嵌入到输出文件的 .NET Framework 资源文件。</span><span class="sxs-lookup"><span data-stu-id="25a1f-107">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="25a1f-108">`identifier`（可选）</span><span class="sxs-lookup"><span data-stu-id="25a1f-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="25a1f-109">资源的逻辑名称；用于加载资源的名称。</span><span class="sxs-lookup"><span data-stu-id="25a1f-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="25a1f-110">默认值是文件名的名称。</span><span class="sxs-lookup"><span data-stu-id="25a1f-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="25a1f-111">`accessibility-modifier`（可选）</span><span class="sxs-lookup"><span data-stu-id="25a1f-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="25a1f-112">资源的可访问性：public 或 private。</span><span class="sxs-lookup"><span data-stu-id="25a1f-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="25a1f-113">默认值为 public。</span><span class="sxs-lookup"><span data-stu-id="25a1f-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25a1f-114">备注</span><span class="sxs-lookup"><span data-stu-id="25a1f-114">Remarks</span></span>  
 <span data-ttu-id="25a1f-115">使用 [linkresource](./linkresource-compiler-option.md) 将资源链接至程序集，不向输出文件添加资源文件。</span><span class="sxs-lookup"><span data-stu-id="25a1f-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="25a1f-116">默认情况下，如果使用 C# 编译器创建资源，则这些资源在程序集中是公有的。</span><span class="sxs-lookup"><span data-stu-id="25a1f-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="25a1f-117">若要使资源变为私有，请将 `private` 指定为可访问性修饰符。</span><span class="sxs-lookup"><span data-stu-id="25a1f-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="25a1f-118">不允许使用 `public` 或 `private` 以外的任何其他可访问性。</span><span class="sxs-lookup"><span data-stu-id="25a1f-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="25a1f-119">例如，如果 `filename` 是由 [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) 创建的或在开发环境中创建的 .NET Framework 资源文件，则可使用 <xref:System.Resources> 命名空间中的成员来访问它。</span><span class="sxs-lookup"><span data-stu-id="25a1f-119">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="25a1f-120">有关详细信息，请参阅 <xref:System.Resources.ResourceManager?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="25a1f-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25a1f-121">对于所有其他资源，请使用 <xref:System.Reflection.Assembly> 类中的 `GetManifestResource` 方法在运行时访问资源。</span><span class="sxs-lookup"><span data-stu-id="25a1f-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="25a1f-122">/res 是 /resource 的缩写形式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25a1f-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="25a1f-123">输出文件中资源的顺序由命令行所指定的顺序决定。</span><span class="sxs-lookup"><span data-stu-id="25a1f-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="25a1f-124">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="25a1f-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="25a1f-125">向项目添加资源文件。</span><span class="sxs-lookup"><span data-stu-id="25a1f-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="25a1f-126">选择要嵌入解决方案资源管理器的文件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25a1f-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="25a1f-127">在“属性”窗口中为文件选择“生成操作”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25a1f-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="25a1f-128">将“生成操作”设置为“嵌入的资源”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25a1f-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="25a1f-129">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.FileProperties2.BuildAction%2A>。</span><span class="sxs-lookup"><span data-stu-id="25a1f-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25a1f-130">示例</span><span class="sxs-lookup"><span data-stu-id="25a1f-130">Example</span></span>  
 <span data-ttu-id="25a1f-131">编译 `in.cs` 并附加资源文件 `rf.resource`：</span><span class="sxs-lookup"><span data-stu-id="25a1f-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="25a1f-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25a1f-132">See also</span></span>

- [<span data-ttu-id="25a1f-133">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="25a1f-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="25a1f-134">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="25a1f-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
