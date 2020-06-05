---
title: 未定义类型“<typename>”
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386927"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="08b8d-102">未定义类型“\<typename>”</span><span class="sxs-lookup"><span data-stu-id="08b8d-102">Type '\<typename>' is not defined</span></span>
<span data-ttu-id="08b8d-103">语句引用了未定义的类型。</span><span class="sxs-lookup"><span data-stu-id="08b8d-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="08b8d-104">可在声明语句（如、、或）中定义类型 `Enum` `Structure` `Class` `Interface` 。</span><span class="sxs-lookup"><span data-stu-id="08b8d-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="08b8d-105">**错误 ID：** BC30002</span><span class="sxs-lookup"><span data-stu-id="08b8d-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08b8d-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="08b8d-106">To correct this error</span></span>  
  
- <span data-ttu-id="08b8d-107">确保类型定义及其引用均使用相同的拼写。</span><span class="sxs-lookup"><span data-stu-id="08b8d-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
- <span data-ttu-id="08b8d-108">确保引用可以访问类型定义。</span><span class="sxs-lookup"><span data-stu-id="08b8d-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="08b8d-109">例如，如果类型在另一个模块中并且已被声明 `Private` ，请将类型定义移到引用模块，或将其声明为 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="08b8d-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
- <span data-ttu-id="08b8d-110">确保未在项目中重新定义类型的命名空间。</span><span class="sxs-lookup"><span data-stu-id="08b8d-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="08b8d-111">如果是，则使用 `Global` 关键字完全限定类型名称。</span><span class="sxs-lookup"><span data-stu-id="08b8d-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="08b8d-112">例如，如果项目定义名为的命名空间 `System` ，则 <xref:System.Object?displayProperty=nameWithType> 无法访问该类型，除非它是用关键字：完全限定的 `Global` `Global.System.Object` 。</span><span class="sxs-lookup"><span data-stu-id="08b8d-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
- <span data-ttu-id="08b8d-113">如果定义了该类型，但在 Visual Basic 中未注册定义该类型的对象库或类型库，请单击 "**项目**" 菜单上的 "**添加引用**"，然后选择相应的对象库或类型库。</span><span class="sxs-lookup"><span data-stu-id="08b8d-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
- <span data-ttu-id="08b8d-114">确保该类型位于作为目标 .NET Framework 配置文件的一部分的程序集中。</span><span class="sxs-lookup"><span data-stu-id="08b8d-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="08b8d-115">有关详细信息，请参阅[排查 .NET Framework 目标错误](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。</span><span class="sxs-lookup"><span data-stu-id="08b8d-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b8d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08b8d-116">See also</span></span>

- [<span data-ttu-id="08b8d-117">Visual Basic 中的命名空间</span><span class="sxs-lookup"><span data-stu-id="08b8d-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="08b8d-118">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="08b8d-118">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="08b8d-119">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="08b8d-119">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="08b8d-120">Class 语句</span><span class="sxs-lookup"><span data-stu-id="08b8d-120">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="08b8d-121">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="08b8d-121">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="08b8d-122">管理项目中的引用</span><span class="sxs-lookup"><span data-stu-id="08b8d-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
