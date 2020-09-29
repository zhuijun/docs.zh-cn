---
title: 如何显示命令行参数 - C# 编程指南
description: 了解如何显示命令行参数。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 717e27c23724e63c03a38b028ef99dc6530b4745
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195475"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="0660c-104">如何显示命令行参数（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="0660c-104">How to display command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="0660c-105">可通过 `Main` 的可选参数来访问在命令行处提供给可执行文件的参数。</span><span class="sxs-lookup"><span data-stu-id="0660c-105">Arguments provided to an executable on the command line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="0660c-106">参数以字符串数组的形式提供。</span><span class="sxs-lookup"><span data-stu-id="0660c-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="0660c-107">数组的每个元素都包含 1 个参数。</span><span class="sxs-lookup"><span data-stu-id="0660c-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="0660c-108">删除参数之间的空格。</span><span class="sxs-lookup"><span data-stu-id="0660c-108">White-space between arguments is removed.</span></span> <span data-ttu-id="0660c-109">例如，下面是对虚构可执行文件的命令行调用：</span><span class="sxs-lookup"><span data-stu-id="0660c-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="0660c-110">命令行上的输入</span><span class="sxs-lookup"><span data-stu-id="0660c-110">Input on command line</span></span>|<span data-ttu-id="0660c-111">传递给 Main 的字符串数组</span><span class="sxs-lookup"><span data-stu-id="0660c-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="0660c-112">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="0660c-112">**executable.exe a b c**</span></span>|<span data-ttu-id="0660c-113">"a"</span><span class="sxs-lookup"><span data-stu-id="0660c-113">"a"</span></span><br /><br /> <span data-ttu-id="0660c-114">"b"</span><span class="sxs-lookup"><span data-stu-id="0660c-114">"b"</span></span><br /><br /> <span data-ttu-id="0660c-115">“c”</span><span class="sxs-lookup"><span data-stu-id="0660c-115">"c"</span></span>|  
|<span data-ttu-id="0660c-116">**executable.exe one two**</span><span class="sxs-lookup"><span data-stu-id="0660c-116">**executable.exe one two**</span></span>|<span data-ttu-id="0660c-117">"one"</span><span class="sxs-lookup"><span data-stu-id="0660c-117">"one"</span></span><br /><br /> <span data-ttu-id="0660c-118">"two"</span><span class="sxs-lookup"><span data-stu-id="0660c-118">"two"</span></span>|  
|<span data-ttu-id="0660c-119">**executable.exe "one two" three**</span><span class="sxs-lookup"><span data-stu-id="0660c-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="0660c-120">"one two"</span><span class="sxs-lookup"><span data-stu-id="0660c-120">"one two"</span></span><br /><br /> <span data-ttu-id="0660c-121">"three"</span><span class="sxs-lookup"><span data-stu-id="0660c-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0660c-122">在 Visual Studio 中运行应用程序时，可在[“项目设计器”->“调试”页](/visualstudio/ide/reference/debug-page-project-designer)中指定命令行参数。</span><span class="sxs-lookup"><span data-stu-id="0660c-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0660c-123">示例</span><span class="sxs-lookup"><span data-stu-id="0660c-123">Example</span></span>  

 <span data-ttu-id="0660c-124">本示例显示了传递给命令行应用程序的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="0660c-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="0660c-125">显示的输出对应于上表中的第一项。</span><span class="sxs-lookup"><span data-stu-id="0660c-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="0660c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0660c-126">See also</span></span>

- [<span data-ttu-id="0660c-127">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="0660c-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0660c-128">在命令行上使用 csc.exe 生成</span><span class="sxs-lookup"><span data-stu-id="0660c-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="0660c-129">Main() 和命令行参数</span><span class="sxs-lookup"><span data-stu-id="0660c-129">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="0660c-130">Main() 返回值</span><span class="sxs-lookup"><span data-stu-id="0660c-130">Main() Return Values</span></span>](./main-return-values.md)
