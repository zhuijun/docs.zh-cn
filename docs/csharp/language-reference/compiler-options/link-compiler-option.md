---
description: -link（C# 编译器选项）
title: -link（C# 编译器选项）
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: f6e654f4a24829de579ac94ef75b1c645fcb1685
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165827"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="9278b-103">-link（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="9278b-103">-link (C# Compiler Options)</span></span>

<span data-ttu-id="9278b-104">使编译器让指定程序集中的 COM 类型信息可供当前正在编译的项目使用。</span><span class="sxs-lookup"><span data-stu-id="9278b-104">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>

## <a name="syntax"></a><span data-ttu-id="9278b-105">语法</span><span class="sxs-lookup"><span data-stu-id="9278b-105">Syntax</span></span>

```console
-link:fileList
// -or-
-l:fileList
```

## <a name="arguments"></a><span data-ttu-id="9278b-106">自变量</span><span class="sxs-lookup"><span data-stu-id="9278b-106">Arguments</span></span>

 `fileList`  
 <span data-ttu-id="9278b-107">必需。</span><span class="sxs-lookup"><span data-stu-id="9278b-107">Required.</span></span> <span data-ttu-id="9278b-108">程序集文件名的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="9278b-108">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="9278b-109">如果文件名包含空格，则将名称括在引号内。</span><span class="sxs-lookup"><span data-stu-id="9278b-109">If the file name contains a space, enclose the name in quotation marks.</span></span>

## <a name="remarks"></a><span data-ttu-id="9278b-110">备注</span><span class="sxs-lookup"><span data-stu-id="9278b-110">Remarks</span></span>

 <span data-ttu-id="9278b-111">`-link` 选项使你可以部署具有嵌入类型信息的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9278b-111">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="9278b-112">应用程序随后可以使用运行时程序集中实现嵌入类型信息的类型，而无需引用运行时程序集。</span><span class="sxs-lookup"><span data-stu-id="9278b-112">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="9278b-113">如果发布了各种版本的运行时程序集，则包含嵌入类型信息的应用程序可以使用各种版本，而无需重新编译。</span><span class="sxs-lookup"><span data-stu-id="9278b-113">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="9278b-114">有关示例，请参阅[演练：嵌入托管程序集中的类型](../../../standard/assembly/embed-types-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9278b-114">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="9278b-115">在使用 COM 互操作时，使用 `-link` 选项会尤其有用。</span><span class="sxs-lookup"><span data-stu-id="9278b-115">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="9278b-116">可以嵌入 COM 类型，以便应用程序在目标计算机上不再需要主互操作程序集 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="9278b-116">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="9278b-117">`-link` 选项指示编译器将引用的互操作程序集中的 COM 类型信息嵌入到生成的已编译代码中。</span><span class="sxs-lookup"><span data-stu-id="9278b-117">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="9278b-118">COM 类型由 CLSID (GUID) 值进行标识。</span><span class="sxs-lookup"><span data-stu-id="9278b-118">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="9278b-119">因此，应用程序可以在安装了具有相同 CLSID 值的相同 COM 类型的目标计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="9278b-119">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="9278b-120">自动执行 Microsoft Office 的应用程序是一个很好的示例。</span><span class="sxs-lookup"><span data-stu-id="9278b-120">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="9278b-121">由于 Office 等应用程序通常在不同版本间保持相同的 CLSID 值，因此只要在目标计算机上安装了 .NET Framework 4 或更高版本，并且应用程序使用引用的 COM 类型中包含的方法、属性或事件，应用程序便可以使用引用的 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="9278b-121">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>

 <span data-ttu-id="9278b-122">`-link` 选项只嵌入接口、结构和委托。</span><span class="sxs-lookup"><span data-stu-id="9278b-122">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="9278b-123">不支持嵌入 COM 类。</span><span class="sxs-lookup"><span data-stu-id="9278b-123">Embedding COM classes is not supported.</span></span>

> [!NOTE]
> <span data-ttu-id="9278b-124">在代码中创建嵌入 COM 类型的实例时，必须使用适当的接口创建该实例。</span><span class="sxs-lookup"><span data-stu-id="9278b-124">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="9278b-125">尝试使用组件类创建嵌入 COM 类型的实例会导致错误。</span><span class="sxs-lookup"><span data-stu-id="9278b-125">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>

 <span data-ttu-id="9278b-126">若要在 Visual Studio 中设置 `-link` 选项，请添加程序集引用并将 `Embed Interop Types` 属性设置为“true”  。</span><span class="sxs-lookup"><span data-stu-id="9278b-126">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="9278b-127">`Embed Interop Types` 属性的默认值为 **false**。</span><span class="sxs-lookup"><span data-stu-id="9278b-127">The default for the `Embed Interop Types` property is **false**.</span></span>

 <span data-ttu-id="9278b-128">如果链接到本身引用了其他 COM 程序集（程序集 B）的 COM 程序集（程序集 A），则在满足以下任一条件时，还必须链接到程序集 B：</span><span class="sxs-lookup"><span data-stu-id="9278b-128">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>

- <span data-ttu-id="9278b-129">程序集 A 中的类型继承自程序集 B 中的类型或实现程序集 B 中的接口。</span><span class="sxs-lookup"><span data-stu-id="9278b-129">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>

- <span data-ttu-id="9278b-130">调用具有程序集 B 中的返回类型或参数类型的字段、属性、事件或方法。</span><span class="sxs-lookup"><span data-stu-id="9278b-130">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>

 <span data-ttu-id="9278b-131">与 [-reference](./reference-compiler-option.md) 编译器选项一样，`-link` 编译器选项使用 Csc.rsp 响应文件，该文件引用常用的 .NET 程序集。</span><span class="sxs-lookup"><span data-stu-id="9278b-131">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET assemblies.</span></span> <span data-ttu-id="9278b-132">如果不希望编译器使用 Csc.rsp 文件，则使用 [-noconfig](./noconfig-compiler-option.md) 编译器选项。</span><span class="sxs-lookup"><span data-stu-id="9278b-132">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>

 <span data-ttu-id="9278b-133">`-link` 的缩写形式是 `-l`。</span><span class="sxs-lookup"><span data-stu-id="9278b-133">The short form of `-link` is `-l`.</span></span>

## <a name="generics-and-embedded-types"></a><span data-ttu-id="9278b-134">泛型类型和嵌入类型</span><span class="sxs-lookup"><span data-stu-id="9278b-134">Generics and Embedded Types</span></span>

 <span data-ttu-id="9278b-135">以下各部分介绍对在嵌入互操作类型的应用程序中使用泛型类型的限制。</span><span class="sxs-lookup"><span data-stu-id="9278b-135">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>

### <a name="generic-interfaces"></a><span data-ttu-id="9278b-136">泛型接口</span><span class="sxs-lookup"><span data-stu-id="9278b-136">Generic Interfaces</span></span>

 <span data-ttu-id="9278b-137">不能使用从互操作程序集中嵌入的泛型接口。</span><span class="sxs-lookup"><span data-stu-id="9278b-137">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="9278b-138">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="9278b-138">This is shown in the following example.</span></span>

 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]

### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="9278b-139">具有泛型参数的类型</span><span class="sxs-lookup"><span data-stu-id="9278b-139">Types That Have Generic Parameters</span></span>

 <span data-ttu-id="9278b-140">对于具有类型是从互操作程序集嵌入的泛型参数的类型，如果该类型来自外部程序集，则无法使用这种类型。</span><span class="sxs-lookup"><span data-stu-id="9278b-140">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="9278b-141">此限制不适用于接口。</span><span class="sxs-lookup"><span data-stu-id="9278b-141">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="9278b-142">例如，考虑在 <xref:Microsoft.Office.Interop.Excel> 程序集中定义的 <xref:Microsoft.Office.Interop.Excel.Range> 接口。</span><span class="sxs-lookup"><span data-stu-id="9278b-142">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="9278b-143">如果某个库从 <xref:Microsoft.Office.Interop.Excel> 程序集嵌入互操作类型，并且公开的一个方法返回具有类型是 <xref:Microsoft.Office.Interop.Excel.Range> 接口的参数的泛型类型，则该方法必须返回泛型接口，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="9278b-143">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>

[!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs)]

 <span data-ttu-id="9278b-144">在下面的示例中，客户端代码可以调用返回 <xref:System.Collections.IList> 泛型接口的方法而不会出现错误。</span><span class="sxs-lookup"><span data-stu-id="9278b-144">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>

 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]

## <a name="example"></a><span data-ttu-id="9278b-145">示例</span><span class="sxs-lookup"><span data-stu-id="9278b-145">Example</span></span>

 <span data-ttu-id="9278b-146">下面的代码编译源文件 `OfficeApp.cs` 并引用来自 `COMData1.dll` 和 `COMData2.dll` 的程序集以生成 `OfficeApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="9278b-146">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>

```csharp
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs
```

## <a name="see-also"></a><span data-ttu-id="9278b-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9278b-147">See also</span></span>

- [<span data-ttu-id="9278b-148">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="9278b-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9278b-149">演练：嵌入托管程序集中的类型</span><span class="sxs-lookup"><span data-stu-id="9278b-149">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="9278b-150">-reference（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="9278b-150">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="9278b-151">-noconfig（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="9278b-151">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="9278b-152">在命令行上使用 csc.exe 生成</span><span class="sxs-lookup"><span data-stu-id="9278b-152">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="9278b-153">互操作性概述</span><span class="sxs-lookup"><span data-stu-id="9278b-153">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
