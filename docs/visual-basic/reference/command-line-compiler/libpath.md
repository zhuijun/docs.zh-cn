---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: dff7e0c3eb696b9b18f4c4e59240a26c1cb9782c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408531"
---
# <a name="-libpath"></a><span data-ttu-id="ddb04-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="ddb04-102">-libpath</span></span>
<span data-ttu-id="ddb04-103">指定引用的程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="ddb04-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb04-104">语法</span><span class="sxs-lookup"><span data-stu-id="ddb04-104">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ddb04-105">自变量</span><span class="sxs-lookup"><span data-stu-id="ddb04-105">Arguments</span></span>  
  
|<span data-ttu-id="ddb04-106">术语</span><span class="sxs-lookup"><span data-stu-id="ddb04-106">Term</span></span>|<span data-ttu-id="ddb04-107">定义</span><span class="sxs-lookup"><span data-stu-id="ddb04-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="ddb04-108">必需。</span><span class="sxs-lookup"><span data-stu-id="ddb04-108">Required.</span></span> <span data-ttu-id="ddb04-109">在当前工作目录（调用编译器的目录）或公共语言运行时的系统目录中未找到引用的程序集时，编译器将在其中进行查找的由分号分隔的目录列表。</span><span class="sxs-lookup"><span data-stu-id="ddb04-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="ddb04-110">如果目录名包含空格，则将名称括在引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="ddb04-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddb04-111">备注</span><span class="sxs-lookup"><span data-stu-id="ddb04-111">Remarks</span></span>  
 <span data-ttu-id="ddb04-112">`-libpath` 选项指定通过 [-reference](reference.md) 选项引用的程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="ddb04-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>  
  
 <span data-ttu-id="ddb04-113">编译器按以下顺序搜索未完全限定的程序集引用：</span><span class="sxs-lookup"><span data-stu-id="ddb04-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="ddb04-114">当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="ddb04-114">Current working directory.</span></span> <span data-ttu-id="ddb04-115">该目录为从其调用编译器的目录。</span><span class="sxs-lookup"><span data-stu-id="ddb04-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="ddb04-116">公共语言运行时系统目录。</span><span class="sxs-lookup"><span data-stu-id="ddb04-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="ddb04-117">由 `-libpath` 指定的目录。</span><span class="sxs-lookup"><span data-stu-id="ddb04-117">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="ddb04-118">由 LIB 环境变量指定的目录。</span><span class="sxs-lookup"><span data-stu-id="ddb04-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="ddb04-119">`-libpath` 选项是累加的；每一次指定的值都追加到以前的值中。</span><span class="sxs-lookup"><span data-stu-id="ddb04-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="ddb04-120">使用 `-reference` 指定程序集引用。</span><span class="sxs-lookup"><span data-stu-id="ddb04-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="ddb04-121">在 Visual Studio 集成开发环境中设置 -libpath</span><span class="sxs-lookup"><span data-stu-id="ddb04-121">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ddb04-122">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="ddb04-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ddb04-123">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="ddb04-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ddb04-124">2.单击“引用”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="ddb04-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="ddb04-125">3.单击“引用路径...”按钮。 </span><span class="sxs-lookup"><span data-stu-id="ddb04-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="ddb04-126">4.在“引用路径”对话框的“文件夹:”框中，输入目录名称。  </span><span class="sxs-lookup"><span data-stu-id="ddb04-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="ddb04-127">5.单击“添加文件夹”。 </span><span class="sxs-lookup"><span data-stu-id="ddb04-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ddb04-128">示例</span><span class="sxs-lookup"><span data-stu-id="ddb04-128">Example</span></span>  
 <span data-ttu-id="ddb04-129">下面的代码编译 `T2.vb`，用于生成 .exe 文件。</span><span class="sxs-lookup"><span data-stu-id="ddb04-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="ddb04-130">编译器将在工作目录、C: 驱动器的根目录和 C: 驱动器的“新程序集”目录中查找程序集引用。</span><span class="sxs-lookup"><span data-stu-id="ddb04-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddb04-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="ddb04-131">See also</span></span>

- [<span data-ttu-id="ddb04-132">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="ddb04-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="ddb04-133">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="ddb04-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ddb04-134">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="ddb04-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
