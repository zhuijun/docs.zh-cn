---
title: 自动实现的属性
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: d991a385e537c43daeb708e96e712acd92110379
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403377"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="e6f67-102">自动实现的属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6f67-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="e6f67-103">使用*自动实现的属性*，可以快速指定类的属性，而无需向 `Get` 和属性写入代码 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="e6f67-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="e6f67-104">为自动实现的属性编写代码时，Visual Basic 编译器会自动创建私有字段以存储属性变量，并且会创建关联的 `Get` 和 `Set` 过程。</span><span class="sxs-lookup"><span data-stu-id="e6f67-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="e6f67-105">使用自动实现的属性，可以在单行中声明一个属性（包括默认值）。</span><span class="sxs-lookup"><span data-stu-id="e6f67-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="e6f67-106">下面的示例演示三个属性声明。</span><span class="sxs-lookup"><span data-stu-id="e6f67-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="e6f67-107">自动实现的属性等效于其属性值存储在私有字段中的属性。</span><span class="sxs-lookup"><span data-stu-id="e6f67-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="e6f67-108">下面的代码示例演示一个自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="e6f67-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="e6f67-109">下面的代码示例演示上面自动实现的属性示例的等效代码。</span><span class="sxs-lookup"><span data-stu-id="e6f67-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="e6f67-110">以下代码演示如何实现只读属性：</span><span class="sxs-lookup"><span data-stu-id="e6f67-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="e6f67-111">可以使用初始化表达式分配给属性（如示例中所示），也可以在包含类型的构造函数中分配给属性。</span><span class="sxs-lookup"><span data-stu-id="e6f67-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="e6f67-112">可以随时分配给只读属性的支持字段。</span><span class="sxs-lookup"><span data-stu-id="e6f67-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="e6f67-113">支持字段</span><span class="sxs-lookup"><span data-stu-id="e6f67-113">Backing Field</span></span>  
 <span data-ttu-id="e6f67-114">当你声明自动实现的属性时，Visual Basic 会自动创建一个名为 "*支持" 字段*的隐藏私有字段来包含属性值。</span><span class="sxs-lookup"><span data-stu-id="e6f67-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="e6f67-115">支持字段名是前面带下划线 (_) 的自动实现的属性名。</span><span class="sxs-lookup"><span data-stu-id="e6f67-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="e6f67-116">例如，如果声明一个名为 `ID` 的自动实现的属性，则支持字段名为 `_ID`。</span><span class="sxs-lookup"><span data-stu-id="e6f67-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="e6f67-117">如果包含一个也名为 `_ID` 的类成员，则会形成命名冲突，Visual Basic 会报告编译器错误。</span><span class="sxs-lookup"><span data-stu-id="e6f67-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="e6f67-118">支持字段还具有下列特征：</span><span class="sxs-lookup"><span data-stu-id="e6f67-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="e6f67-119">支持字段的访问修饰符始终是 `Private`，即使在属性本身具有不同访问级别（如 `Public`）时也是如此。</span><span class="sxs-lookup"><span data-stu-id="e6f67-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="e6f67-120">如果属性标记为 `Shared`，则支持字段也进行共享。</span><span class="sxs-lookup"><span data-stu-id="e6f67-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="e6f67-121">为属性指定的属性不适用于支持字段。</span><span class="sxs-lookup"><span data-stu-id="e6f67-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="e6f67-122">可以从类中的代码以及从调试工具（如监视窗口）访问支持字段。</span><span class="sxs-lookup"><span data-stu-id="e6f67-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="e6f67-123">但是，支持字段不显示在 IntelliSense 文字自动完成列表中。</span><span class="sxs-lookup"><span data-stu-id="e6f67-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="e6f67-124">初始化自动实现的属性</span><span class="sxs-lookup"><span data-stu-id="e6f67-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="e6f67-125">任何可以用于实例化字段的表达式对于初始化自动实现的属性都是有效的。</span><span class="sxs-lookup"><span data-stu-id="e6f67-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="e6f67-126">初始化自动实现的属性时，表达式会进行计算并传递给属性的 `Set` 过程。</span><span class="sxs-lookup"><span data-stu-id="e6f67-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="e6f67-127">下面的代码示例演示一些包含初始值的自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="e6f67-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="e6f67-128">无法初始化作为 `Interface` 的成员或标记为 `MustOverride` 的自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="e6f67-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="e6f67-129">将自动实现的属性声明为 `Structure` 的成员时，如果自动实现的属性标记为 `Shared`，则只能初始化它。</span><span class="sxs-lookup"><span data-stu-id="e6f67-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="e6f67-130">将自动实现的属性声明为数组时，不能指定显式数组边界。</span><span class="sxs-lookup"><span data-stu-id="e6f67-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="e6f67-131">但是，可以使用数组初始值设定项提供值，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="e6f67-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="e6f67-132">需要标准语法的属性定义</span><span class="sxs-lookup"><span data-stu-id="e6f67-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="e6f67-133">自动实现的属性十分方便，支持很多编程方案。</span><span class="sxs-lookup"><span data-stu-id="e6f67-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="e6f67-134">但是，在某些情况下，你不能使用自动实现的属性，而是必须使用标准或*扩展*的属性语法。</span><span class="sxs-lookup"><span data-stu-id="e6f67-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="e6f67-135">如果要执行以下任一操作，则必须使用扩展属性定义语法：</span><span class="sxs-lookup"><span data-stu-id="e6f67-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="e6f67-136">向属性的 `Get` 或 `Set` 过程添加代码，如用于在 `Set` 过程中验证传入值的代码。</span><span class="sxs-lookup"><span data-stu-id="e6f67-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="e6f67-137">例如，你可能要在设置属性值之前验证表示电话号码的字符串是否包含所需数量的数字。</span><span class="sxs-lookup"><span data-stu-id="e6f67-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="e6f67-138">为 `Get` 和 `Set` 过程指定不同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="e6f67-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="e6f67-139">例如，你可能要使 `Set` 过程是 `Private`，要使 `Get` 过程是 `Public`。</span><span class="sxs-lookup"><span data-stu-id="e6f67-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="e6f67-140">创建作为 `WriteOnly` 的属性。</span><span class="sxs-lookup"><span data-stu-id="e6f67-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="e6f67-141">使用参数化的属性（包括 `Default` 属性）。</span><span class="sxs-lookup"><span data-stu-id="e6f67-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="e6f67-142">必须声明扩展属性才能为属性指定参数或是为 `Set` 过程指定附加参数。</span><span class="sxs-lookup"><span data-stu-id="e6f67-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="e6f67-143">将属性置于支持字段上，或更改支持字段的访问级别。</span><span class="sxs-lookup"><span data-stu-id="e6f67-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="e6f67-144">为支持字段提供 XML 注释。</span><span class="sxs-lookup"><span data-stu-id="e6f67-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="e6f67-145">扩展自动实现的属性</span><span class="sxs-lookup"><span data-stu-id="e6f67-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="e6f67-146">如果需要将自动实现的属性转换为包含 `Get` 或 `Set` 过程的展开属性，则 Visual Basic 代码编辑器可以为属性自动生成 `Get` 和 `Set` 过程以及 `End Property` 语句。</span><span class="sxs-lookup"><span data-stu-id="e6f67-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="e6f67-147">如果将光标置于语句后面的空行上 `Property` ，请键入 `G` （对于 `Get` ）或 `S` （对于 `Set` ），然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="e6f67-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="e6f67-148">在 `Property` 语句末尾按 Enter 时，Visual Basic 代码编辑器会为只读和只写属性自动生成 `Get` 或 `Set` 过程。</span><span class="sxs-lookup"><span data-stu-id="e6f67-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f67-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6f67-149">See also</span></span>

- [<span data-ttu-id="e6f67-150">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="e6f67-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="e6f67-151">如何：声明具有混合访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="e6f67-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="e6f67-152">Property Statement</span><span class="sxs-lookup"><span data-stu-id="e6f67-152">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="e6f67-153">只读</span><span class="sxs-lookup"><span data-stu-id="e6f67-153">ReadOnly</span></span>](../../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="e6f67-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="e6f67-154">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="e6f67-155">对象和类</span><span class="sxs-lookup"><span data-stu-id="e6f67-155">Objects and Classes</span></span>](../objects-and-classes/index.md)
