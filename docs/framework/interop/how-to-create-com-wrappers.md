---
title: 如何：创建 COM 包装
description: 使用 Visual Studio 或 .NET 工具（Tlbimp.exe 和 Regasm.exe）创建组件对象模型 (COM) 包装器。 这两种方法都会生成两种类型的 COM 包装器。
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 286526c710287e6efa3e49a7f7c55e3687076e29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617387"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="867d2-104">如何：创建 COM 包装</span><span class="sxs-lookup"><span data-stu-id="867d2-104">How to: Create COM Wrappers</span></span>

<span data-ttu-id="867d2-105">可以通过使用 Visual Studio 2005 功能或 .NET Framework 工具 Tlbimp.exe 和 Regasm.exe 创建组件对象模型 (COM) 包装器。</span><span class="sxs-lookup"><span data-stu-id="867d2-105">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="867d2-106">这两种方法都会生成两种类型的 COM 包装器：</span><span class="sxs-lookup"><span data-stu-id="867d2-106">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="867d2-107">从类型库中生成一个[运行时可调用包装器](../../standard/native-interop/runtime-callable-wrapper.md)以在托管代码中运行 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="867d2-107">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="867d2-108">生成具有所需注册表设置的一个 [COM 可调用包装器](../../standard/native-interop/com-callable-wrapper.md)以在本机应用程序中运行托管对象。</span><span class="sxs-lookup"><span data-stu-id="867d2-108">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="867d2-109">在 Visual Studio 2005 中，可以将 COM 包装器作为引用添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="867d2-109">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="867d2-110">在托管应用程序中包装 COM 对象</span><span class="sxs-lookup"><span data-stu-id="867d2-110">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="867d2-111">使用 Visual Studio 创建运行时可调用包装器</span><span class="sxs-lookup"><span data-stu-id="867d2-111">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="867d2-112">打开托管应用程序的项目。</span><span class="sxs-lookup"><span data-stu-id="867d2-112">Open the project for your managed application.</span></span>

2. <span data-ttu-id="867d2-113">在“项目”菜单上，单击“显示所有文件” 。</span><span class="sxs-lookup"><span data-stu-id="867d2-113">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="867d2-114">在“项目”菜单上，单击“添加引用” 。</span><span class="sxs-lookup"><span data-stu-id="867d2-114">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="867d2-115">在“添加引用”对话框中，单击“COM”选项卡，选择要使用的组件，然后单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="867d2-115">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="867d2-116">在“解决方案资源管理器”中检查 COM 组件是否已添加到项目的“引用”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="867d2-116">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="867d2-117">现在可以编写代码以访问 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="867d2-117">You can now write code to access the COM object.</span></span> <span data-ttu-id="867d2-118">可以从通过声明对象开始，例如使用适用于 Visual Basic 的 `Imports` 语句或适用于 C# 的 `Using` 语句。</span><span class="sxs-lookup"><span data-stu-id="867d2-118">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="867d2-119">如果要编写 Microsoft Office 组件的程序，请首先安装 [Microsoft Office 主互操作程序集可再发行程序包](https://www.microsoft.com/Download/details.aspx?id=3508)。</span><span class="sxs-lookup"><span data-stu-id="867d2-119">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="867d2-120">使用 .NET Framework 工具创建运行时可调用包装器</span><span class="sxs-lookup"><span data-stu-id="867d2-120">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="867d2-121">运行 [Tlbimp.exe（类型库导入程序）](../tools/tlbimp-exe-type-library-importer.md)工具。</span><span class="sxs-lookup"><span data-stu-id="867d2-121">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="867d2-122">此工具为在原始类型库中定义的类型创建包含运行时元数据的程序集。</span><span class="sxs-lookup"><span data-stu-id="867d2-122">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="867d2-123">在本机应用程序中包装托管对象</span><span class="sxs-lookup"><span data-stu-id="867d2-123">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="867d2-124">使用 Visual Studio 创建 COM 可调用包装器</span><span class="sxs-lookup"><span data-stu-id="867d2-124">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="867d2-125">为要在本机代码中运行的托管类创建类库项目。</span><span class="sxs-lookup"><span data-stu-id="867d2-125">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="867d2-126">类必须具有一个无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="867d2-126">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="867d2-127">在 AssemblyInfo 文件中验证程序集是否具有由四部分构成的完整版本号。</span><span class="sxs-lookup"><span data-stu-id="867d2-127">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="867d2-128">在 Windows 注册表中维护版本控制需要此版本号。</span><span class="sxs-lookup"><span data-stu-id="867d2-128">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="867d2-129">有关版本号的详细信息，请参阅[程序集版本控制](../../standard/assembly/versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="867d2-129">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="867d2-130">在“项目”菜单上，单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="867d2-130">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="867d2-131">单击“编译”选项卡。</span><span class="sxs-lookup"><span data-stu-id="867d2-131">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="867d2-132">选择“为 COM 互操作注册”复选框。</span><span class="sxs-lookup"><span data-stu-id="867d2-132">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="867d2-133">生成项目时，将自动为 COM 互操作注册程序集。</span><span class="sxs-lookup"><span data-stu-id="867d2-133">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="867d2-134">如果要在 Visual Studio 2005 中生成本机应用程序，可以通过单击“项目”菜单上的“添加引用”来使用此程序集 。</span><span class="sxs-lookup"><span data-stu-id="867d2-134">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="867d2-135">使用 .NET Framework 工具创建 COM 可调用包装器</span><span class="sxs-lookup"><span data-stu-id="867d2-135">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="867d2-136">运行 [Regasm.exe（程序集注册工具）](../tools/regasm-exe-assembly-registration-tool.md)工具。</span><span class="sxs-lookup"><span data-stu-id="867d2-136">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="867d2-137">此工具读取程序集元数据，并向注册表添加所需的项。</span><span class="sxs-lookup"><span data-stu-id="867d2-137">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="867d2-138">这样，使 COM 客户端可以透明方式创建 .NET Framework 类。</span><span class="sxs-lookup"><span data-stu-id="867d2-138">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="867d2-139">可以像使用本机 COM 类一样可以使用此程序集。</span><span class="sxs-lookup"><span data-stu-id="867d2-139">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="867d2-140">可以在任何目录中的程序集上运行 Regasm.exe，然后运行 [Gacutil.exe（全局程序集缓存工具）](../tools/gacutil-exe-gac-tool.md)以将其移动到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="867d2-140">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="867d2-141">移动此程序集不会使位置注册表项失效，因为如果未在其他位置找到此程序集，则会始终对全局程序集缓存进行检查。</span><span class="sxs-lookup"><span data-stu-id="867d2-141">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867d2-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="867d2-142">See also</span></span>

- [<span data-ttu-id="867d2-143">运行时可调用包装器</span><span class="sxs-lookup"><span data-stu-id="867d2-143">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="867d2-144">COM 可调用包装器</span><span class="sxs-lookup"><span data-stu-id="867d2-144">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
