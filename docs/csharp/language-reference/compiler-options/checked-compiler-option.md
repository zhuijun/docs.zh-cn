---
description: -checked（C# 编译器选项）
title: -checked（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 5c90696edd3031271e16cd2c1a332da5b605f81f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125938"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="30da7-103">-checked（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="30da7-103">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="30da7-104">-checked 选项指定，不在 [checked](../keywords/checked.md) 或 [unchecked](../keywords/unchecked.md) 关键字的范围内、并且产生的值超出数据类型范围的整数算法语句是否将导致运行时异常。</span><span class="sxs-lookup"><span data-stu-id="30da7-104">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30da7-105">语法</span><span class="sxs-lookup"><span data-stu-id="30da7-105">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="30da7-106">备注</span><span class="sxs-lookup"><span data-stu-id="30da7-106">Remarks</span></span>  
 <span data-ttu-id="30da7-107">`checked` 或 `unchecked` 关键字范围内的整数算法语句不受 -checked 选项的影响。</span><span class="sxs-lookup"><span data-stu-id="30da7-107">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="30da7-108">如果不在 `checked` 或 `unchecked` 关键字范围内的整数算法语句产生的值超出数据类型范围，并且编译中使用了 -checked+（或 -checked），则该语句将在运行时导致异常\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30da7-108">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="30da7-109">如果编译中使用的是 -checked-，则该语句在运行时不会导致异常。</span><span class="sxs-lookup"><span data-stu-id="30da7-109">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="30da7-110">此选项的默认值为“-checked-”\*\*\*\*；溢出检查已禁用。</span><span class="sxs-lookup"><span data-stu-id="30da7-110">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="30da7-111">有时，用于生成大型应用程序的自动化工具将 -checked 设置为 +。</span><span class="sxs-lookup"><span data-stu-id="30da7-111">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="30da7-112">使用 -checked- 的一种方案：通过指定 -checked- 来替代工具的全局默认值。</span><span class="sxs-lookup"><span data-stu-id="30da7-112">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="30da7-113">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="30da7-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="30da7-114">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="30da7-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="30da7-115">有关详细信息，请参阅 [“项目设计器”->“生成”页 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="30da7-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="30da7-116">单击“生成”\*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="30da7-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="30da7-117">单击“高级”按钮。</span><span class="sxs-lookup"><span data-stu-id="30da7-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="30da7-118">修改“检查算术溢出”属性。</span><span class="sxs-lookup"><span data-stu-id="30da7-118">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="30da7-119">要以编程方式访问此编译器选项，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>。</span><span class="sxs-lookup"><span data-stu-id="30da7-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30da7-120">示例</span><span class="sxs-lookup"><span data-stu-id="30da7-120">Example</span></span>  
 <span data-ttu-id="30da7-121">以下命令编译 `t2.cs`。</span><span class="sxs-lookup"><span data-stu-id="30da7-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="30da7-122">命令中 `-checked` 的使用指定，任何不在 `checked` 或 `unchecked` 关键字范围内以及导致数据类型以外值的结果的文件中的整数算术语句，会在运行时引发异常。</span><span class="sxs-lookup"><span data-stu-id="30da7-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="30da7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30da7-123">See also</span></span>

- [<span data-ttu-id="30da7-124">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="30da7-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="30da7-125">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="30da7-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
