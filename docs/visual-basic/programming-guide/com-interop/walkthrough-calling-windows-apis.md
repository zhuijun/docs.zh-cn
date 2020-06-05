---
title: 演练：调用 Windows API
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: c7b84a3bb12329ae235e5ea03dc5e86f921112c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396748"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="2ea5e-102">演练：调用 Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ea5e-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="2ea5e-103">Windows Api 是 Windows 操作系统中的动态链接库（Dll）。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="2ea5e-104">当难以编写您自己的等效过程时，可以使用它们来执行任务。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="2ea5e-105">例如，Windows 提供了一个名为 `FlashWindowEx` 的函数，使你可以使应用程序的标题栏在浅色和暗色之间交替。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="2ea5e-106">在您的代码中使用 Windows Api 的优势在于它们可以节省开发时间，因为它们包含已经编写并等待使用的数十个有用函数。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="2ea5e-107">缺点在于，当出现问题时，Windows Api 可能难以处理并铁面无私。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="2ea5e-108">Windows Api 表示一种特殊的互操作性类别。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="2ea5e-109">Windows Api 不使用托管代码，不具备内置类型库，而是使用与 Visual Studio 使用的数据类型不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="2ea5e-110">由于存在这些差异，并且 Windows Api 不是 COM 对象，因此，使用平台调用或 PInvoke 执行与 Windows Api 和 .NET Framework 的互操作性。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the .NET Framework is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="2ea5e-111">平台调用是一项服务，它使托管代码能够调用 Dll 中实现的非托管函数。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="2ea5e-112">有关详细信息，请参阅[使用非托管 DLL 函数](../../../framework/interop/consuming-unmanaged-dll-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-112">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md).</span></span> <span data-ttu-id="2ea5e-113">可以通过使用 `Declare` 语句或将 `DllImport` 属性应用于空过程，在 Visual Basic 中使用 PInvoke。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-113">You can use PInvoke in Visual Basic by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="2ea5e-114">Windows API 调用是过去 Visual Basic 编程的重要组成部分，但在 Visual Basic .NET 中很少需要。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-114">Windows API calls were an important part of Visual Basic programming in the past, but are seldom necessary with Visual Basic .NET.</span></span> <span data-ttu-id="2ea5e-115">应尽可能使用 .NET Framework 中的托管代码来执行任务，而不是 Windows API 调用。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-115">Whenever possible, you should use managed code from the .NET Framework to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="2ea5e-116">本演练介绍了需要使用 Windows Api 的情况的信息。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="2ea5e-117">使用 Declare 的 API 调用</span><span class="sxs-lookup"><span data-stu-id="2ea5e-117">API Calls Using Declare</span></span>  
 <span data-ttu-id="2ea5e-118">调用 Windows Api 的最常见方法是使用 `Declare` 语句。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="2ea5e-119">声明 DLL 过程</span><span class="sxs-lookup"><span data-stu-id="2ea5e-119">To declare a DLL procedure</span></span>  
  
1. <span data-ttu-id="2ea5e-120">确定要调用的函数的名称，以及该函数的参数、参数类型和返回值，以及包含该函数的 DLL 的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2ea5e-121">有关 Windows Api 的完整信息，请参阅 Platform sdk Windows API 中的 Win32 SDK 文档。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="2ea5e-122">有关 Windows Api 使用的常量的详细信息，请检查在平台 SDK 中包含的头文件（如 Windows）。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2. <span data-ttu-id="2ea5e-123">在 "**文件**" 菜单上单击 "**新建**"，然后单击 "**项目**"，以打开新的 Windows 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="2ea5e-124">将显示“新建项目”对话框。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-124">The **New Project** dialog box appears.</span></span>  
  
3. <span data-ttu-id="2ea5e-125">从 Visual Basic 项目模板列表中选择 " **Windows 应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-125">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="2ea5e-126">将显示新项目。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-126">The new project is displayed.</span></span>  
  
4. <span data-ttu-id="2ea5e-127">将以下 `Declare` 函数添加到要在其中使用 DLL 的类或模块：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="2ea5e-128">Declare 语句的组成部分</span><span class="sxs-lookup"><span data-stu-id="2ea5e-128">Parts of the Declare Statement</span></span>  
 <span data-ttu-id="2ea5e-129">`Declare`语句包括以下元素。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-129">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="2ea5e-130">Auto 修饰符</span><span class="sxs-lookup"><span data-stu-id="2ea5e-130">Auto modifier</span></span>  
 <span data-ttu-id="2ea5e-131">`Auto`修饰符指示运行时根据公共语言运行时规则（如果指定，则为别名）转换基于方法名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-131">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="2ea5e-132">Lib 和 Alias 关键字</span><span class="sxs-lookup"><span data-stu-id="2ea5e-132">Lib and Alias keywords</span></span>  
 <span data-ttu-id="2ea5e-133">关键字后面的名称 `Function` 是程序用来访问导入的函数的名称。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-133">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="2ea5e-134">它可以与要调用的函数的实际名称相同，也可以使用任何有效的过程名称，然后使用 `Alias` 关键字来指定要调用的函数的真实名称。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-134">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="2ea5e-135">指定 `Lib` 关键字，后跟包含要调用的函数的 DLL 的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-135">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="2ea5e-136">不需要指定位于 Windows 系统目录中的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-136">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="2ea5e-137">如果要 `Alias` 调用的函数的名称不是有效的 Visual Basic 过程名称，或者与应用程序中其他项的名称冲突，请使用关键字。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-137">Use the `Alias` keyword if the name of the function you are calling is not a valid Visual Basic procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="2ea5e-138">`Alias`指示正在调用的函数的真实名称。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-138">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="2ea5e-139">参数和数据类型声明</span><span class="sxs-lookup"><span data-stu-id="2ea5e-139">Argument and Data Type Declarations</span></span>  
 <span data-ttu-id="2ea5e-140">声明参数及其数据类型。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-140">Declare the arguments and their data types.</span></span> <span data-ttu-id="2ea5e-141">此部分可能具有挑战性，因为 Windows 使用的数据类型与 Visual Studio 数据类型不对应。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-141">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> <span data-ttu-id="2ea5e-142">Visual Basic 通过将参数转换为兼容的数据类型（称为*封送*处理的进程）来执行大量的工作。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-142">Visual Basic does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="2ea5e-143">您可以通过使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 命名空间中定义的属性来显式控制如何对参数进行封送处理 <xref:System.Runtime.InteropServices> 。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-143">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ea5e-144">以前版本的 Visual Basic 允许你声明参数 `As Any` ，这意味着可以使用任何数据类型的数据。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-144">Previous versions of Visual Basic allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> <span data-ttu-id="2ea5e-145">Visual Basic 要求对所有语句使用特定数据类型 `Declare` 。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-145">Visual Basic requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="2ea5e-146">Windows API 常量</span><span class="sxs-lookup"><span data-stu-id="2ea5e-146">Windows API Constants</span></span>  
 <span data-ttu-id="2ea5e-147">一些参数是常量的组合。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-147">Some arguments are combinations of constants.</span></span> <span data-ttu-id="2ea5e-148">例如， `MessageBox` 本演练中所示的 API 接受一个名为的整数参数 `Typ` ，用于控制消息框的显示方式。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-148">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="2ea5e-149">可以通过检查 Winuser.h 文件中的语句来确定这些常量的数值 `#define` 。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-149">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="2ea5e-150">数值通常以十六进制显示，因此，您可能希望使用计算器来添加它们并将其转换为 decimal。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-150">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="2ea5e-151">例如，如果想要将感叹号样式的常量 `MB_ICONEXCLAMATION` 0x00000030 和 Yes/No 样式0x00000004 组合在一起 `MB_YESNO` ，则可以添加数字，并获得0x00000034 或 52 decimal 的结果。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-151">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="2ea5e-152">虽然您可以直接使用 decimal 结果，但最好将这些值声明为应用程序中的常量，并使用运算符组合这些值 `Or` 。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-152">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="2ea5e-153">声明用于 Windows API 调用的常量</span><span class="sxs-lookup"><span data-stu-id="2ea5e-153">To declare constants for Windows API calls</span></span>  
  
1. <span data-ttu-id="2ea5e-154">请查阅您正在调用的 Windows 函数的文档。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-154">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="2ea5e-155">确定其使用的常量的名称以及包含这些常量的数值的 .h 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-155">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2. <span data-ttu-id="2ea5e-156">使用文本编辑器（如记事本）查看标头（.h）文件的内容，并查找与正在使用的常量相关联的值。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-156">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="2ea5e-157">例如， `MessageBox` API 使用常量 `MB_ICONQUESTION` 在消息框中显示一个问号。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-157">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="2ea5e-158">的定义位于 `MB_ICONQUESTION` winuser.h 中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-158">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. <span data-ttu-id="2ea5e-159">将等效 `Const` 语句添加到你的类或模块，以使这些常量可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-159">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="2ea5e-160">例如：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-160">For example:</span></span>  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="2ea5e-161">调用 DLL 过程</span><span class="sxs-lookup"><span data-stu-id="2ea5e-161">To call the DLL procedure</span></span>  
  
1. <span data-ttu-id="2ea5e-162">将名为的按钮添加 `Button1` 到项目的启动窗体，然后双击它以查看其代码。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-162">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="2ea5e-163">显示按钮的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-163">The event handler for the button is displayed.</span></span>  
  
2. <span data-ttu-id="2ea5e-164">向 `Click` 添加的按钮的事件处理程序中添加代码，以调用过程并提供相应的参数：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-164">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. <span data-ttu-id="2ea5e-165">按 F5 运行项目。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-165">Run the project by pressing F5.</span></span> <span data-ttu-id="2ea5e-166">消息框显示 **"是" 和 "** **无**" 响应按钮。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-166">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="2ea5e-167">单击任一项。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-167">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="2ea5e-168">数据封送</span><span class="sxs-lookup"><span data-stu-id="2ea5e-168">Data Marshaling</span></span>  
 <span data-ttu-id="2ea5e-169">Visual Basic 会自动转换 Windows API 调用的参数和返回值的数据类型，但可以使用 `MarshalAs` 属性显式指定 API 预期的非托管数据类型。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-169">Visual Basic automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="2ea5e-170">有关互操作封送处理的详细信息，请参阅[互操作封送处理](../../../framework/interop/interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-170">For more information about interop marshaling, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="2ea5e-171">在 API 调用中使用 Declare 和 MarshalAs</span><span class="sxs-lookup"><span data-stu-id="2ea5e-171">To use Declare and MarshalAs in an API call</span></span>  
  
1. <span data-ttu-id="2ea5e-172">确定要调用的函数的名称，以及该函数的参数、数据类型和返回值。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-172">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2. <span data-ttu-id="2ea5e-173">若要简化对属性的访问 `MarshalAs` ，请向 `Imports` 类或模块的代码顶部添加一个语句，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-173">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. <span data-ttu-id="2ea5e-174">将导入函数的函数原型添加到正在使用的类或模块，并将该特性应用于 `MarshalAs` 参数或返回值。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-174">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="2ea5e-175">在下面的示例中，需要将类型 `void*` 封送为的 API 调用如下 `AsAny` ：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-175">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="2ea5e-176">使用 DllImport 的 API 调用</span><span class="sxs-lookup"><span data-stu-id="2ea5e-176">API Calls Using DllImport</span></span>  
 <span data-ttu-id="2ea5e-177">`DllImport`特性提供了另一种方法来调用不带类型库的 dll 中的函数。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-177">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="2ea5e-178">`DllImport`大致等效于使用语句， `Declare` 但可以更好地控制调用函数的方式。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-178">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="2ea5e-179">`DllImport`只要调用引用共享（有时称为*静态*）方法，就可以将用于大多数 Windows API 调用。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-179">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="2ea5e-180">不能使用需要类的实例的方法。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-180">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="2ea5e-181">与 `Declare` 语句不同， `DllImport` 调用不能使用 `MarshalAs` 属性。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-181">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="2ea5e-182">使用 DllImport 特性调用 Windows API</span><span class="sxs-lookup"><span data-stu-id="2ea5e-182">To call a Windows API using the DllImport attribute</span></span>  
  
1. <span data-ttu-id="2ea5e-183">在 "**文件**" 菜单上单击 "**新建**"，然后单击 "**项目**"，以打开新的 Windows 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-183">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="2ea5e-184">将显示“新建项目”对话框。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-184">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="2ea5e-185">从 Visual Basic 项目模板列表中选择 " **Windows 应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-185">Select **Windows Application** from the list of Visual Basic project templates.</span></span> <span data-ttu-id="2ea5e-186">将显示新项目。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-186">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="2ea5e-187">将名为的按钮添加 `Button2` 到启动窗体。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-187">Add a button named `Button2` to the startup form.</span></span>  
  
4. <span data-ttu-id="2ea5e-188">双击 `Button2` 打开窗体的代码视图。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-188">Double-click `Button2` to open the code view for the form.</span></span>  
  
5. <span data-ttu-id="2ea5e-189">若要简化对的访问 `DllImport` ，请将 `Imports` 语句添加到 startup 窗体类的代码顶部：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-189">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. <span data-ttu-id="2ea5e-190">在该窗体的语句之前声明一个空函数 `End Class` ，并将该函数命名为 `MoveFile` 。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-190">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7. <span data-ttu-id="2ea5e-191">将 `Public` 和修饰符应用于 `Shared` 函数声明，并 `MoveFile` 基于 Windows API 函数使用的参数设置参数：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-191">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     <span data-ttu-id="2ea5e-192">函数可以具有任何有效的过程名称;`DllImport`特性指定 DLL 中的名称。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-192">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="2ea5e-193">它还处理参数和返回值的互操作性封送处理，以便可以选择类似于 API 使用的数据类型的 Visual Studio 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-193">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8. <span data-ttu-id="2ea5e-194">将特性应用于 `DllImport` 空函数。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-194">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="2ea5e-195">第一个参数是包含所调用函数的 DLL 的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-195">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="2ea5e-196">不需要指定位于 Windows 系统目录中的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-196">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="2ea5e-197">第二个参数是命名参数，用于指定 Windows API 中函数的名称。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-197">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="2ea5e-198">在此示例中， `DllImport` 属性强制将调用 `MoveFile` 转发到 `MoveFileW` kernel32.dll 中的。.DLL.</span><span class="sxs-lookup"><span data-stu-id="2ea5e-198">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="2ea5e-199">`MoveFileW`方法从路径 `src` 向路径复制文件 `dst` 。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-199">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. <span data-ttu-id="2ea5e-200">向 `Button2_Click` 事件处理程序添加代码以调用函数：</span><span class="sxs-lookup"><span data-stu-id="2ea5e-200">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. <span data-ttu-id="2ea5e-201">创建名为 test.txt 的文件，并将其放在硬盘驱动器上的 C:\Tmp 目录中。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-201">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="2ea5e-202">如有必要，请创建 Tmp 目录。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-202">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="2ea5e-203">按 F5 键启动该应用程序。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-203">Press F5 to start the application.</span></span> <span data-ttu-id="2ea5e-204">主窗体出现。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-204">The main form appears.</span></span>  
  
12. <span data-ttu-id="2ea5e-205">单击 " **Button2**"。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-205">Click **Button2**.</span></span> <span data-ttu-id="2ea5e-206">如果可以移动该文件，则会显示消息 "文件已成功移动"。</span><span class="sxs-lookup"><span data-stu-id="2ea5e-206">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea5e-207">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ea5e-207">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2ea5e-208">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="2ea5e-208">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="2ea5e-209">自动</span><span class="sxs-lookup"><span data-stu-id="2ea5e-209">Auto</span></span>](../../language-reference/modifiers/auto.md)
- [<span data-ttu-id="2ea5e-210">别名</span><span class="sxs-lookup"><span data-stu-id="2ea5e-210">Alias</span></span>](../../language-reference/statements/alias-clause.md)
- [<span data-ttu-id="2ea5e-211">COM 互操作</span><span class="sxs-lookup"><span data-stu-id="2ea5e-211">COM Interop</span></span>](index.md)
- [<span data-ttu-id="2ea5e-212">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="2ea5e-212">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="2ea5e-213">将委托作为回调方法进行封送</span><span class="sxs-lookup"><span data-stu-id="2ea5e-213">Marshaling a Delegate as a Callback Method</span></span>](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
