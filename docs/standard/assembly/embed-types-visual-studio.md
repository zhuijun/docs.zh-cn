---
title: 演练：在 Visual Studio 中嵌入托管程序集中的类型
description: 本演练演示如何使用 Visual Studio 在 .NET 中嵌入托管程序集中的类型。 嵌入类型可支持版本独立性。
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378987"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="e92d9-104">演练：在 Visual Studio 中嵌入托管程序集中的类型</span><span class="sxs-lookup"><span data-stu-id="e92d9-104">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="e92d9-105">如果嵌入强命名托管程序集中的类型信息，则可以对应用程序中的类型进行松耦合，以实现版本独立性。</span><span class="sxs-lookup"><span data-stu-id="e92d9-105">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="e92d9-106">也就是说，可以将程序编写为使用托管库任何版本中的类型，而不必对每个版本重新编译程序。</span><span class="sxs-lookup"><span data-stu-id="e92d9-106">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="e92d9-107">类型嵌入经常与 COM 互操作一起使用，例如使用 Microsoft Office 中的自动化对象的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e92d9-107">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="e92d9-108">通过嵌入类型信息，程序的同一个版本可以处理不同计算机上的不同 Microsoft Office 版本。</span><span class="sxs-lookup"><span data-stu-id="e92d9-108">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="e92d9-109">但也可以在完全托管的解决方案中使用类型嵌入。</span><span class="sxs-lookup"><span data-stu-id="e92d9-109">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="e92d9-110">指定可嵌入的公共接口后，创建实现这些接口的运行时类。</span><span class="sxs-lookup"><span data-stu-id="e92d9-110">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="e92d9-111">客户端程序可以通过引用包含这些公共接口的程序集，并将该引用的 `Embed Interop Types` 属性设置为 `True`，即可在设计时嵌入这些接口的类型信息。</span><span class="sxs-lookup"><span data-stu-id="e92d9-111">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="e92d9-112">然后，客户端程序可以加载类型化为这些接口的运行时对象的实例。</span><span class="sxs-lookup"><span data-stu-id="e92d9-112">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="e92d9-113">这相当于使用命令行编译器和通过 [-link 编译器选项](../../csharp/language-reference/compiler-options/link-compiler-option.md)引用该程序集。</span><span class="sxs-lookup"><span data-stu-id="e92d9-113">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="e92d9-114">如果创建新版本的强命名运行时程序集，则不必重新编译客户端程序。</span><span class="sxs-lookup"><span data-stu-id="e92d9-114">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="e92d9-115">客户端程序继续使用任何可用的运行时程序集版本，使用公共接口的嵌入类型信息。</span><span class="sxs-lookup"><span data-stu-id="e92d9-115">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="e92d9-116">在此演练中，将：</span><span class="sxs-lookup"><span data-stu-id="e92d9-116">In this walkthrough, you:</span></span>

1. <span data-ttu-id="e92d9-117">创建一个强命名程序集，使其中的公共接口包含可嵌入的类型信息。</span><span class="sxs-lookup"><span data-stu-id="e92d9-117">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="e92d9-118">创建一个实现公共接口的强命名运行时程序集。</span><span class="sxs-lookup"><span data-stu-id="e92d9-118">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="e92d9-119">创建一个客户端程序，该程序嵌入公共接口中的类型信息，并创建运行时程序集中的类的实例。</span><span class="sxs-lookup"><span data-stu-id="e92d9-119">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="e92d9-120">修改并重新生成运行时程序集。</span><span class="sxs-lookup"><span data-stu-id="e92d9-120">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="e92d9-121">运行客户端程序，查看是否使用运行时程序集的新版本，而不必进行重新编译。</span><span class="sxs-lookup"><span data-stu-id="e92d9-121">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="e92d9-122">条件和限制</span><span class="sxs-lookup"><span data-stu-id="e92d9-122">Conditions and limitations</span></span>

<span data-ttu-id="e92d9-123">可以在以下条件下嵌入程序集中的类型信息：</span><span class="sxs-lookup"><span data-stu-id="e92d9-123">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="e92d9-124">程序集至少公开一个公共接口。</span><span class="sxs-lookup"><span data-stu-id="e92d9-124">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="e92d9-125">嵌入的接口使用具有唯一 GUID 的 `ComImport` 属性和 `Guid` 属性进行批注。</span><span class="sxs-lookup"><span data-stu-id="e92d9-125">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="e92d9-126">程序集使用 `ImportedFromTypeLib` 特性或 `PrimaryInteropAssembly` 特性和程序集级别的 `Guid` 特性进行批注。</span><span class="sxs-lookup"><span data-stu-id="e92d9-126">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="e92d9-127">默认情况下，Visual C# 和 Visual Basic 项目模板包含程序集级别的 `Guid` 属性。</span><span class="sxs-lookup"><span data-stu-id="e92d9-127">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="e92d9-128">由于类型嵌入的主要功能是支持 COM 互操作程序集，因此在完全托管解决方案中嵌入类型信息时，将应用以下限制：</span><span class="sxs-lookup"><span data-stu-id="e92d9-128">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="e92d9-129">仅嵌入特定于 COM 互操作的属性。</span><span class="sxs-lookup"><span data-stu-id="e92d9-129">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="e92d9-130">忽略其他属性。</span><span class="sxs-lookup"><span data-stu-id="e92d9-130">Other attributes are ignored.</span></span>
- <span data-ttu-id="e92d9-131">如果一个类型使用泛型参数，且泛型参数的类型是嵌入类型，则不能跨程序集边界使用该类型。</span><span class="sxs-lookup"><span data-stu-id="e92d9-131">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="e92d9-132">跨程序集边界的示例包括从另一个程序集调用方法或从另一个程序集中定义的类型派生类型。</span><span class="sxs-lookup"><span data-stu-id="e92d9-132">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="e92d9-133">不嵌入常量。</span><span class="sxs-lookup"><span data-stu-id="e92d9-133">Constants are not embedded.</span></span>
- <span data-ttu-id="e92d9-134"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 类不支持将嵌入类型作为密钥。</span><span class="sxs-lookup"><span data-stu-id="e92d9-134">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="e92d9-135">可以实现自己的字典类型以支持将嵌入类型作为密钥。</span><span class="sxs-lookup"><span data-stu-id="e92d9-135">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="e92d9-136">创建接口</span><span class="sxs-lookup"><span data-stu-id="e92d9-136">Create an interface</span></span>

<span data-ttu-id="e92d9-137">第一步是创建类型等效性接口程序集。</span><span class="sxs-lookup"><span data-stu-id="e92d9-137">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="e92d9-138">在 Visual Studio 中，选择“文件” > “新建” > “项目”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-138">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="e92d9-139">在“创建新项目”对话框中，在“搜索模板”框中键入“类库”。</span><span class="sxs-lookup"><span data-stu-id="e92d9-139">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="e92d9-140">从列表中选择 C# 或 Visual Basic“类库(.NET Framework)”模板，然后选择“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-140">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="e92d9-141">在“配置新项目”对话框的“项目名称”下，键入“TypeEquivalenceInterface”，然后选择“创建” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-141">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="e92d9-142">新项目创建完成。</span><span class="sxs-lookup"><span data-stu-id="e92d9-142">The new project is created.</span></span>

1. <span data-ttu-id="e92d9-143">在“解决方案资源管理器”中，右键单击“Class1.cs”或“Class1.vb”文件，选择“重命名”，并将该文件从“Class1”重命名为“ISampleInterface”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-143">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="e92d9-144">出现提示时选择“是”，同时将类重命名为 `ISampleInterface`。</span><span class="sxs-lookup"><span data-stu-id="e92d9-144">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="e92d9-145">此类表示类的公共接口。</span><span class="sxs-lookup"><span data-stu-id="e92d9-145">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="e92d9-146">在“解决方案资源管理器”中，右键单击 TypeEquivalenceInterface 项目，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-146">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="e92d9-147">在“属性”屏幕的左窗格中选择“生成”，并将“输出路径”设置为计算机上的某个位置（例如 C:\TypeEquivalenceSample）  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-147">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="e92d9-148">本演练中使用相同的位置。</span><span class="sxs-lookup"><span data-stu-id="e92d9-148">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="e92d9-149">在“属性”屏幕的左窗格中选择“签名”，然后选择“对程序集签名”复选框  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-149">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="e92d9-150">在“选择强名称密钥文件”下拉列表中，选择“新建” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-150">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="e92d9-151">在“创建强名称密钥”对话框的“密钥文件名称”下，键入“key.snk” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-151">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="e92d9-152">取消选中“使用密码保护密钥文件”复选框，然后选择“确定” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-152">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="e92d9-153">在代码编辑器中打开 ISampleInterface 类文件，将其内容替换为以下代码，以便创建 `ISampleInterface` 接口：</span><span class="sxs-lookup"><span data-stu-id="e92d9-153">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. <span data-ttu-id="e92d9-154">在“工具”菜单上，选择“创建 GUID”，然后在“创建 GUID”对话框中，选择“注册表格式”   。</span><span class="sxs-lookup"><span data-stu-id="e92d9-154">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="e92d9-155">选择“复制”，然后选择“退出” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-155">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="e92d9-156">在代码的 `Guid` 属性中，将示例 GUID 替换为复制的 GUID，并删除大括号 ({ })。</span><span class="sxs-lookup"><span data-stu-id="e92d9-156">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="e92d9-157">在“解决方案资源管理器”中，展开“属性”文件夹，并选择“AssemblyInfo.cs”或“AssemblyInfo.vb”文件  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-157">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="e92d9-158">在代码编辑器中，将以下属性添加到文件：</span><span class="sxs-lookup"><span data-stu-id="e92d9-158">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="e92d9-159">选择“文件” > “保存全部”，或按 Ctrl+Shift+S 来保存文件和项目    。</span><span class="sxs-lookup"><span data-stu-id="e92d9-159">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="e92d9-160">在“解决方案资源管理器”中，右键单击 TypeEquivalenceInterface 项目，然后选择“生成”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-160">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="e92d9-161">编译类库 DLL 文件，并保存到指定的生成输出路径中（如 C:\TypeEquivalenceSample）。</span><span class="sxs-lookup"><span data-stu-id="e92d9-161">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="e92d9-162">创建运行时类</span><span class="sxs-lookup"><span data-stu-id="e92d9-162">Create a runtime class</span></span>

<span data-ttu-id="e92d9-163">接下来，创建类型等效性运行时类。</span><span class="sxs-lookup"><span data-stu-id="e92d9-163">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="e92d9-164">在 Visual Studio 中，选择“文件” > “新建” > “项目”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-164">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="e92d9-165">在“创建新项目”对话框中，在“搜索模板”框中键入“类库”。</span><span class="sxs-lookup"><span data-stu-id="e92d9-165">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="e92d9-166">从列表中选择 C# 或 Visual Basic“类库(.NET Framework)”模板，然后选择“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-166">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="e92d9-167">在“配置新项目”对话框的“项目名称”下，键入“TypeEquivalenceRuntime”，然后选择“创建” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-167">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="e92d9-168">新项目创建完成。</span><span class="sxs-lookup"><span data-stu-id="e92d9-168">The new project is created.</span></span>

1. <span data-ttu-id="e92d9-169">在“解决方案资源管理器”中，右键单击“Class1.cs”或“Class1.vb”文件，选择“重命名”，并将该文件从“Class1”重命名为“SampleClass”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-169">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="e92d9-170">出现提示时选择“是”，同时将类重命名为 `SampleClass`。</span><span class="sxs-lookup"><span data-stu-id="e92d9-170">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="e92d9-171">此类实现 `ISampleInterface` 接口。</span><span class="sxs-lookup"><span data-stu-id="e92d9-171">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="e92d9-172">在“解决方案资源管理器”中，右键单击 TypeEquivalenceInterface 项目，并选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-172">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="e92d9-173">在“属性”屏幕的左窗格中选择“生成”，然后将“输出路径”设置为用于 TypeEquivalenceInterface 项目的同一位置（例如 C:\TypeEquivalenceSample）  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-173">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="e92d9-174">在“属性”屏幕的左窗格中选择“签名”，然后选择“对程序集签名”复选框  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-174">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="e92d9-175">在“选择强名称密钥文件”下拉列表中，选择“新建” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-175">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="e92d9-176">在“创建强名称密钥”对话框的“密钥文件名称”下，键入“key.snk” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-176">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="e92d9-177">取消选中“使用密码保护密钥文件”复选框，然后选择“确定” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-177">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="e92d9-178">在“解决方案资源管理器”中，右键单击 TypeEquivalenceRuntime 项目，然后选择“添加” > “引用”   。</span><span class="sxs-lookup"><span data-stu-id="e92d9-178">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="e92d9-179">在“引用管理器”对话框中，选择“浏览”并浏览到输出路径文件夹 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-179">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="e92d9-180">选择 TypeEquivalenceInterface.dll 文件，选择“添加”，然后选择“确定” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-180">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="e92d9-181">在“解决方案资源管理器”中，展开“引用”文件夹，并选择“TypeEquivalenceInterface”引用  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-181">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="e92d9-182">在“属性”窗格中，将“特定版本”设置为“False”（如果尚未设置）  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-182">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="e92d9-183">在代码编辑器中打开 SampleClass 类文件，将其内容替换为以下代码，以便创建 `SampleClass` 类：</span><span class="sxs-lookup"><span data-stu-id="e92d9-183">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

   ```csharp
   using System;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }

           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports TypeEquivalenceInterface

   Public Class SampleClass
       Implements ISampleInterface

       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property

       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```

1. <span data-ttu-id="e92d9-184">选择“文件” > “保存全部”，或按 Ctrl+Shift+S 来保存文件和项目    。</span><span class="sxs-lookup"><span data-stu-id="e92d9-184">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="e92d9-185">在“解决方案资源管理器”中，右键单击 TypeEquivalenceRuntime 项目，并选择“生成”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-185">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="e92d9-186">编译类库 DLL 文件，并保存到指定的生成输出路径中。</span><span class="sxs-lookup"><span data-stu-id="e92d9-186">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="e92d9-187">创建客户端项目</span><span class="sxs-lookup"><span data-stu-id="e92d9-187">Create a client project</span></span>

<span data-ttu-id="e92d9-188">最后，创建引用接口程序集的类型等效性客户端程序。</span><span class="sxs-lookup"><span data-stu-id="e92d9-188">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="e92d9-189">在 Visual Studio 中，选择“文件” > “新建” > “项目”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-189">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="e92d9-190">在“创建新项目”对话框中，在“搜索模板”框中键入“控制台”。</span><span class="sxs-lookup"><span data-stu-id="e92d9-190">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="e92d9-191">从列表中选择 C# 或 Visual Basic“控制台应用(.NET Framework)”模板，然后选择“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-191">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="e92d9-192">在“配置新项目”对话框的“项目名称”下，键入“TypeEquivalenceClient”，然后选择“创建” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-192">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="e92d9-193">新项目创建完成。</span><span class="sxs-lookup"><span data-stu-id="e92d9-193">The new project is created.</span></span>

1. <span data-ttu-id="e92d9-194">在“解决方案资源管理器”中，右键单击 TypeEquivalenceClient 项目，并选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="e92d9-195">在“属性”屏幕的左窗格中选择“生成”，然后将“输出路径”设置为用于 TypeEquivalenceInterface 项目的同一位置（例如 C:\TypeEquivalenceSample）  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-195">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="e92d9-196">在“解决方案资源管理器”中，右键单击 TypeEquivalenceClient 项目，并选择“添加” > “引用”   。</span><span class="sxs-lookup"><span data-stu-id="e92d9-196">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="e92d9-197">如果 TypeEquivalenceInterface.dll 文件已在“引用管理器”对话框中列出，则选择该文件 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-197">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="e92d9-198">如果没有，请选择“浏览”，浏览到输出路径文件夹，选择 TypeEquivalenceInterface.dll 文件（而不是 TypeEquivalenceRuntime.dll 文件），并选择“添加” 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-198">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="e92d9-199">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="e92d9-199">Select **OK**.</span></span>

1. <span data-ttu-id="e92d9-200">在“解决方案资源管理器”中，展开“引用”文件夹，并选择“TypeEquivalenceInterface”引用  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-200">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="e92d9-201">在“属性”窗格中，将“嵌入式互操作类型”设置为“True”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-201">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="e92d9-202">在代码编辑器中打开 Program.cs 或 Module1.vb 文件，将其内容替换为以下代码，以便创建客户端程序 ：</span><span class="sxs-lookup"><span data-stu-id="e92d9-202">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

   Module Module1

       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub

   End Module
   ```

1. <span data-ttu-id="e92d9-203">选择“文件” > “保存全部”，或按 Ctrl+Shift+S 来保存文件和项目    。</span><span class="sxs-lookup"><span data-stu-id="e92d9-203">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="e92d9-204">按 Ctrl+F5 生成并运行程序 。</span><span class="sxs-lookup"><span data-stu-id="e92d9-204">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="e92d9-205">请注意，控制台输出返回程序集版本 1.0.0.0。</span><span class="sxs-lookup"><span data-stu-id="e92d9-205">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="e92d9-206">修改接口</span><span class="sxs-lookup"><span data-stu-id="e92d9-206">Modify the interface</span></span>

<span data-ttu-id="e92d9-207">现在，修改接口程序集，并更改其版本。</span><span class="sxs-lookup"><span data-stu-id="e92d9-207">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="e92d9-208">在 Visual Studio 中，选择“文件” > “打开” > 项目/解决方案，并打开 TypeEquivalenceInterface 项目   。</span><span class="sxs-lookup"><span data-stu-id="e92d9-208">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="e92d9-209">在“解决方案资源管理器”中，右键单击 TypeEquivalenceInterface 项目，并选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-209">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="e92d9-210">在“属性”屏幕的左窗格中选择“应用程序”，然后选择“程序集信息”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-210">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="e92d9-211">在“程序集信息”对话框中，将“程序集版本”和“文件版本”值更改为 2.0.0.0，然后选择“确定”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-211">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="e92d9-212">打开 SampleInterface.cs 或 SampleInterface.vb 文件，并将以下代码行添加到 `ISampleInterface` 接口 ：</span><span class="sxs-lookup"><span data-stu-id="e92d9-212">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="e92d9-213">选择“文件” > “保存全部”，或按 Ctrl+Shift+S 来保存文件和项目    。</span><span class="sxs-lookup"><span data-stu-id="e92d9-213">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="e92d9-214">在“解决方案资源管理器”中，右键单击 TypeEquivalenceInterface 项目，然后选择“生成”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-214">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="e92d9-215">编译类库 DLL 文件的新版本，并保存到生成输出路径中。</span><span class="sxs-lookup"><span data-stu-id="e92d9-215">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="e92d9-216">修改运行时类</span><span class="sxs-lookup"><span data-stu-id="e92d9-216">Modify the runtime class</span></span>

<span data-ttu-id="e92d9-217">修改运行时类的同时更新其版本。</span><span class="sxs-lookup"><span data-stu-id="e92d9-217">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="e92d9-218">在 Visual Studio 中，选择“文件” > “打开” > 项目/解决方案，并打开 TypeEquivalenceRuntime 项目   。</span><span class="sxs-lookup"><span data-stu-id="e92d9-218">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="e92d9-219">在“解决方案资源管理器”中，右键单击 TypeEquivalenceRuntime 项目，并选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-219">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="e92d9-220">在“属性”屏幕的左窗格中选择“应用程序”，然后选择“程序集信息”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-220">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="e92d9-221">在“程序集信息”对话框中，将“程序集版本”和“文件版本”值更改为 2.0.0.0，然后选择“确定”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-221">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="e92d9-222">打开 SampleClass.cs 或 SampleClass.vb 文件，并将以下代码添加到 `SampleClass` 类 ：</span><span class="sxs-lookup"><span data-stu-id="e92d9-222">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. <span data-ttu-id="e92d9-223">选择“文件” > “保存全部”，或按 Ctrl+Shift+S 来保存文件和项目    。</span><span class="sxs-lookup"><span data-stu-id="e92d9-223">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="e92d9-224">在“解决方案资源管理器”中，右键单击 TypeEquivalenceRuntime 项目，并选择“生成”  。</span><span class="sxs-lookup"><span data-stu-id="e92d9-224">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="e92d9-225">编译类库 DLL 文件的新版本，并保存到生成输出路径中。</span><span class="sxs-lookup"><span data-stu-id="e92d9-225">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="e92d9-226">运行更新的客户端程序</span><span class="sxs-lookup"><span data-stu-id="e92d9-226">Run the updated client program</span></span>

<span data-ttu-id="e92d9-227">转到生成输出文件夹位置，并运行 TypeEquivalenceClient.exe。</span><span class="sxs-lookup"><span data-stu-id="e92d9-227">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="e92d9-228">请注意，控制台输出现在反映 `TypeEquivalenceRuntime` 程序集的新版本（即 2.0.0.0），而不会重新编译程序。</span><span class="sxs-lookup"><span data-stu-id="e92d9-228">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="e92d9-229">请参阅</span><span class="sxs-lookup"><span data-stu-id="e92d9-229">See also</span></span>

- [<span data-ttu-id="e92d9-230">-link（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="e92d9-230">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="e92d9-231">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e92d9-231">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="e92d9-232">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="e92d9-232">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e92d9-233">编程概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e92d9-233">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="e92d9-234">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="e92d9-234">Assemblies in .NET</span></span>](index.md)
