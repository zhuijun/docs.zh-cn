---
title: 变量和自变量
description: 本文介绍变量，这些变量表示数据的存储和自变量，这些变量表示与 Workflow Foundation 中的活动之间的数据流。
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 5cce9931e9b0a37d5fafbfb84527ffd543a0a50f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201946"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="eb10e-103">变量和自变量</span><span class="sxs-lookup"><span data-stu-id="eb10e-103">Variables and Arguments</span></span>
<span data-ttu-id="eb10e-104">在 Windows Workflow Foundation （WF）中，变量表示数据的存储，参数表示流入和流出活动的数据流。</span><span class="sxs-lookup"><span data-stu-id="eb10e-104">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="eb10e-105">活动拥有一组自变量，这些自变量构成活动的签名。</span><span class="sxs-lookup"><span data-stu-id="eb10e-105">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="eb10e-106">此外，活动可以维护一个变量列表，在工作流设计期间，开发人员可在该列表中添加或移除变量。</span><span class="sxs-lookup"><span data-stu-id="eb10e-106">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="eb10e-107">使用可返回值的表达式可以绑定参数。</span><span class="sxs-lookup"><span data-stu-id="eb10e-107">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="eb10e-108">变量</span><span class="sxs-lookup"><span data-stu-id="eb10e-108">Variables</span></span>  
 <span data-ttu-id="eb10e-109">变量是数据的存储位置。</span><span class="sxs-lookup"><span data-stu-id="eb10e-109">Variables are storage locations for data.</span></span> <span data-ttu-id="eb10e-110">变量被声明为工作流定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="eb10e-110">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="eb10e-111">变量在运行时获取值，并将这些值存储为工作流实例状态的一部分。</span><span class="sxs-lookup"><span data-stu-id="eb10e-111">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="eb10e-112">变量定义指定了变量的类型，如果需要，还可指定变量的名称。</span><span class="sxs-lookup"><span data-stu-id="eb10e-112">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="eb10e-113">以下代码演示如何声明变量，使用 <xref:System.Activities.Statements.Assign%601> 活动为变量赋值，然后使用 <xref:System.Activities.Statements.WriteLine> 活动将其值显示在控制台上。</span><span class="sxs-lookup"><span data-stu-id="eb10e-113">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="eb10e-114">可根据需要将默认值表达式指定为变量声明的一部分。</span><span class="sxs-lookup"><span data-stu-id="eb10e-114">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="eb10e-115">变量还可具有修饰符。</span><span class="sxs-lookup"><span data-stu-id="eb10e-115">Variables also can have modifiers.</span></span> <span data-ttu-id="eb10e-116">例如，如果某个变量为只读变量，则可应用只读 <xref:System.Activities.VariableModifiers> 修饰符。</span><span class="sxs-lookup"><span data-stu-id="eb10e-116">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="eb10e-117">在以下示例中，创建具有指定默认值的只读变量。</span><span class="sxs-lookup"><span data-stu-id="eb10e-117">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="eb10e-118">变量的作用域</span><span class="sxs-lookup"><span data-stu-id="eb10e-118">Variable Scoping</span></span>  
 <span data-ttu-id="eb10e-119">变量在运行时的生存期与声明该变量的活动的生存期相同。</span><span class="sxs-lookup"><span data-stu-id="eb10e-119">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="eb10e-120">活动完成后，其变量将被清除，并且无法再引用。</span><span class="sxs-lookup"><span data-stu-id="eb10e-120">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="eb10e-121">自变量</span><span class="sxs-lookup"><span data-stu-id="eb10e-121">Arguments</span></span>  
 <span data-ttu-id="eb10e-122">活动作者使用参数来定义数据流入流出活动的方式。</span><span class="sxs-lookup"><span data-stu-id="eb10e-122">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="eb10e-123">每个自变量都有特定的方向：<xref:System.Activities.ArgumentDirection.In>、<xref:System.Activities.ArgumentDirection.Out>、或 <xref:System.Activities.ArgumentDirection.InOut>。</span><span class="sxs-lookup"><span data-stu-id="eb10e-123">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="eb10e-124">工作流运行时对数据流入流出活动的时间有以下保证：</span><span class="sxs-lookup"><span data-stu-id="eb10e-124">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="eb10e-125">活动开始执行时，将计算其所有输入和输入/输出参数的值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-125">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="eb10e-126">例如，不管何时调用 <xref:System.Activities.Argument.Get%2A>，返回值都为调用 `Execute` 之前运行时所计算的值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-126">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="eb10e-127">调用 <xref:System.Activities.InOutArgument%601.Set%2A> 时，运行时将立即设置值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-127">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="eb10e-128">可根据需要指定自变量的 <xref:System.Activities.Argument.EvaluationOrder%2A>。</span><span class="sxs-lookup"><span data-stu-id="eb10e-128">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="eb10e-129"><xref:System.Activities.Argument.EvaluationOrder%2A> 是指定自变量计算顺序的从零开始的值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-129"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="eb10e-130">默认情况下，自变量的计算顺序未指定且等于 <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> 值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-130">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="eb10e-131">将 <xref:System.Activities.Argument.EvaluationOrder%2A> 设置为一个大于或等于零的值，以便为此自变量指定一个计算顺序。</span><span class="sxs-lookup"><span data-stu-id="eb10e-131">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="eb10e-132">Windows Workflow Foundation 按指定的计算顺序按升序计算参数。</span><span class="sxs-lookup"><span data-stu-id="eb10e-132">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="eb10e-133">注意：未指定计算顺序的参数将先于指定计算顺序的参数计算。</span><span class="sxs-lookup"><span data-stu-id="eb10e-133">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="eb10e-134">活动作者可以使用强类型机制来公开其参数。</span><span class="sxs-lookup"><span data-stu-id="eb10e-134">An activity author can use a strongly typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="eb10e-135">实现方法是声明 <xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 和 <xref:System.Activities.InOutArgument%601> 类型的属性。</span><span class="sxs-lookup"><span data-stu-id="eb10e-135">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="eb10e-136">这允许活动作者建立有关流入流出活动的数据的特定协定。</span><span class="sxs-lookup"><span data-stu-id="eb10e-136">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="eb10e-137">定义活动的自变量</span><span class="sxs-lookup"><span data-stu-id="eb10e-137">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="eb10e-138">可通过指定 <xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601> 和 <xref:System.Activities.InOutArgument%601> 类型的属性来定义活动的自变量。</span><span class="sxs-lookup"><span data-stu-id="eb10e-138">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="eb10e-139">以下代码演示如何为 `Prompt` 活动定义参数，该活动接收一个字符串以显示给用户，并返回包含用户响应的字符串。</span><span class="sxs-lookup"><span data-stu-id="eb10e-139">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="eb10e-140">返回单个值的活动可从 <xref:System.Activities.Activity%601>、<xref:System.Activities.NativeActivity%601> 或 <xref:System.Activities.CodeActivity%601> 派生。</span><span class="sxs-lookup"><span data-stu-id="eb10e-140">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="eb10e-141">这些活动拥有定义完善的名为 <xref:System.Activities.OutArgument%601> 的 <xref:System.Activities.Activity%601.Result%2A>，它包含活动的返回值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-141">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="eb10e-142">在工作流中使用变量和自变量</span><span class="sxs-lookup"><span data-stu-id="eb10e-142">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="eb10e-143">以下示例演示如何在工作流中使用变量和自变量。</span><span class="sxs-lookup"><span data-stu-id="eb10e-143">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="eb10e-144">该工作流是一个声明三个变量：`var1`、`var2` 和 `var3` 的序列。</span><span class="sxs-lookup"><span data-stu-id="eb10e-144">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="eb10e-145">该工作流中的第一个活动是 `Assign` 活动，它将变量 `var1` 的值赋给变量 `var2`。</span><span class="sxs-lookup"><span data-stu-id="eb10e-145">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="eb10e-146">接下来是 `WriteLine` 活动，该活动打印 `var2` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-146">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="eb10e-147">之后是另一个 `Assign` 活动，该活动将变量 `var2` 的值赋给变量 `var3`。</span><span class="sxs-lookup"><span data-stu-id="eb10e-147">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="eb10e-148">最后是另一个 `WriteLine` 活动，该活动打印 `var3` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="eb10e-148">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="eb10e-149">第一个 `Assign` 活动使用 `InArgument<string>` 和 `OutArgument<string>` 对象，显式表示对活动自变量的绑定。</span><span class="sxs-lookup"><span data-stu-id="eb10e-149">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="eb10e-150">将 `InArgument<string>` 用于 <xref:System.Activities.Statements.Assign.Value%2A> 是因为值通过其 <xref:System.Activities.Statements.Assign%601> 自变量流入 <xref:System.Activities.Statements.Assign.Value%2A> 活动，而将 `OutArgument<string>` 用于 <xref:System.Activities.Statements.Assign.To%2A> 是因为值从 <xref:System.Activities.Statements.Assign.To%2A> 自变量流出而赋给变量。</span><span class="sxs-lookup"><span data-stu-id="eb10e-150">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="eb10e-151">第二个 `Assign` 活动完成相同的操作，它采用更加紧凑的语法，通过使用隐式强制转换而达到相同目的。</span><span class="sxs-lookup"><span data-stu-id="eb10e-151">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="eb10e-152">`WriteLine` 活动也使用紧凑语法。</span><span class="sxs-lookup"><span data-stu-id="eb10e-152">The `WriteLine` activities also use the compact syntax.</span></span>  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="eb10e-153">在基于代码的活动中使用变量和参数</span><span class="sxs-lookup"><span data-stu-id="eb10e-153">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="eb10e-154">先前的示例演示如何在工作流和声明性活动中使用自变量和变量。</span><span class="sxs-lookup"><span data-stu-id="eb10e-154">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="eb10e-155">自变量和变量也用在基于代码的活动中。</span><span class="sxs-lookup"><span data-stu-id="eb10e-155">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="eb10e-156">从概念上来说，二者的使用非常相似。</span><span class="sxs-lookup"><span data-stu-id="eb10e-156">Conceptually the usage is very similar.</span></span> <span data-ttu-id="eb10e-157">变量表示活动中的数据存储区，而自变量表示流入或流出活动的数据，二者由工作流作者绑定到工作流中表示数据流至或流出位置的其他变量或自变量。</span><span class="sxs-lookup"><span data-stu-id="eb10e-157">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="eb10e-158">若要获取或设置活动中的变量或参数的值，必须使用表示该活动当前执行环境的活动上下文。</span><span class="sxs-lookup"><span data-stu-id="eb10e-158">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="eb10e-159">活动上下文由工作流运行时传入活动的 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="eb10e-159">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="eb10e-160">在本示例中，为自定义 `Add` 活动定义了两个 <xref:System.Activities.ArgumentDirection.In> 参数。</span><span class="sxs-lookup"><span data-stu-id="eb10e-160">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="eb10e-161">为了访问这些自变量的值，使用了 <xref:System.Activities.Argument.Get%2A> 方法，并使用了由工作流运行时传入的上下文。</span><span class="sxs-lookup"><span data-stu-id="eb10e-161">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="eb10e-162">有关在代码中使用参数、变量和表达式的详细信息，请参阅使用命令性代码和[必需的参数和重载组](required-arguments-and-overload-groups.md)[创作工作流、活动和表达式](authoring-workflows-activities-and-expressions-using-imperative-code.md)。</span><span class="sxs-lookup"><span data-stu-id="eb10e-162">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
