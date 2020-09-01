---
description: -noconfig（C# 编译器选项）
title: -noconfig（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 26d0680743ccc3af26a0e81eeec9cd2fc0d693af
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125223"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="784b9-103">-noconfig（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="784b9-103">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="784b9-104">-noconfig 选项告知编译器不要在 csc.rsp 文件中编译，该文件的位置和加载位置是与 csc.exe 文件相同的目录\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="784b9-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="784b9-105">语法</span><span class="sxs-lookup"><span data-stu-id="784b9-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="784b9-106">备注</span><span class="sxs-lookup"><span data-stu-id="784b9-106">Remarks</span></span>  
 <span data-ttu-id="784b9-107">csc.rsp 文件引用 .NET Framework 随附的所有程序集。</span><span class="sxs-lookup"><span data-stu-id="784b9-107">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="784b9-108">Visual Studio .NET 开发环境包括的实际引用取决于项目类型。</span><span class="sxs-lookup"><span data-stu-id="784b9-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="784b9-109">可以修改 csc.rsp 文件并使用 csc.exe 的命令行指定每个编译中应包含的其他编译器选项（-noconfig 选项外）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="784b9-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="784b9-110">编译器将处理最后传递给 csc 命令的选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="784b9-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="784b9-111">因此，命令行中的任何选项都将替代 csc.rsp 文件中相同选项的设置。</span><span class="sxs-lookup"><span data-stu-id="784b9-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="784b9-112">如果不希望编译器查询和使用 csc.rsp 文件中的设置，请指定 -noconfig\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="784b9-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="784b9-113">此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。</span><span class="sxs-lookup"><span data-stu-id="784b9-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="784b9-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="784b9-114">See also</span></span>

- [<span data-ttu-id="784b9-115">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="784b9-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="784b9-116">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="784b9-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
