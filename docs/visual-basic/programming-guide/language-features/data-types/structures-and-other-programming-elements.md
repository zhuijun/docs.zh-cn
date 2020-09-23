---
title: 结构和其他编程元素
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 26c98adda7305783b0220141db35b08285b21554
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084081"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="21900-102">结构和其他编程元素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21900-102">Structures and Other Programming Elements (Visual Basic)</span></span>

<span data-ttu-id="21900-103">您可以将结构与数组、对象和过程以及彼此一起使用。</span><span class="sxs-lookup"><span data-stu-id="21900-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="21900-104">交互使用的语法与这些元素分别使用的语法相同。</span><span class="sxs-lookup"><span data-stu-id="21900-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21900-105">不能在结构声明中初始化任何结构元素。</span><span class="sxs-lookup"><span data-stu-id="21900-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="21900-106">只能为已声明为结构类型的变量的元素赋值。</span><span class="sxs-lookup"><span data-stu-id="21900-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="21900-107">结构和数组</span><span class="sxs-lookup"><span data-stu-id="21900-107">Structures and Arrays</span></span>  

 <span data-ttu-id="21900-108">结构可以包含数组作为其一个或多个元素。</span><span class="sxs-lookup"><span data-stu-id="21900-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="21900-109">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="21900-110">访问结构中数组的值的方式与访问对象上的属性的方式相同。</span><span class="sxs-lookup"><span data-stu-id="21900-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="21900-111">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="21900-112">还可以声明结构的数组。</span><span class="sxs-lookup"><span data-stu-id="21900-112">You can also declare an array of structures.</span></span> <span data-ttu-id="21900-113">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="21900-114">遵循相同的规则来访问此数据体系结构的组件。</span><span class="sxs-lookup"><span data-stu-id="21900-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="21900-115">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="21900-116">结构和对象</span><span class="sxs-lookup"><span data-stu-id="21900-116">Structures and Objects</span></span>  

 <span data-ttu-id="21900-117">结构可以包含对象作为其一个或多个元素。</span><span class="sxs-lookup"><span data-stu-id="21900-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="21900-118">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="21900-119">在此类声明中应使用特定对象类，而不是 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="21900-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="21900-120">结构和过程</span><span class="sxs-lookup"><span data-stu-id="21900-120">Structures and Procedures</span></span>  

 <span data-ttu-id="21900-121">可以将结构作为过程自变量传递。</span><span class="sxs-lookup"><span data-stu-id="21900-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="21900-122">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="21900-123">前面的示例 *通过引用*传递结构，这允许过程修改其元素，以使所做的更改在调用代码中生效。</span><span class="sxs-lookup"><span data-stu-id="21900-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="21900-124">如果要针对此类修改保护结构，请按值传递它。</span><span class="sxs-lookup"><span data-stu-id="21900-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="21900-125">还可以从过程返回结构 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="21900-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="21900-126">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="21900-127">结构内的结构</span><span class="sxs-lookup"><span data-stu-id="21900-127">Structures Within Structures</span></span>  

 <span data-ttu-id="21900-128">结构可以包含其他结构。</span><span class="sxs-lookup"><span data-stu-id="21900-128">Structures can contain other structures.</span></span> <span data-ttu-id="21900-129">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="21900-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="21900-130">你还可以使用此方法将一个模块中定义的结构封装在另一个模块中定义的结构内。</span><span class="sxs-lookup"><span data-stu-id="21900-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="21900-131">结构可以包含任意深度的其他结构。</span><span class="sxs-lookup"><span data-stu-id="21900-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21900-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="21900-132">See also</span></span>

- [<span data-ttu-id="21900-133">数据类型</span><span class="sxs-lookup"><span data-stu-id="21900-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="21900-134">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="21900-134">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="21900-135">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="21900-135">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="21900-136">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="21900-136">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="21900-137">结构</span><span class="sxs-lookup"><span data-stu-id="21900-137">Structures</span></span>](structures.md)
- [<span data-ttu-id="21900-138">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="21900-138">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="21900-139">如何：声明结构</span><span class="sxs-lookup"><span data-stu-id="21900-139">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="21900-140">结构变量</span><span class="sxs-lookup"><span data-stu-id="21900-140">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="21900-141">结构和类</span><span class="sxs-lookup"><span data-stu-id="21900-141">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="21900-142">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="21900-142">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
