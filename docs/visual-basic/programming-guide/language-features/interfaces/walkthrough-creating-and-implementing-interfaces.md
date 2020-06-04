---
title: 创建和实现接口
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 89e8f91a04b25b84bc783d5c4f4b91cf12426f72
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405062"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="3ee17-102">演练：创建和实现接口 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ee17-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="3ee17-103">接口描述属性、方法和事件的特征，但使实现详细信息保留在结构或类中。</span><span class="sxs-lookup"><span data-stu-id="3ee17-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="3ee17-104">本演练演示如何声明和实现接口。</span><span class="sxs-lookup"><span data-stu-id="3ee17-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ee17-105">本演练不提供有关如何创建用户界面的信息。</span><span class="sxs-lookup"><span data-stu-id="3ee17-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="3ee17-106">定义接口</span><span class="sxs-lookup"><span data-stu-id="3ee17-106">To define an interface</span></span>
  
1. <span data-ttu-id="3ee17-107">打开一个新的 Visual Basic Windows 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="3ee17-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="3ee17-108">通过单击 "**项目**" 菜单上的 "**添加模块**"，将新模块添加到项目。</span><span class="sxs-lookup"><span data-stu-id="3ee17-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="3ee17-109">将新模块命名为 `Module1.vb` ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="3ee17-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="3ee17-110">新模块的代码随即显示。</span><span class="sxs-lookup"><span data-stu-id="3ee17-110">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="3ee17-111">`TestInterface` `Module1` 通过在 `Interface TestInterface` `Module` 和语句之间键入，然后 `End Module` 按 enter，在中定义名为的接口。</span><span class="sxs-lookup"><span data-stu-id="3ee17-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="3ee17-112">**代码编辑器**会缩进 `Interface` 关键字并添加 `End Interface` 语句来形成代码块。</span><span class="sxs-lookup"><span data-stu-id="3ee17-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="3ee17-113">通过在和语句之间放置以下代码，为接口定义属性、方法和事件 `Interface` `End Interface` ：</span><span class="sxs-lookup"><span data-stu-id="3ee17-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="3ee17-114">实现</span><span class="sxs-lookup"><span data-stu-id="3ee17-114">Implementation</span></span>

 <span data-ttu-id="3ee17-115">你可能会注意到，用于声明接口成员的语法不同于用于声明类成员的语法。</span><span class="sxs-lookup"><span data-stu-id="3ee17-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="3ee17-116">这种差异反映了接口不能包含实现代码这一事实。</span><span class="sxs-lookup"><span data-stu-id="3ee17-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="3ee17-117">实现接口</span><span class="sxs-lookup"><span data-stu-id="3ee17-117">To implement the interface</span></span>
  
1. <span data-ttu-id="3ee17-118">添加一个名为 `ImplementationClass` 的类，方法是将以下语句添加到 `Module1` ，在 `End Interface` 语句后面但在语句之前，然后 `End Module` 按 enter：</span><span class="sxs-lookup"><span data-stu-id="3ee17-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="3ee17-119">如果在集成开发环境中工作，则按 ENTER 时，**代码编辑器**将提供一个匹配的 `End Class` 语句。</span><span class="sxs-lookup"><span data-stu-id="3ee17-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="3ee17-120">将以下 `Implements` 语句添加到 `ImplementationClass` ，命名类实现的接口：</span><span class="sxs-lookup"><span data-stu-id="3ee17-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="3ee17-121">当与类或结构顶部的其他项分开列出时， `Implements` 语句指示类或结构实现接口。</span><span class="sxs-lookup"><span data-stu-id="3ee17-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="3ee17-122">如果你在集成开发环境中工作，则在按下 ENTER 键时，**代码编辑器**将实现所需的类成员， `TestInterface` 并且你可以跳过下一步。</span><span class="sxs-lookup"><span data-stu-id="3ee17-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="3ee17-123">如果未在集成开发环境中工作，则必须实现该接口的所有成员 `MyInterface` 。</span><span class="sxs-lookup"><span data-stu-id="3ee17-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="3ee17-124">将以下代码添加到以 `ImplementationClass` 实现 `Event1` 、 `Method1` 和 `Prop1` ：</span><span class="sxs-lookup"><span data-stu-id="3ee17-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="3ee17-125">`Implements`语句命名要实现的接口和接口成员。</span><span class="sxs-lookup"><span data-stu-id="3ee17-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="3ee17-126">完成的定义， `Prop1` 方法是将私有字段添加到存储属性值的类：</span><span class="sxs-lookup"><span data-stu-id="3ee17-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="3ee17-127">`pval`从属性 get 访问器返回的值。</span><span class="sxs-lookup"><span data-stu-id="3ee17-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="3ee17-128">`pval`在属性集访问器中设置的值。</span><span class="sxs-lookup"><span data-stu-id="3ee17-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="3ee17-129">`Method1`通过添加以下代码完成的定义。</span><span class="sxs-lookup"><span data-stu-id="3ee17-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="3ee17-130">测试接口的实现</span><span class="sxs-lookup"><span data-stu-id="3ee17-130">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="3ee17-131">右键单击 "**解决方案资源管理器**中项目的启动窗体，然后单击"**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="3ee17-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="3ee17-132">编辑器显示您的启动窗体的类。</span><span class="sxs-lookup"><span data-stu-id="3ee17-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="3ee17-133">默认情况下，将调用启动窗体 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="3ee17-133">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="3ee17-134">将以下 `testInstance` 字段添加到 `Form1` 类：</span><span class="sxs-lookup"><span data-stu-id="3ee17-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="3ee17-135">通过将声明 `testInstance` 为 `WithEvents` ， `Form1` 类可处理其事件。</span><span class="sxs-lookup"><span data-stu-id="3ee17-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="3ee17-136">向类添加以下事件处理程序 `Form1` ，以处理引发的事件 `testInstance` ：</span><span class="sxs-lookup"><span data-stu-id="3ee17-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="3ee17-137">将名 `Test` 为的子程序添加到 `Form1` 类，以测试实现类：</span><span class="sxs-lookup"><span data-stu-id="3ee17-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="3ee17-138">此 `Test` 过程创建实现的类的一个实例 `MyInterface` ，将该实例分配给该 `testInstance` 字段，设置一个属性，然后通过接口运行方法。</span><span class="sxs-lookup"><span data-stu-id="3ee17-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="3ee17-139">添加代码以 `Test` 从 `Form1 Load` 启动窗体的过程调用过程：</span><span class="sxs-lookup"><span data-stu-id="3ee17-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="3ee17-140">`Test`按 F5 运行该过程。</span><span class="sxs-lookup"><span data-stu-id="3ee17-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="3ee17-141">将显示消息 "Prop1 已设置为 9"。</span><span class="sxs-lookup"><span data-stu-id="3ee17-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="3ee17-142">单击 "确定" 后，将显示消息 "Method1 的 X 参数是 5"。</span><span class="sxs-lookup"><span data-stu-id="3ee17-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="3ee17-143">单击 "确定"，将显示消息 "事件处理程序捕获到事件"。</span><span class="sxs-lookup"><span data-stu-id="3ee17-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee17-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ee17-144">See also</span></span>

- [<span data-ttu-id="3ee17-145">Implements 语句</span><span class="sxs-lookup"><span data-stu-id="3ee17-145">Implements Statement</span></span>](../../../language-reference/statements/implements-statement.md)
- [<span data-ttu-id="3ee17-146">接口</span><span class="sxs-lookup"><span data-stu-id="3ee17-146">Interfaces</span></span>](index.md)
- [<span data-ttu-id="3ee17-147">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="3ee17-147">Interface Statement</span></span>](../../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="3ee17-148">Event 语句</span><span class="sxs-lookup"><span data-stu-id="3ee17-148">Event Statement</span></span>](../../../language-reference/statements/event-statement.md)
