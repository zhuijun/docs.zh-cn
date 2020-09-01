---
description: -recurse（C# 编译器选项）
title: -recurse（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 3edd7e23358bc0569dae6204d519209df1ade290
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124820"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="63a66-103">-recurse（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="63a66-103">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="63a66-104">通过 -recurse 选项，可在指定目录 (dir) 的所有子目录中，或项目目录的所有子目录中编译源代码文件。</span><span class="sxs-lookup"><span data-stu-id="63a66-104">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63a66-105">语法</span><span class="sxs-lookup"><span data-stu-id="63a66-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="63a66-106">自变量</span><span class="sxs-lookup"><span data-stu-id="63a66-106">Arguments</span></span>  
 <span data-ttu-id="63a66-107">`dir`（可选）</span><span class="sxs-lookup"><span data-stu-id="63a66-107">`dir` (optional)</span></span>  
 <span data-ttu-id="63a66-108">希望从中开始搜索的目录。</span><span class="sxs-lookup"><span data-stu-id="63a66-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="63a66-109">如未指定目录，搜索将从项目目录开始。</span><span class="sxs-lookup"><span data-stu-id="63a66-109">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="63a66-110">要搜索的文件。</span><span class="sxs-lookup"><span data-stu-id="63a66-110">The file(s) to search for.</span></span> <span data-ttu-id="63a66-111">允许通配符。</span><span class="sxs-lookup"><span data-stu-id="63a66-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63a66-112">备注</span><span class="sxs-lookup"><span data-stu-id="63a66-112">Remarks</span></span>  
 <span data-ttu-id="63a66-113">通过 -recurse 选项，可在指定目录 (`dir`) 的所有子目录中，或项目目录的所有子目录中编译源代码文件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63a66-113">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="63a66-114">可在文件名中使用通配符，对项目目录中的所有匹配文件进行编译，而无需使用 -recurse\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63a66-114">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="63a66-115">此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。</span><span class="sxs-lookup"><span data-stu-id="63a66-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63a66-116">示例</span><span class="sxs-lookup"><span data-stu-id="63a66-116">Example</span></span>  
 <span data-ttu-id="63a66-117">在当前目录中编译所有 C# 文件：</span><span class="sxs-lookup"><span data-stu-id="63a66-117">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="63a66-118">编译 dir1\dir2 目录及其下的任何目录中的所有 C# 文件，并生成 dir2.dll：</span><span class="sxs-lookup"><span data-stu-id="63a66-118">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="63a66-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63a66-119">See also</span></span>

- [<span data-ttu-id="63a66-120">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="63a66-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="63a66-121">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="63a66-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
