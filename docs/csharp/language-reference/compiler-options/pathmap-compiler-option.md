---
description: -pathmap（C# 编译器选项）
title: -pathmap（C# 编译器选项）
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 707a37c6946cfcaf429552f0aeece6b87f3ad71d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125002"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="0e55e-103">-pathmap（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="0e55e-103">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="0e55e-104">\*\*\*\*-pathmap 编译器选项指定如何将物理路径映射到编译器输出的源路径名称。</span><span class="sxs-lookup"><span data-stu-id="0e55e-104">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e55e-105">语法</span><span class="sxs-lookup"><span data-stu-id="0e55e-105">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="0e55e-106">自变量</span><span class="sxs-lookup"><span data-stu-id="0e55e-106">Arguments</span></span>

 <span data-ttu-id="0e55e-107">`path1` 当前环境中源文件的完整路径</span><span class="sxs-lookup"><span data-stu-id="0e55e-107">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="0e55e-108">`sourcePath1` 在任何输出文件中将源路径替换为 `path1`。</span><span class="sxs-lookup"><span data-stu-id="0e55e-108">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="0e55e-109">要指定多个映射的源路径，请用逗号分隔每个路径。</span><span class="sxs-lookup"><span data-stu-id="0e55e-109">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e55e-110">备注</span><span class="sxs-lookup"><span data-stu-id="0e55e-110">Remarks</span></span>

<span data-ttu-id="0e55e-111">编译器将源路径写入其输出，原因如下：</span><span class="sxs-lookup"><span data-stu-id="0e55e-111">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="0e55e-112">将 <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 应用于可选参数时，会将源路径替换为参数。</span><span class="sxs-lookup"><span data-stu-id="0e55e-112">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="0e55e-113">PDB 文件中嵌入的源路径。</span><span class="sxs-lookup"><span data-stu-id="0e55e-113">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="0e55e-114">PDB 文件的路径嵌入到 PE（可移植的可执行文件）文件中。</span><span class="sxs-lookup"><span data-stu-id="0e55e-114">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="0e55e-115">此选项将编译器在其上运行的计算机上的每个物理路径映射到应写入输出文件的相应路径。</span><span class="sxs-lookup"><span data-stu-id="0e55e-115">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="0e55e-116">示例</span><span class="sxs-lookup"><span data-stu-id="0e55e-116">Example</span></span>

<span data-ttu-id="0e55e-117">在目录 C:\\work\\tests\*\*\*\* 中编译 `t.cs` 并将该目录映射到输出中的 \publish\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="0e55e-117">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="0e55e-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e55e-118">See also</span></span>

- [<span data-ttu-id="0e55e-119">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="0e55e-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0e55e-120">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="0e55e-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
