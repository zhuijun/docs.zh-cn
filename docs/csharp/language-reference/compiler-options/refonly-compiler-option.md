---
description: -refonly（C# 编译器选项）
title: -refonly（C# 编译器选项）
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124742"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="835fb-103">-refonly（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="835fb-103">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="835fb-104">-refonly 选项表示应输出引用程序集（而不是实现程序集）作为主输出\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="835fb-104">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="835fb-105">`-refonly` 参数以无提示方式禁用输出 PDB，因为无法执行引用程序集。</span><span class="sxs-lookup"><span data-stu-id="835fb-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="835fb-106">此选项对应于 MSBuild 的 [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 项目属性。</span><span class="sxs-lookup"><span data-stu-id="835fb-106">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="835fb-107">语法</span><span class="sxs-lookup"><span data-stu-id="835fb-107">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="835fb-108">备注</span><span class="sxs-lookup"><span data-stu-id="835fb-108">Remarks</span></span>

<span data-ttu-id="835fb-109">引用程序集是一种特殊类型的程序集，它只包含表示库的公共 API 外围应用所需的最少元数据量。</span><span class="sxs-lookup"><span data-stu-id="835fb-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="835fb-110">它们包括在生成工具中引用程序集时所需的所有成员的声明，但不包括所有成员实现以及对其 API 协定没有明显影响的私有成员的声明。</span><span class="sxs-lookup"><span data-stu-id="835fb-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="835fb-111">有关详细信息，请参阅 .NET 指南中的[引用程序集](../../../standard/assembly/reference-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="835fb-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="835fb-112">`-refonly` 和 [`-refout`](refout-compiler-option.md) 选项互斥。</span><span class="sxs-lookup"><span data-stu-id="835fb-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="835fb-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="835fb-113">See also</span></span>

- [<span data-ttu-id="835fb-114">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="835fb-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="835fb-115">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="835fb-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
