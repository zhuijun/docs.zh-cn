---
title: 如何：使用泛型类
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393839"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="34747-102">如何：使用泛型类 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34747-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="34747-103">采用 *类型参数* 的类称为 *泛型类*。</span><span class="sxs-lookup"><span data-stu-id="34747-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="34747-104">如果使用一个泛型类，则可以通过为每个形参提供 *类型实参* ，从该类生成 *构造类* 。</span><span class="sxs-lookup"><span data-stu-id="34747-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="34747-105">随后可以声明构造类类型的一个变量，可以创建构造类的实例并将它分配给该变量。</span><span class="sxs-lookup"><span data-stu-id="34747-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="34747-106">除了类之外，你还可以定义和使用泛型结构、接口、过程和委托。</span><span class="sxs-lookup"><span data-stu-id="34747-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="34747-107">下面的过程使用在 .NET Framework 中定义的泛型类，并从它创建一个实例。</span><span class="sxs-lookup"><span data-stu-id="34747-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="34747-108">使用采用类型参数的类</span><span class="sxs-lookup"><span data-stu-id="34747-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="34747-109">在源文件的开头，包括[Imports 语句（.Net 命名空间和类型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)以导入 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="34747-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="34747-110">这使你可以引用 <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> 类，而不必完全限定它即可将它与其他队列类（如 <xref:System.Collections.Queue?displayProperty=nameWithType>）区分开来。</span><span class="sxs-lookup"><span data-stu-id="34747-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="34747-111">以正常方式创建对象，但是紧接在类名之后添加 `(Of type)` 。</span><span class="sxs-lookup"><span data-stu-id="34747-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="34747-112">下面的示例使用相同类 (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) 创建保存不同数据类型的项的两个队列对象。</span><span class="sxs-lookup"><span data-stu-id="34747-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="34747-113">它将项添加到每个队列末尾，然后从每个队列的前面删除并显示项。</span><span class="sxs-lookup"><span data-stu-id="34747-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="34747-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34747-114">See also</span></span>

- [<span data-ttu-id="34747-115">数据类型</span><span class="sxs-lookup"><span data-stu-id="34747-115">Data Types</span></span>](index.md)
- [<span data-ttu-id="34747-116">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34747-116">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="34747-117">语言独立性和与语言无关的组件</span><span class="sxs-lookup"><span data-stu-id="34747-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="34747-118">个</span><span class="sxs-lookup"><span data-stu-id="34747-118">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="34747-119">Imports 语句（.NET 命名空间和类型）</span><span class="sxs-lookup"><span data-stu-id="34747-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="34747-120">如何：定义可对不同数据类型提供相同功能的类</span><span class="sxs-lookup"><span data-stu-id="34747-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="34747-121">迭代器</span><span class="sxs-lookup"><span data-stu-id="34747-121">Iterators</span></span>](../../concepts/iterators.md)
