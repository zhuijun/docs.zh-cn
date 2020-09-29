---
description: -nowarn（C# 编译器选项）
title: -nowarn（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194019"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="286e9-103">-nowarn（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="286e9-103">-nowarn (C# Compiler Options)</span></span>

<span data-ttu-id="286e9-104">使用 -nowarn 选项可以禁止编译器显示一个或多个警告。</span><span class="sxs-lookup"><span data-stu-id="286e9-104">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="286e9-105">使用逗号分隔多个警告编号。</span><span class="sxs-lookup"><span data-stu-id="286e9-105">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="286e9-106">语法</span><span class="sxs-lookup"><span data-stu-id="286e9-106">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="286e9-107">自变量</span><span class="sxs-lookup"><span data-stu-id="286e9-107">Arguments</span></span>  

 <span data-ttu-id="286e9-108">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="286e9-108">`number1`, `number2`</span></span>  
 <span data-ttu-id="286e9-109">希望编译器禁止显示的警告编号。</span><span class="sxs-lookup"><span data-stu-id="286e9-109">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="286e9-110">备注</span><span class="sxs-lookup"><span data-stu-id="286e9-110">Remarks</span></span>  

 <span data-ttu-id="286e9-111">只应指定警告标识符的数值部分。</span><span class="sxs-lookup"><span data-stu-id="286e9-111">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="286e9-112">例如，如果要禁止显示 CS0028，则可以指定 `-nowarn:28`。</span><span class="sxs-lookup"><span data-stu-id="286e9-112">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="286e9-113">编译器会以无提示方式忽略传递给 `-nowarn` 的警告编号，这些编号在早期版本中有效，但已从编译器中移除。</span><span class="sxs-lookup"><span data-stu-id="286e9-113">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="286e9-114">例如，CS0679 在 Visual Studio .NET 2002 的编译器中有效，但是在后来已移除。</span><span class="sxs-lookup"><span data-stu-id="286e9-114">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="286e9-115">无法通过 `-nowarn` 选项禁止显示以下警告：</span><span class="sxs-lookup"><span data-stu-id="286e9-115">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="286e9-116">编译器警告（等级 1）CS2002</span><span class="sxs-lookup"><span data-stu-id="286e9-116">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="286e9-117">编译器警告（等级 1）CS2023</span><span class="sxs-lookup"><span data-stu-id="286e9-117">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="286e9-118">编译器警告（等级 1）CS2029</span><span class="sxs-lookup"><span data-stu-id="286e9-118">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="286e9-119">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="286e9-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="286e9-120">打开项目的“属性” \*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="286e9-120">Open the **Properties** page for the project.</span></span> <span data-ttu-id="286e9-121">有关详细信息，请参阅[“项目设计器”->“生成”页 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="286e9-121">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="286e9-122">单击“生成”\*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="286e9-122">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="286e9-123">修改“禁止显示警告”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="286e9-123">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="286e9-124">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。</span><span class="sxs-lookup"><span data-stu-id="286e9-124">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286e9-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="286e9-125">See also</span></span>

- [<span data-ttu-id="286e9-126">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="286e9-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="286e9-127">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="286e9-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="286e9-128">C# 编译器错误</span><span class="sxs-lookup"><span data-stu-id="286e9-128">C# Compiler Errors</span></span>](../compiler-messages/index.md)
