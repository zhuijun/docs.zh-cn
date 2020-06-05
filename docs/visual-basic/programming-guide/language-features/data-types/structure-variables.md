---
title: 结构变量
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 270e8ca26185e4a68def3b95f4ce6ab4c57a629c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393580"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="6ba3a-102">结构变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ba3a-102">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="6ba3a-103">创建结构后，可以声明该类型的过程级和模块级变量。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="6ba3a-104">例如，可以创建一个结构来记录有关计算机系统的信息。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="6ba3a-105">下面的示例对这种情况进行了演示。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-105">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="6ba3a-106">现在可以声明该类型的变量。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-106">You can now declare variables of that type.</span></span> <span data-ttu-id="6ba3a-107">下面的声明阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-107">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="6ba3a-108">在类和模块中，使用[Dim 语句](../../../language-reference/statements/dim-statement.md)声明的结构默认为公共访问。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-108">In classes and modules, structures declared using the [Dim Statement](../../../language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="6ba3a-109">如果要将结构设置为私有，请确保使用[private](../../../language-reference/modifiers/private.md)关键字对其进行声明。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="6ba3a-110">对结构值的访问</span><span class="sxs-lookup"><span data-stu-id="6ba3a-110">Access to Structure Values</span></span>

<span data-ttu-id="6ba3a-111">若要分配和检索结构变量的元素中的值，请使用与用于设置和获取对象属性相同的语法。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="6ba3a-112">将成员访问运算符（）放置在 `.` 结构变量名和元素名之间。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="6ba3a-113">下面的示例访问之前声明为类型的变量元素 `systemInfo` 。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="6ba3a-114">分配结构变量</span><span class="sxs-lookup"><span data-stu-id="6ba3a-114">Assigning Structure Variables</span></span>

<span data-ttu-id="6ba3a-115">如果两个变量具有相同的结构类型，则也可以将其分配给另一个变量。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="6ba3a-116">这会将一个结构的所有元素复制到另一个结构中的相应元素。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="6ba3a-117">下面的声明阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-117">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="6ba3a-118">如果结构元素是引用类型（如 `String` 、 `Object` 或数组），则会复制指向数据的指针。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="6ba3a-119">在前面的示例中，如果 `systemInfo` 已包含一个对象变量，则前面的示例会将指向的指针复制 `mySystem` 到 `yourSystem` ，并且通过一个结构对该对象的数据的更改将在通过其他结构访问时生效。</span><span class="sxs-lookup"><span data-stu-id="6ba3a-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ba3a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ba3a-120">See also</span></span>

- [<span data-ttu-id="6ba3a-121">数据类型</span><span class="sxs-lookup"><span data-stu-id="6ba3a-121">Data Types</span></span>](index.md)
- [<span data-ttu-id="6ba3a-122">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="6ba3a-122">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="6ba3a-123">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="6ba3a-123">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="6ba3a-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="6ba3a-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="6ba3a-125">结构</span><span class="sxs-lookup"><span data-stu-id="6ba3a-125">Structures</span></span>](structures.md)
- [<span data-ttu-id="6ba3a-126">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="6ba3a-126">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="6ba3a-127">如何：声明结构</span><span class="sxs-lookup"><span data-stu-id="6ba3a-127">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="6ba3a-128">结构和其他编程元素</span><span class="sxs-lookup"><span data-stu-id="6ba3a-128">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="6ba3a-129">结构和类</span><span class="sxs-lookup"><span data-stu-id="6ba3a-129">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="6ba3a-130">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="6ba3a-130">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
