---
title: 后期绑定解决方案；可能会发生运行时错误
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397345"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="e9533-102">后期绑定解决方案；可能会发生运行时错误</span><span class="sxs-lookup"><span data-stu-id="e9533-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="e9533-103">对象被分配给声明为[Object 数据类型](../data-types/object-data-type.md)的变量。</span><span class="sxs-lookup"><span data-stu-id="e9533-103">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="e9533-104">将变量声明为时 `Object` ，编译器必须执行*后期绑定*，这会导致在运行时产生额外的操作。</span><span class="sxs-lookup"><span data-stu-id="e9533-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="e9533-105">它还使应用程序易于发生潜在的运行时错误。</span><span class="sxs-lookup"><span data-stu-id="e9533-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="e9533-106">例如，如果将分配 <xref:System.Windows.Forms.Form> 到 `Object` 变量，然后尝试访问 <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> 属性，则运行时将引发， <xref:System.MemberAccessException> 因为该类不 <xref:System.Windows.Forms.Form> 公开 `NameTable` 属性。</span><span class="sxs-lookup"><span data-stu-id="e9533-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="e9533-107">如果将变量声明为特定类型，编译器可以在编译时执行*早期绑定*。</span><span class="sxs-lookup"><span data-stu-id="e9533-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="e9533-108">这会提高性能、控制对特定类型的成员的访问，以及更好的代码可读性。</span><span class="sxs-lookup"><span data-stu-id="e9533-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="e9533-109">默认情况下，此消息是一个警告。</span><span class="sxs-lookup"><span data-stu-id="e9533-109">By default, this message is a warning.</span></span> <span data-ttu-id="e9533-110">有关隐藏警告或将警告视为错误的信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="e9533-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e9533-111">**错误 ID：** BC42017</span><span class="sxs-lookup"><span data-stu-id="e9533-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9533-112">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e9533-112">To correct this error</span></span>  
  
- <span data-ttu-id="e9533-113">如果可能，请将变量声明为特定类型。</span><span class="sxs-lookup"><span data-stu-id="e9533-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9533-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9533-114">See also</span></span>

- [<span data-ttu-id="e9533-115">早期绑定和后期绑定</span><span class="sxs-lookup"><span data-stu-id="e9533-115">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="e9533-116">对象变量声明</span><span class="sxs-lookup"><span data-stu-id="e9533-116">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
