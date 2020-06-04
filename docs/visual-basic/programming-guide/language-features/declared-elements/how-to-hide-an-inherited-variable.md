---
title: 如何：隐藏继承的变量
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: f49bba0497f9f4f2774b01284c815bba9aaed119
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357265"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="30963-102">如何：隐藏继承的变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30963-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>

<span data-ttu-id="30963-103">派生类继承其基类的所有定义。</span><span class="sxs-lookup"><span data-stu-id="30963-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="30963-104">如果要使用与基类元素相同的名称来定义变量，则可以在派生类中定义变量时*隐藏或隐藏*该基类元素。</span><span class="sxs-lookup"><span data-stu-id="30963-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="30963-105">如果执行此操作，派生类中的代码将访问你的变量，除非它显式跳过隐藏机制。</span><span class="sxs-lookup"><span data-stu-id="30963-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>

<span data-ttu-id="30963-106">您可能想要隐藏继承的变量的另一个原因是为了防止基类修订。</span><span class="sxs-lookup"><span data-stu-id="30963-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="30963-107">基类可能会改变要继承的元素。</span><span class="sxs-lookup"><span data-stu-id="30963-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="30963-108">如果发生这种情况，则 `Shadows` 修饰符强制将派生类中的引用解析为你的变量，而不是基类元素。</span><span class="sxs-lookup"><span data-stu-id="30963-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>

## <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="30963-109">隐藏继承的变量</span><span class="sxs-lookup"><span data-stu-id="30963-109">To hide an inherited variable</span></span>

1. <span data-ttu-id="30963-110">确保要隐藏的变量是在类级别（在任何过程外部）声明的。</span><span class="sxs-lookup"><span data-stu-id="30963-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="30963-111">否则，你无需隐藏它。</span><span class="sxs-lookup"><span data-stu-id="30963-111">Otherwise, you do not need to hide it.</span></span>
  
2. <span data-ttu-id="30963-112">在派生类中，编写声明变量的[Dim 语句](../../../language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="30963-112">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="30963-113">使用与继承变量相同的名称。</span><span class="sxs-lookup"><span data-stu-id="30963-113">Use the same name as that of the inherited variable.</span></span>

3. <span data-ttu-id="30963-114">在声明中包含[Shadows](../../../language-reference/modifiers/shadows.md)关键字。</span><span class="sxs-lookup"><span data-stu-id="30963-114">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

     <span data-ttu-id="30963-115">当派生类中的代码引用变量名时，编译器会将对变量的引用解析为。</span><span class="sxs-lookup"><span data-stu-id="30963-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

     <span data-ttu-id="30963-116">下面的示例说明了继承变量的隐藏：</span><span class="sxs-lookup"><span data-stu-id="30963-116">The following example illustrates shadowing of an inherited variable:</span></span>
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="30963-117">前面的示例声明 `shadowString` 基类中的变量，并将其隐藏在派生类中。</span><span class="sxs-lookup"><span data-stu-id="30963-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="30963-118">`ShowStrings`派生类中的过程在名称不合格时显示字符串的隐藏版本 `shadowString` 。</span><span class="sxs-lookup"><span data-stu-id="30963-118">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="30963-119">当用关键字限定时，它会显示隐藏的版本 `shadowString` `MyBase` 。</span><span class="sxs-lookup"><span data-stu-id="30963-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="30963-120">可靠编程</span><span class="sxs-lookup"><span data-stu-id="30963-120">Robust programming</span></span>

<span data-ttu-id="30963-121">隐藏引入了一个具有相同名称的变量的多个版本。</span><span class="sxs-lookup"><span data-stu-id="30963-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="30963-122">当代码语句引用变量名时，编译器解析引用的版本取决于一些因素，如代码语句的位置和符合条件的字符串的状态。</span><span class="sxs-lookup"><span data-stu-id="30963-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="30963-123">这可能会增加引用隐藏变量的意外版本的风险。</span><span class="sxs-lookup"><span data-stu-id="30963-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="30963-124">您可以通过完全限定对隐藏变量的所有引用来降低风险。</span><span class="sxs-lookup"><span data-stu-id="30963-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="30963-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30963-125">See also</span></span>

- [<span data-ttu-id="30963-126">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="30963-126">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="30963-127">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="30963-127">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="30963-128">隐藏和重写之间的差异</span><span class="sxs-lookup"><span data-stu-id="30963-128">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="30963-129">如何：隐藏与变量同名的变量</span><span class="sxs-lookup"><span data-stu-id="30963-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="30963-130">如何：访问被派生类隐藏的变量</span><span class="sxs-lookup"><span data-stu-id="30963-130">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="30963-131">替代</span><span class="sxs-lookup"><span data-stu-id="30963-131">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="30963-132">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="30963-132">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="30963-133">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="30963-133">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
