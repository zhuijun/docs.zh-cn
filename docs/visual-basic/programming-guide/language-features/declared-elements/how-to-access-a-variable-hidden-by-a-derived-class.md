---
title: 如何：访问被派生类隐藏的变量
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392852"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="7db83-102">如何：访问被派生类隐藏的变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db83-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="7db83-103">当派生类中的代码访问某个变量时，编译器通常会将该引用解析为最接近的可访问版本，即，可访问的版本 derivational 从访问类向后翻的步骤。</span><span class="sxs-lookup"><span data-stu-id="7db83-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="7db83-104">如果在派生类中定义了该变量，则代码通常会访问该定义。</span><span class="sxs-lookup"><span data-stu-id="7db83-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="7db83-105">如果派生类变量隐藏了基类中的变量，则会隐藏基类版本。</span><span class="sxs-lookup"><span data-stu-id="7db83-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="7db83-106">但是，您可以通过使用关键字限定基类变量来访问它 `MyBase` 。</span><span class="sxs-lookup"><span data-stu-id="7db83-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="7db83-107">访问由派生类隐藏的基类变量</span><span class="sxs-lookup"><span data-stu-id="7db83-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="7db83-108">在表达式或赋值语句中，在变量名称之前加上 `MyBase` 关键字和一个句点（ `.` ）。</span><span class="sxs-lookup"><span data-stu-id="7db83-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="7db83-109">编译器将引用解析为对变量的基类版本的引用。</span><span class="sxs-lookup"><span data-stu-id="7db83-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="7db83-110">下面的示例演示通过继承进行的隐藏。</span><span class="sxs-lookup"><span data-stu-id="7db83-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="7db83-111">它创建两个引用，一个用于访问隐藏变量，另一个用于绕过隐藏。</span><span class="sxs-lookup"><span data-stu-id="7db83-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="7db83-112">前面的示例声明 `shadowString` 基类中的变量，并将其隐藏在派生类中。</span><span class="sxs-lookup"><span data-stu-id="7db83-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="7db83-113">`showStrings`派生类中的过程在名称不合格时显示字符串的隐藏版本 `shadowString` 。</span><span class="sxs-lookup"><span data-stu-id="7db83-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="7db83-114">当用关键字限定时，它会显示隐藏的版本 `shadowString` `MyBase` 。</span><span class="sxs-lookup"><span data-stu-id="7db83-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="7db83-115">可靠编程</span><span class="sxs-lookup"><span data-stu-id="7db83-115">Robust Programming</span></span>

<span data-ttu-id="7db83-116">为了降低引用隐藏变量的意外版本的风险，可以完全限定对隐藏变量的所有引用。</span><span class="sxs-lookup"><span data-stu-id="7db83-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="7db83-117">隐藏引入了一个具有相同名称的变量的多个版本。</span><span class="sxs-lookup"><span data-stu-id="7db83-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="7db83-118">当代码语句引用变量名时，编译器解析引用的版本取决于一些因素，如代码语句的位置和符合条件的字符串的状态。</span><span class="sxs-lookup"><span data-stu-id="7db83-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="7db83-119">这可能会增加引用错误的变量版本的风险。</span><span class="sxs-lookup"><span data-stu-id="7db83-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="7db83-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7db83-120">See also</span></span>

- [<span data-ttu-id="7db83-121">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="7db83-121">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="7db83-122">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="7db83-122">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="7db83-123">隐藏和重写之间的差异</span><span class="sxs-lookup"><span data-stu-id="7db83-123">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="7db83-124">如何：隐藏与变量同名的变量</span><span class="sxs-lookup"><span data-stu-id="7db83-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="7db83-125">如何：隐藏继承的变量</span><span class="sxs-lookup"><span data-stu-id="7db83-125">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="7db83-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="7db83-126">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="7db83-127">替代</span><span class="sxs-lookup"><span data-stu-id="7db83-127">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="7db83-128">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="7db83-128">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="7db83-129">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="7db83-129">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
