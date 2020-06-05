---
title: My.Forms 对象
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372435"
---
# <a name="myforms-object"></a><span data-ttu-id="9e2ff-102">My.Forms 对象</span><span class="sxs-lookup"><span data-stu-id="9e2ff-102">My.Forms Object</span></span>

<span data-ttu-id="9e2ff-103">为访问在当前项目中声明的每个 Windows 窗体的实例提供属性。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e2ff-104">备注</span><span class="sxs-lookup"><span data-stu-id="9e2ff-104">Remarks</span></span>

<span data-ttu-id="9e2ff-105">`My.Forms`对象为当前项目中的每个窗体提供一个实例。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="9e2ff-106">属性的名称与属性访问的窗体的名称相同。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-106">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="9e2ff-107">您可以 `My.Forms` 通过使用窗体的名称，而无需限定来访问由对象提供的窗体。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="9e2ff-108">因为属性名称与窗体的类型名称相同，所以这允许你像访问默认实例一样访问窗体。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="9e2ff-109">例如，`My.Forms.Form1.Show` 与 `Form1.Show` 等效。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="9e2ff-110">`My.Forms`对象只公开与当前项目关联的窗体。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="9e2ff-111">它不提供对引用 Dll 中声明的窗体的访问。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="9e2ff-112">若要访问 DLL 提供的窗体，必须使用以*DllName*形式编写的格式的限定名称。*FormName*。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="9e2ff-113">您可以使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> 属性来获取应用程序的所有打开窗体的集合。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="9e2ff-114">对象及其属性仅适用于 Windows 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-114">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="9e2ff-115">属性</span><span class="sxs-lookup"><span data-stu-id="9e2ff-115">Properties</span></span>

<span data-ttu-id="9e2ff-116">对象的每个属性都 `My.Forms` 提供对当前项目中窗体的实例的访问。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="9e2ff-117">属性的名称与属性访问的窗体的名称相同，属性类型与窗体的类型相同。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="9e2ff-118">如果存在名称冲突，则用于访问窗体的属性名称为*RootNamespace*_*命名空间* \_ *FormName*。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="9e2ff-119">例如，假设有两个名为的窗体： `Form1.` 如果其中一个窗体位于根命名空间 `WindowsApplication1` 和命名空间中 `Namespace1` ，则可以通过访问该窗体 `My.Forms.WindowsApplication1_Namespace1_Form1` 。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="9e2ff-120">`My.Forms`对象提供对启动时创建的应用程序主窗体实例的访问权限。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="9e2ff-121">对于所有其他窗体， `My.Forms` 对象在被访问并存储时创建窗体的新实例。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="9e2ff-122">后续尝试访问该属性将返回该窗体的实例。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-122">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="9e2ff-123">您可以通过 `Nothing` 向窗体的属性分配来释放窗体。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="9e2ff-124">属性 setter 调用 <xref:System.Windows.Forms.Form.Close%2A> 窗体的方法，然后将分配 `Nothing` 给存储的值。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="9e2ff-125">如果为属性分配除以外的任何值 `Nothing` ，则 setter 会引发 <xref:System.ArgumentException> 异常。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="9e2ff-126">您可以 `My.Forms` 使用 or 运算符测试对象的属性是否存储窗体的实例 `Is` `IsNot` 。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="9e2ff-127">您可以使用这些运算符来检查属性的值是否为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="9e2ff-128">通常， `Is` 或 `IsNot` 运算符必须读取属性的值才能执行比较。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="9e2ff-129">但是，如果属性当前存储 `Nothing` ，则属性创建窗体的新实例，然后返回该实例。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="9e2ff-130">不过，Visual Basic 编译器 `My.Forms` 会以不同的方式处理对象的属性，并允许 `Is` 或 `IsNot` 运算符检查属性的状态，而无需更改其值。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="9e2ff-131">示例</span><span class="sxs-lookup"><span data-stu-id="9e2ff-131">Example</span></span>

<span data-ttu-id="9e2ff-132">此示例更改默认窗体的标题 `SidebarMenu` 。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-132">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="9e2ff-133">要使此示例正常运行，你的项目必须具有名为的窗体 `SidebarMenu` 。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="9e2ff-134">此代码仅适用于 Windows 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-134">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e2ff-135">要求</span><span class="sxs-lookup"><span data-stu-id="9e2ff-135">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="9e2ff-136">按项目类型的可用性</span><span class="sxs-lookup"><span data-stu-id="9e2ff-136">Availability by Project Type</span></span>

|<span data-ttu-id="9e2ff-137">项目类型</span><span class="sxs-lookup"><span data-stu-id="9e2ff-137">Project type</span></span>|<span data-ttu-id="9e2ff-138">可用</span><span class="sxs-lookup"><span data-stu-id="9e2ff-138">Available</span></span>|
|---|---|
|<span data-ttu-id="9e2ff-139">Windows 应用程序</span><span class="sxs-lookup"><span data-stu-id="9e2ff-139">Windows Application</span></span>|<span data-ttu-id="9e2ff-140">**是**</span><span class="sxs-lookup"><span data-stu-id="9e2ff-140">**Yes**</span></span>|
|<span data-ttu-id="9e2ff-141">类库</span><span class="sxs-lookup"><span data-stu-id="9e2ff-141">Class Library</span></span>|<span data-ttu-id="9e2ff-142">否</span><span class="sxs-lookup"><span data-stu-id="9e2ff-142">No</span></span>|
|<span data-ttu-id="9e2ff-143">控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="9e2ff-143">Console Application</span></span>|<span data-ttu-id="9e2ff-144">否</span><span class="sxs-lookup"><span data-stu-id="9e2ff-144">No</span></span>|
|<span data-ttu-id="9e2ff-145">Windows 控件库</span><span class="sxs-lookup"><span data-stu-id="9e2ff-145">Windows Control Library</span></span>|<span data-ttu-id="9e2ff-146">否</span><span class="sxs-lookup"><span data-stu-id="9e2ff-146">No</span></span>|
|<span data-ttu-id="9e2ff-147">Web 控件库</span><span class="sxs-lookup"><span data-stu-id="9e2ff-147">Web Control Library</span></span>|<span data-ttu-id="9e2ff-148">否</span><span class="sxs-lookup"><span data-stu-id="9e2ff-148">No</span></span>|
|<span data-ttu-id="9e2ff-149">Windows 服务</span><span class="sxs-lookup"><span data-stu-id="9e2ff-149">Windows Service</span></span>|<span data-ttu-id="9e2ff-150">否</span><span class="sxs-lookup"><span data-stu-id="9e2ff-150">No</span></span>|
|<span data-ttu-id="9e2ff-151">网站</span><span class="sxs-lookup"><span data-stu-id="9e2ff-151">Web Site</span></span>|<span data-ttu-id="9e2ff-152">否</span><span class="sxs-lookup"><span data-stu-id="9e2ff-152">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="9e2ff-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e2ff-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="9e2ff-154">对象</span><span class="sxs-lookup"><span data-stu-id="9e2ff-154">Objects</span></span>](index.md)
- [<span data-ttu-id="9e2ff-155">Is 运算符</span><span class="sxs-lookup"><span data-stu-id="9e2ff-155">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="9e2ff-156">IsNot 运算符</span><span class="sxs-lookup"><span data-stu-id="9e2ff-156">IsNot Operator</span></span>](../operators/isnot-operator.md)
- [<span data-ttu-id="9e2ff-157">访问应用程序窗体</span><span class="sxs-lookup"><span data-stu-id="9e2ff-157">Accessing Application Forms</span></span>](../../developing-apps/programming/accessing-application-forms.md)
