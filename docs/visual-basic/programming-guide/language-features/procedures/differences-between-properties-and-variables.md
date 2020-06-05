---
title: 属性和变量之间的差异
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: 162bd71eaebdf55f6be89e0c5dce7acc1b975d79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403299"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a><span data-ttu-id="48f38-102">Visual Basic 中属性和变量的差异</span><span class="sxs-lookup"><span data-stu-id="48f38-102">Differences Between Properties and Variables in Visual Basic</span></span>
<span data-ttu-id="48f38-103">变量和属性都表示可以访问的值。</span><span class="sxs-lookup"><span data-stu-id="48f38-103">Variables and properties both represent values that you can access.</span></span> <span data-ttu-id="48f38-104">但在存储和实现方面存在差异。</span><span class="sxs-lookup"><span data-stu-id="48f38-104">However, there are differences in storage and implementation.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="48f38-105">变量</span><span class="sxs-lookup"><span data-stu-id="48f38-105">Variables</span></span>  
 <span data-ttu-id="48f38-106">*变量*直接对应于内存位置。</span><span class="sxs-lookup"><span data-stu-id="48f38-106">A *variable* corresponds directly to a memory location.</span></span> <span data-ttu-id="48f38-107">使用单个声明语句定义变量。</span><span class="sxs-lookup"><span data-stu-id="48f38-107">You define a variable with a single declaration statement.</span></span> <span data-ttu-id="48f38-108">变量可以是在过程中定义的*本地变量*，只能在该过程中使用，也可以是在模块、类或结构中定义但不在任何过程内的*成员变量*。</span><span class="sxs-lookup"><span data-stu-id="48f38-108">A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure.</span></span> <span data-ttu-id="48f38-109">成员变量也称为*字段*。</span><span class="sxs-lookup"><span data-stu-id="48f38-109">A member variable is also called a *field*.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="48f38-110">属性</span><span class="sxs-lookup"><span data-stu-id="48f38-110">Properties</span></span>  
 <span data-ttu-id="48f38-111">*属性*是在模块、类或结构上定义的数据元素。</span><span class="sxs-lookup"><span data-stu-id="48f38-111">A *property* is a data element defined on a module, class, or structure.</span></span> <span data-ttu-id="48f38-112">使用和语句之间的代码块定义属性 `Property` `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="48f38-112">You define a property with a code block between the `Property` and `End Property` statements.</span></span> <span data-ttu-id="48f38-113">代码块包含 `Get` 过程和 `Set` /或过程。</span><span class="sxs-lookup"><span data-stu-id="48f38-113">The code block contains a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="48f38-114">这些过程称为*属性过程*或*属性访问器*。</span><span class="sxs-lookup"><span data-stu-id="48f38-114">These procedures are called *property procedures* or *property accessors*.</span></span> <span data-ttu-id="48f38-115">除了检索或存储属性值以外，还可以执行自定义操作，如更新访问计数器。</span><span class="sxs-lookup"><span data-stu-id="48f38-115">In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="48f38-116">差异</span><span class="sxs-lookup"><span data-stu-id="48f38-116">Differences</span></span>  
 <span data-ttu-id="48f38-117">下表显示了变量和属性之间的一些重要差异。</span><span class="sxs-lookup"><span data-stu-id="48f38-117">The following table shows some important differences between variables and properties.</span></span>  
  
|<span data-ttu-id="48f38-118">差异点</span><span class="sxs-lookup"><span data-stu-id="48f38-118">Point of difference</span></span>|<span data-ttu-id="48f38-119">变量</span><span class="sxs-lookup"><span data-stu-id="48f38-119">Variable</span></span>|<span data-ttu-id="48f38-120">Property</span><span class="sxs-lookup"><span data-stu-id="48f38-120">Property</span></span>|  
|-------------------------|--------------|--------------|  
|<span data-ttu-id="48f38-121">声明</span><span class="sxs-lookup"><span data-stu-id="48f38-121">Declaration</span></span>|<span data-ttu-id="48f38-122">单个声明语句</span><span class="sxs-lookup"><span data-stu-id="48f38-122">Single declaration statement</span></span>|<span data-ttu-id="48f38-123">代码块中的一系列语句</span><span class="sxs-lookup"><span data-stu-id="48f38-123">Series of statements in a code block</span></span>|  
|<span data-ttu-id="48f38-124">实现</span><span class="sxs-lookup"><span data-stu-id="48f38-124">Implementation</span></span>|<span data-ttu-id="48f38-125">单个存储位置</span><span class="sxs-lookup"><span data-stu-id="48f38-125">Single storage location</span></span>|<span data-ttu-id="48f38-126">可执行代码（属性过程）</span><span class="sxs-lookup"><span data-stu-id="48f38-126">Executable code (property procedures)</span></span>|  
|<span data-ttu-id="48f38-127">存储</span><span class="sxs-lookup"><span data-stu-id="48f38-127">Storage</span></span>|<span data-ttu-id="48f38-128">直接与变量的值关联</span><span class="sxs-lookup"><span data-stu-id="48f38-128">Directly associated with variable's value</span></span>|<span data-ttu-id="48f38-129">通常，内部存储在属性的包含类或模块外部不可用</span><span class="sxs-lookup"><span data-stu-id="48f38-129">Typically has internal storage not available outside the property's containing class or module</span></span><br /><br /> <span data-ttu-id="48f38-130">属性的值不能作为存储元素<sup>1</sup>存在，也可能不存在。</span><span class="sxs-lookup"><span data-stu-id="48f38-130">Property's value might or might not exist as a stored element <sup>1</sup></span></span>|  
|<span data-ttu-id="48f38-131">可执行代码</span><span class="sxs-lookup"><span data-stu-id="48f38-131">Executable code</span></span>|<span data-ttu-id="48f38-132">无</span><span class="sxs-lookup"><span data-stu-id="48f38-132">None</span></span>|<span data-ttu-id="48f38-133">必须至少有一个过程</span><span class="sxs-lookup"><span data-stu-id="48f38-133">Must have at least one procedure</span></span>|  
|<span data-ttu-id="48f38-134">读写访问权限</span><span class="sxs-lookup"><span data-stu-id="48f38-134">Read and write access</span></span>|<span data-ttu-id="48f38-135">读/写或只读</span><span class="sxs-lookup"><span data-stu-id="48f38-135">Read/write or read-only</span></span>|<span data-ttu-id="48f38-136">读/写、只读或只写</span><span class="sxs-lookup"><span data-stu-id="48f38-136">Read/write, read-only, or write-only</span></span>|  
|<span data-ttu-id="48f38-137">自定义操作（除了接受或返回值之外）</span><span class="sxs-lookup"><span data-stu-id="48f38-137">Custom actions (in addition to accepting or returning value)</span></span>|<span data-ttu-id="48f38-138">不可用</span><span class="sxs-lookup"><span data-stu-id="48f38-138">Not possible</span></span>|<span data-ttu-id="48f38-139">可以在设置或检索属性值的过程中执行</span><span class="sxs-lookup"><span data-stu-id="48f38-139">Can be performed as part of setting or retrieving property value</span></span>|  
  
 <span data-ttu-id="48f38-140"><sup>1</sup>与变量不同，属性的值可能不会直接对应于单个存储项。</span><span class="sxs-lookup"><span data-stu-id="48f38-140"><sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage.</span></span> <span data-ttu-id="48f38-141">为了方便或安全，存储区可能会拆分为若干个部分，或者值可能以加密形式存储。</span><span class="sxs-lookup"><span data-stu-id="48f38-141">The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form.</span></span> <span data-ttu-id="48f38-142">在这些情况下，该 `Get` 过程会组装部分或解密存储的值，并且该 `Set` 过程将加密新值或将其拆分为构成存储。</span><span class="sxs-lookup"><span data-stu-id="48f38-142">In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage.</span></span> <span data-ttu-id="48f38-143">属性值可以是暂时的，如一天中的时间，在这种情况下， `Get` 每次访问该属性时，该过程会动态计算该属性。</span><span class="sxs-lookup"><span data-stu-id="48f38-143">A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f38-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48f38-144">See also</span></span>

- [<span data-ttu-id="48f38-145">Property 过程</span><span class="sxs-lookup"><span data-stu-id="48f38-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="48f38-146">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="48f38-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="48f38-147">Property Statement</span><span class="sxs-lookup"><span data-stu-id="48f38-147">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="48f38-148">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="48f38-148">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="48f38-149">如何：创建属性</span><span class="sxs-lookup"><span data-stu-id="48f38-149">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="48f38-150">如何：声明具有混合访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="48f38-150">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="48f38-151">如何：调用 Property 过程</span><span class="sxs-lookup"><span data-stu-id="48f38-151">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="48f38-152">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="48f38-152">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="48f38-153">如何：在属性中放置值</span><span class="sxs-lookup"><span data-stu-id="48f38-153">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="48f38-154">如何：从属性获取值</span><span class="sxs-lookup"><span data-stu-id="48f38-154">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
