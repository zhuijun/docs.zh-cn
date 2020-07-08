---
title: 演练：创建 COM 对象
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 6ff23f73af384a1440bcebd4b6bac21714e01756
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051475"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="6bb2d-102">演练：使用 Visual Basic 创建 COM 对象</span><span class="sxs-lookup"><span data-stu-id="6bb2d-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="6bb2d-103">创建新的应用程序或组件时，最好创建 .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="6bb2d-104">不过，Visual Basic 还可以轻松地向 COM 公开 .NET Framework 组件。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="6bb2d-105">这使你可以为需要 COM 组件的早期应用程序套件提供新组件。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="6bb2d-106">本演练演示了如何使用 Visual Basic 将 .NET Framework 对象公开为 COM 对象，无论使用 COM 类模板还是不使用 COM 类模板。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="6bb2d-107">公开 COM 对象的最简单方法是使用 COM 类模板。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="6bb2d-108">此模板创建一个新类，然后将项目配置为生成具有互操作性层作为 COM 对象的类，并将其注册到操作系统。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-108">This template creates a new class, then configures your project to generate the class with an interoperability layer as a COM object, and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bb2d-109">尽管还可以公开在 Visual Basic 中创建的类作为要使用的非托管代码的 COM 对象，但它不是真正的 COM 对象，不能由 Visual Basic 使用。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="6bb2d-110">有关详细信息，请参阅[.NET Framework 应用程序中的 COM 互操作性](com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-110">For more information, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="6bb2d-111">使用 COM 类模板创建 COM 对象</span><span class="sxs-lookup"><span data-stu-id="6bb2d-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="6bb2d-112">单击 "**新建项目**"，从 "**文件**" 菜单打开新的 Windows 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="6bb2d-113">在 "**新建项目**" 对话框中的 "**项目类型**" 字段下，选中 "Windows" 处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="6bb2d-114">从 "**模板**" 列表中选择 **"类库"** ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="6bb2d-115">将显示新项目。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="6bb2d-116">从 "**项目**" 菜单中选择 "**添加新项**"。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="6bb2d-117">随即出现“添加新项”对话框。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="6bb2d-118">从 "**模板**" 列表中选择**COM 类**，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="6bb2d-119">Visual Basic 添加一个新类，并为 COM 互操作配置新的项目。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="6bb2d-120">向 COM 类中添加代码，如属性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="6bb2d-121">从 "**生成**" 菜单中选择 "**生成 classlibrary1.chainone** "。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="6bb2d-122">Visual Basic 生成程序集并向操作系统注册 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="6bb2d-123">不带 COM 类模板创建 COM 对象</span><span class="sxs-lookup"><span data-stu-id="6bb2d-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="6bb2d-124">你还可以手动创建 COM 类，而不是使用 COM 类模板。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="6bb2d-125">当你在命令行中工作或需要更好地控制如何定义 COM 对象时，此过程非常有用。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="6bb2d-126">设置项目以生成 COM 对象</span><span class="sxs-lookup"><span data-stu-id="6bb2d-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="6bb2d-127">单击 " **NewProject**"，从 "**文件**" 菜单打开新的 Windows 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="6bb2d-128">在 "**新建项目**" 对话框中的 "**项目类型**" 字段下，选中 "Windows" 处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="6bb2d-129">从 "**模板**" 列表中选择 **"类库"** ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="6bb2d-130">将显示新项目。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="6bb2d-131">在“解决方案资源管理器”中，右键单击项目，然后单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="6bb2d-132">随即显示 "**项目设计器**"。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="6bb2d-133">单击“编译”选项卡。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="6bb2d-134">选中 "**为 COM 互操作注册**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="6bb2d-135">在类中设置代码以创建 COM 对象</span><span class="sxs-lookup"><span data-stu-id="6bb2d-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="6bb2d-136">在**解决方案资源管理器**中，双击 " **Class1** " 以显示其代码。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="6bb2d-137">将类重命名为 `ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="6bb2d-138">将以下常量添加到 `ComClass1` 。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="6bb2d-139">它们将存储 COM 对象所需的全局唯一标识符（GUID）常量。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="6bb2d-140">在“工具”\*\*\*\* 菜单上，单击“创建 Guid”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="6bb2d-141">在“创建 GUID”\*\*\*\* 对话框中，单击“注册表格式”\*\*\*\*，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="6bb2d-142">单击 **“退出”**。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="6bb2d-143">用 GUID 替换的空字符串 `ClassId` ，同时删除前导大括号和尾随大括号。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="6bb2d-144">例如，如果 Guidgen.exe 提供的 GUID 为， `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` 则代码应如下所示。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="6bb2d-145">对和常量重复前面的 `InterfaceId` 步骤 `EventsId` ，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="6bb2d-146">请确保 Guid 是新的且唯一的;否则，COM 组件可能会与其他 COM 组件发生冲突。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="6bb2d-147">将 `ComClass` 属性添加到 `ComClass1` ，并为类 Id、接口 ID 和事件 ID 指定 guid，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="6bb2d-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="6bb2d-148">COM 类必须具有无参数的 `Public Sub New()` 构造函数，否则类将不会正确注册。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="6bb2d-149">向类添加无参数构造函数：</span><span class="sxs-lookup"><span data-stu-id="6bb2d-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="6bb2d-150">向类添加属性、方法和事件，并将其以语句结束 `End Class` 。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="6bb2d-151">从 "**生成**" 菜单中选择 "**生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="6bb2d-152">Visual Basic 生成程序集并向操作系统注册 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6bb2d-153">使用 Visual Basic 生成的 COM 对象无法由其他 Visual Basic 应用程序使用，因为它们不是真正的 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="6bb2d-154">尝试添加对此类 COM 对象的引用将引发错误。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="6bb2d-155">有关详细信息，请参阅[.NET Framework 应用程序中的 COM 互操作性](com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="6bb2d-155">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb2d-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="6bb2d-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="6bb2d-157">COM 互操作</span><span class="sxs-lookup"><span data-stu-id="6bb2d-157">COM Interop</span></span>](index.md)
- [<span data-ttu-id="6bb2d-158">演练：使用 COM 对象实现继承</span><span class="sxs-lookup"><span data-stu-id="6bb2d-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="6bb2d-159">#Region 指令</span><span class="sxs-lookup"><span data-stu-id="6bb2d-159">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="6bb2d-160">.NET Framework 应用程序中的 COM 互操作性</span><span class="sxs-lookup"><span data-stu-id="6bb2d-160">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="6bb2d-161">互操作性疑难解答</span><span class="sxs-lookup"><span data-stu-id="6bb2d-161">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
