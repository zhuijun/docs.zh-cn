---
title: Me、My、MyBase 和 MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: cc96f39d9dc37b7f1a5d8205e145869fb1b5ecef
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072231"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="9fe4b-102">Visual Basic 中的 Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="9fe4b-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>

<span data-ttu-id="9fe4b-103">`Me`Visual Basic 中，、、 `My` `MyBase` 和的 `MyClass` 名称相似，但用途不同。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="9fe4b-104">本主题将介绍其中的每个实体，以便将它们区分开来。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="9fe4b-105">我</span><span class="sxs-lookup"><span data-stu-id="9fe4b-105">Me</span></span>  

 <span data-ttu-id="9fe4b-106">`Me`关键字提供了一种方法，用于引用当前执行代码的类或结构的特定实例。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="9fe4b-107">`Me` 的行为类似于引用当前实例的对象变量或结构变量。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="9fe4b-108">使用 `Me` 对于将有关当前正在执行的类或结构实例的信息传递给另一个类、结构或模块中的过程特别有用。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="9fe4b-109">例如，假设你在模块中具有以下过程。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="9fe4b-110">可以调用此过程，并 <xref:System.Windows.Forms.Form> 使用以下语句将类的当前实例作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="9fe4b-111">My</span><span class="sxs-lookup"><span data-stu-id="9fe4b-111">My</span></span>  

 <span data-ttu-id="9fe4b-112">此 `My` 功能提供对多个 .NET Framework 类的简单直观的访问，使 Visual Basic 用户可以与计算机、应用程序、设置、资源等交互。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="9fe4b-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="9fe4b-113">MyBase</span></span>  

 <span data-ttu-id="9fe4b-114">`MyBase`关键字的行为类似于引用类的当前实例的基类的对象变量。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="9fe4b-115">`MyBase` 通常用于访问在派生类中被重写或隐藏的基类成员。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="9fe4b-116">`MyBase.New` 用于从派生类构造函数中显式调用基类构造函数。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="9fe4b-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="9fe4b-117">MyClass</span></span>  

 <span data-ttu-id="9fe4b-118">`MyClass`关键字的行为类似于引用最初实现的类的当前实例的对象变量。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="9fe4b-119">`MyClass` 类似于 `Me` ，但其上的所有方法调用都视为方法 `NotOverridable` 。</span><span class="sxs-lookup"><span data-stu-id="9fe4b-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe4b-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="9fe4b-120">See also</span></span>

- [<span data-ttu-id="9fe4b-121">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="9fe4b-121">Inheritance Basics</span></span>](../language-features/objects-and-classes/inheritance-basics.md)
