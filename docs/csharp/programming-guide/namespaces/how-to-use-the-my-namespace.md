---
title: 如何使用 My 命名空间 - C# 编程指南
description: 了解如何使用“My”命名空间。 “My”命名空间使访问多个 .NET 类变得轻松直观。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 5310b911cc0abf0e82c4dc8efd45eb45ffb94c9d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176222"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="3a227-104">如何使用 My 命名空间（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="3a227-104">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="3a227-105"><xref:Microsoft.VisualBasic.MyServices> 命名空间（在 Visual Basic 中为 `My`）使访问多个 .NET 类变得轻松直观，让你能够编写与计算机、应用程序、设置、资源等交互的代码。</span><span class="sxs-lookup"><span data-stu-id="3a227-105">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="3a227-106">虽然最初设计用于 Visual Basic，但 `MyServices` 命名空间仍可用于 C# 应用程序。</span><span class="sxs-lookup"><span data-stu-id="3a227-106">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="3a227-107">有关使用 Visual Basic 的 `MyServices` 命名空间的详细信息，请参阅[使用 My 开发](../../../visual-basic/developing-apps/development-with-my/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3a227-107">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="3a227-108">添加引用</span><span class="sxs-lookup"><span data-stu-id="3a227-108">Add a reference</span></span>

 <span data-ttu-id="3a227-109">可以在解决方案中使用 `MyServices` 类之前，必须添加对 Visual Basic 库的引用。</span><span class="sxs-lookup"><span data-stu-id="3a227-109">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="3a227-110">添加对 Visual Basic 库的引用</span><span class="sxs-lookup"><span data-stu-id="3a227-110">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="3a227-111">在解决方案资源管理器中，右键单击“引用”节点并选择“添加引用”  。</span><span class="sxs-lookup"><span data-stu-id="3a227-111">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="3a227-112">出现“引用”对话框时，向下滚动列表，然后选择“Microsoft.VisualBasic.dll”。</span><span class="sxs-lookup"><span data-stu-id="3a227-112">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="3a227-113">同时建议将以下行包括在程序开头的 `using` 部分。</span><span class="sxs-lookup"><span data-stu-id="3a227-113">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="3a227-114">示例</span><span class="sxs-lookup"><span data-stu-id="3a227-114">Example</span></span>  

 <span data-ttu-id="3a227-115">此示例调用 `MyServices` 命名空间中包含的各种静态方法。</span><span class="sxs-lookup"><span data-stu-id="3a227-115">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="3a227-116">若要编译此代码，必须向项目添加对 Microsoft.VisualBasic.DLL 的引用。</span><span class="sxs-lookup"><span data-stu-id="3a227-116">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="3a227-117">并不是 `MyServices` 命名空间中的所有类均可从 C# 应用程序中调用：例如，<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> 类不兼容。</span><span class="sxs-lookup"><span data-stu-id="3a227-117">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="3a227-118">在此特定情况下，可以改为使用属于 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 的静态方法，这些方法也包含在 VisualBasic.dll 中。</span><span class="sxs-lookup"><span data-stu-id="3a227-118">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="3a227-119">例如，下面介绍了如何使用此类方法来复制目录：</span><span class="sxs-lookup"><span data-stu-id="3a227-119">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="3a227-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="3a227-120">See also</span></span>

- [<span data-ttu-id="3a227-121">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="3a227-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3a227-122">命名空间</span><span class="sxs-lookup"><span data-stu-id="3a227-122">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="3a227-123">使用命名空间</span><span class="sxs-lookup"><span data-stu-id="3a227-123">Using Namespaces</span></span>](./using-namespaces.md)
