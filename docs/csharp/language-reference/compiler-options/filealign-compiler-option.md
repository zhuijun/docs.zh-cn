---
description: -filealign（C# 编译器选项）
title: -filealign（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: 4b61217a3d6812ea3ab036f82d49bba05c20629e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173238"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="bdd4f-103">-filealign（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="bdd4f-103">-filealign (C# Compiler Options)</span></span>

<span data-ttu-id="bdd4f-104">-filealign 选项用于指定输出文件中各节的大小\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-104">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd4f-105">语法</span><span class="sxs-lookup"><span data-stu-id="bdd4f-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="bdd4f-106">自变量</span><span class="sxs-lookup"><span data-stu-id="bdd4f-106">Arguments</span></span>  

 `number`  
 <span data-ttu-id="bdd4f-107">一个值，用于指定输出文件中各节的大小。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-107">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="bdd4f-108">有效值为 512、1024、2048、4096 和 8192。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="bdd4f-109">这些值以字节为单位。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdd4f-110">备注</span><span class="sxs-lookup"><span data-stu-id="bdd4f-110">Remarks</span></span>  

 <span data-ttu-id="bdd4f-111">每一节都在是 -filealign 值的倍数的边界上对齐\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-111">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="bdd4f-112">没有固定的默认值。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-112">There is no fixed default.</span></span> <span data-ttu-id="bdd4f-113">如果未指定 -filealign，则公共语言运行时在编译时会选取一个默认值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-113">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="bdd4f-114">通过指定节的大小，可以影响输出文件的大小。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-114">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="bdd4f-115">修改节的大小可能对将在较小设备上运行的程序有用。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-115">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="bdd4f-116">使用 [DUMPBIN](/cpp/build/reference/dumpbin-options) 可查看有关输出文件中各节的信息。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bdd4f-117">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="bdd4f-117">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bdd4f-118">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-118">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="bdd4f-119">单击“生成”\*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-119">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="bdd4f-120">单击“高级”按钮。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-120">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="bdd4f-121">修改“文件对齐”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-121">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="bdd4f-122">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd4f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdd4f-123">See also</span></span>

- [<span data-ttu-id="bdd4f-124">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="bdd4f-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="bdd4f-125">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="bdd4f-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
