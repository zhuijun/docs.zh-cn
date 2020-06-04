---
title: 早期绑定和晚期绑定
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: e8d87e095b7c3104e3a2d66525644d1771ae883e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410627"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="7eaf3-102">早期绑定和后期绑定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7eaf3-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="7eaf3-103">Visual Basic 编译器将 `binding` 在对象被分配给对象变量时执行调用的进程。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="7eaf3-104">如果对象被分配给声明为特定对象类型的变量，就是*早期绑定*对象。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="7eaf3-105">借助早期绑定对象，编译器可以在应用程序执行前分配内存并执行其他优化。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="7eaf3-106">例如，下面的代码片段将变量声明为类型 <xref:System.IO.FileStream>：</span><span class="sxs-lookup"><span data-stu-id="7eaf3-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="7eaf3-107">由于 <xref:System.IO.FileStream> 是特定对象类型，因此分配给 `FS` 的实例就是早期绑定对象。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="7eaf3-108">相反，如果对象被分配给声明为 `Object` 类型的变量，就是*晚期绑定*对象。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="7eaf3-109">虽然这种类型的对象可保留对任何对象的引用，但却没有早期绑定对象的诸多优点。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="7eaf3-110">例如，下面的代码片段将对象变量声明为保留 `CreateObject` 函数返回的对象：</span><span class="sxs-lookup"><span data-stu-id="7eaf3-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="7eaf3-111">早期绑定的优点</span><span class="sxs-lookup"><span data-stu-id="7eaf3-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="7eaf3-112">应尽量使用早期绑定对象，因为这样编译器可以执行重要优化，从而大大提升应用程序的工作效率。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="7eaf3-113">早期绑定对象的速度远超晚期绑定对象，并明确指出在使用的对象类型，使得代码更易于阅读和维护。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="7eaf3-114">早期绑定的另一个优点是，它启用了一些有用的功能，如自动代码完成和动态帮助，因为 Visual Studio 集成开发环境（IDE）可以在编辑代码时准确确定所使用的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="7eaf3-115">早期绑定降低了运行时错误的数量和严重性，因为它允许编译器在编译程序时报告错误。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7eaf3-116">晚期绑定只能用于访问声明为 `Public` 的类型成员。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="7eaf3-117">访问声明为 `Friend` 或 `Protected Friend` 的成员会导致生成运行时错误。</span><span class="sxs-lookup"><span data-stu-id="7eaf3-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eaf3-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7eaf3-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="7eaf3-119">对象生存期：如何创建和销毁对象</span><span class="sxs-lookup"><span data-stu-id="7eaf3-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="7eaf3-120">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="7eaf3-120">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
