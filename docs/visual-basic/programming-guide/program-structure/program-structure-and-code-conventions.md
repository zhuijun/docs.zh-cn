---
title: 程序结构和代码约定
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: c8d851afc33e7e898ab16abc941d8680f74145e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398300"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="8375f-102">程序结构和代码约定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8375f-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="8375f-103">本部分介绍了典型的 Visual Basic 计划结构，提供了一个简单的 Visual Basic 程序： "Hello，World"，并讨论 Visual Basic 代码约定。</span><span class="sxs-lookup"><span data-stu-id="8375f-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="8375f-104">代码约定是重点介绍不在程序逻辑上，而是在其物理结构和外观上的建议。</span><span class="sxs-lookup"><span data-stu-id="8375f-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="8375f-105">下面的代码可使代码更易于阅读、理解和维护。</span><span class="sxs-lookup"><span data-stu-id="8375f-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="8375f-106">代码约定可以包含其他内容：</span><span class="sxs-lookup"><span data-stu-id="8375f-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="8375f-107">用于标记和注释代码的标准化格式。</span><span class="sxs-lookup"><span data-stu-id="8375f-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="8375f-108">间距、格式设置和缩进代码的准则。</span><span class="sxs-lookup"><span data-stu-id="8375f-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="8375f-109">对象、变量和过程的命名约定。</span><span class="sxs-lookup"><span data-stu-id="8375f-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="8375f-110">以下主题提供了一组用于 Visual Basic 程序的编程准则，以及良好使用的示例。</span><span class="sxs-lookup"><span data-stu-id="8375f-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8375f-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="8375f-111">In This Section</span></span>  
 [<span data-ttu-id="8375f-112">Visual Basic 程序的结构</span><span class="sxs-lookup"><span data-stu-id="8375f-112">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="8375f-113">提供组成 Visual Basic 程序的元素的概述。</span><span class="sxs-lookup"><span data-stu-id="8375f-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="8375f-114">Visual Basic 中的 Main 过程</span><span class="sxs-lookup"><span data-stu-id="8375f-114">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="8375f-115">讨论作为开始点和应用程序的总体控制的过程。</span><span class="sxs-lookup"><span data-stu-id="8375f-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="8375f-116">引用和 Imports 语句</span><span class="sxs-lookup"><span data-stu-id="8375f-116">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="8375f-117">讨论如何引用其他程序集中的对象。</span><span class="sxs-lookup"><span data-stu-id="8375f-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="8375f-118">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="8375f-118">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="8375f-119">描述命名空间如何组织程序集内的对象。</span><span class="sxs-lookup"><span data-stu-id="8375f-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="8375f-120">Visual Basic 命名约定</span><span class="sxs-lookup"><span data-stu-id="8375f-120">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="8375f-121">包括命名过程、常量、变量、参数和对象的一般准则。</span><span class="sxs-lookup"><span data-stu-id="8375f-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="8375f-122">Visual Basic 编码约定</span><span class="sxs-lookup"><span data-stu-id="8375f-122">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="8375f-123">查看在本文档中开发示例时使用的准则。</span><span class="sxs-lookup"><span data-stu-id="8375f-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="8375f-124">条件编译</span><span class="sxs-lookup"><span data-stu-id="8375f-124">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="8375f-125">介绍如何有选择性地编译特定代码块，同时指示编译器忽略其他代码块。</span><span class="sxs-lookup"><span data-stu-id="8375f-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="8375f-126">如何：在代码中拆分和合并语句</span><span class="sxs-lookup"><span data-stu-id="8375f-126">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="8375f-127">说明如何将长语句分割为多行，并将短语句合并到一行。</span><span class="sxs-lookup"><span data-stu-id="8375f-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="8375f-128">如何：折叠和隐藏代码节</span><span class="sxs-lookup"><span data-stu-id="8375f-128">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="8375f-129">演示如何折叠和隐藏 Visual Basic 代码编辑器中的代码段。</span><span class="sxs-lookup"><span data-stu-id="8375f-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="8375f-130">如何：标记语句</span><span class="sxs-lookup"><span data-stu-id="8375f-130">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="8375f-131">演示如何将代码行标记为将其标识为与等语句一起使用 `On Error Goto` 。</span><span class="sxs-lookup"><span data-stu-id="8375f-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="8375f-132">代码中的特殊字符</span><span class="sxs-lookup"><span data-stu-id="8375f-132">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="8375f-133">显示如何以及在何处使用非数字字符和非字母字符。</span><span class="sxs-lookup"><span data-stu-id="8375f-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="8375f-134">代码中的注释</span><span class="sxs-lookup"><span data-stu-id="8375f-134">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="8375f-135">讨论如何向代码添加描述性注释。</span><span class="sxs-lookup"><span data-stu-id="8375f-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="8375f-136">代码中用作元素名称的关键字</span><span class="sxs-lookup"><span data-stu-id="8375f-136">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="8375f-137">介绍如何使用括号（ `[]` ）来分隔同时 Visual Basic 关键字的变量名称。</span><span class="sxs-lookup"><span data-stu-id="8375f-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="8375f-138">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="8375f-138">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="8375f-139">描述引用 Visual Basic 程序的元素的各种方法。</span><span class="sxs-lookup"><span data-stu-id="8375f-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="8375f-140">Visual Basic 限制</span><span class="sxs-lookup"><span data-stu-id="8375f-140">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="8375f-141">讨论 Visual Basic 中删除已知编码限制。</span><span class="sxs-lookup"><span data-stu-id="8375f-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8375f-142">相关章节</span><span class="sxs-lookup"><span data-stu-id="8375f-142">Related Sections</span></span>  
 [<span data-ttu-id="8375f-143">版式和代码约定</span><span class="sxs-lookup"><span data-stu-id="8375f-143">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="8375f-144">为 Visual Basic 提供标准编码约定。</span><span class="sxs-lookup"><span data-stu-id="8375f-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="8375f-145">编写代码</span><span class="sxs-lookup"><span data-stu-id="8375f-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="8375f-146">介绍一些功能，使您可以更轻松地编写和管理代码。</span><span class="sxs-lookup"><span data-stu-id="8375f-146">Describes features that make it easier for you to write and manage your code.</span></span>
