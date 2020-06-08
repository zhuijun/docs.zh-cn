---
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 6082806591d398aa8b16b44e769a3f8078ce62d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387733"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="407be-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="407be-102">-link (Visual Basic)</span></span>
<span data-ttu-id="407be-103">使编译器让指定程序集中的 COM 类型信息可供当前正在编译的项目使用。</span><span class="sxs-lookup"><span data-stu-id="407be-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407be-104">语法</span><span class="sxs-lookup"><span data-stu-id="407be-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="407be-105">or</span><span class="sxs-lookup"><span data-stu-id="407be-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="407be-106">自变量</span><span class="sxs-lookup"><span data-stu-id="407be-106">Arguments</span></span>  
  
|<span data-ttu-id="407be-107">术语</span><span class="sxs-lookup"><span data-stu-id="407be-107">Term</span></span>|<span data-ttu-id="407be-108">定义</span><span class="sxs-lookup"><span data-stu-id="407be-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="407be-109">必需。</span><span class="sxs-lookup"><span data-stu-id="407be-109">Required.</span></span> <span data-ttu-id="407be-110">程序集文件名的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="407be-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="407be-111">如果文件名包含空格，则将名称括在引号内。</span><span class="sxs-lookup"><span data-stu-id="407be-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="407be-112">备注</span><span class="sxs-lookup"><span data-stu-id="407be-112">Remarks</span></span>  
 <span data-ttu-id="407be-113">`-link` 选项使你可以部署具有嵌入类型信息的应用程序。</span><span class="sxs-lookup"><span data-stu-id="407be-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="407be-114">应用程序随后可以使用运行时程序集中实现嵌入类型信息的类型，而无需引用运行时程序集。</span><span class="sxs-lookup"><span data-stu-id="407be-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="407be-115">如果发布了各种版本的运行时程序集，则包含嵌入类型信息的应用程序可以使用各种版本，而无需重新编译。</span><span class="sxs-lookup"><span data-stu-id="407be-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="407be-116">有关示例，请参阅[演练：嵌入托管程序集中的类型](../../../standard/assembly/embed-types-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="407be-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="407be-117">在使用 COM 互操作时，使用 `-link` 选项会尤其有用。</span><span class="sxs-lookup"><span data-stu-id="407be-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="407be-118">可以嵌入 COM 类型，以便应用程序在目标计算机上不再需要主互操作程序集 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="407be-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="407be-119">`-link` 选项指示编译器将引用的互操作程序集中的 COM 类型信息嵌入到生成的已编译代码中。</span><span class="sxs-lookup"><span data-stu-id="407be-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="407be-120">COM 类型由 CLSID (GUID) 值进行标识。</span><span class="sxs-lookup"><span data-stu-id="407be-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="407be-121">因此，应用程序可以在安装了具有相同 CLSID 值的相同 COM 类型的目标计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="407be-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="407be-122">自动执行 Microsoft Office 的应用程序是一个很好的示例。</span><span class="sxs-lookup"><span data-stu-id="407be-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="407be-123">由于 Office 等应用程序通常在不同版本间保持相同的 CLSID 值，因此只要在目标计算机上安装了 .NET Framework 4 或更高版本，并且应用程序使用引用的 COM 类型中包含的方法、属性或事件，应用程序便可以使用引用的 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="407be-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="407be-124">`-link` 选项只嵌入接口、结构和委托。</span><span class="sxs-lookup"><span data-stu-id="407be-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="407be-125">不支持嵌入 COM 类。</span><span class="sxs-lookup"><span data-stu-id="407be-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="407be-126">在代码中创建嵌入 COM 类型的实例时，必须使用适当的接口创建该实例。</span><span class="sxs-lookup"><span data-stu-id="407be-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="407be-127">尝试使用组件类创建嵌入 COM 类型的实例会导致错误。</span><span class="sxs-lookup"><span data-stu-id="407be-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="407be-128">若要在 Visual Studio 中设置 `-link` 选项，请添加程序集引用并将 `Embed Interop Types` 属性设置为“true”  。</span><span class="sxs-lookup"><span data-stu-id="407be-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="407be-129">`Embed Interop Types` 属性的默认值为 **false**。</span><span class="sxs-lookup"><span data-stu-id="407be-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="407be-130">如果链接到本身引用了其他 COM 程序集（程序集 B）的 COM 程序集（程序集 A），则在满足以下任一条件时，还必须链接到程序集 B：</span><span class="sxs-lookup"><span data-stu-id="407be-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="407be-131">程序集 A 中的类型继承自程序集 B 中的类型或实现程序集 B 中的接口。</span><span class="sxs-lookup"><span data-stu-id="407be-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="407be-132">调用具有程序集 B 中的返回类型或参数类型的字段、属性、事件或方法。</span><span class="sxs-lookup"><span data-stu-id="407be-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="407be-133">使用 [-libpath](libpath.md) 指定一个或多个程序集引用所在的目录。</span><span class="sxs-lookup"><span data-stu-id="407be-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="407be-134">与 [-reference](reference.md) 编译器选项类似，`-link` 编译器选项使用 Vbc.rsp 响应文件，该文件引用常用 .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="407be-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="407be-135">如果不希望编译器使用 Vbc.rsp 文件，则使用 [-noconfig](noconfig.md) 编译器选项。</span><span class="sxs-lookup"><span data-stu-id="407be-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="407be-136">`-link` 的缩写形式是 `-l`。</span><span class="sxs-lookup"><span data-stu-id="407be-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="407be-137">泛型类型和嵌入类型</span><span class="sxs-lookup"><span data-stu-id="407be-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="407be-138">以下各部分介绍对在嵌入互操作类型的应用程序中使用泛型类型的限制。</span><span class="sxs-lookup"><span data-stu-id="407be-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="407be-139">泛型接口</span><span class="sxs-lookup"><span data-stu-id="407be-139">Generic Interfaces</span></span>  
 <span data-ttu-id="407be-140">不能使用从互操作程序集中嵌入的泛型接口。</span><span class="sxs-lookup"><span data-stu-id="407be-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="407be-141">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="407be-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="407be-142">具有泛型参数的类型</span><span class="sxs-lookup"><span data-stu-id="407be-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="407be-143">对于具有类型是从互操作程序集嵌入的泛型参数的类型，如果该类型来自外部程序集，则无法使用这种类型。</span><span class="sxs-lookup"><span data-stu-id="407be-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="407be-144">此限制不适用于接口。</span><span class="sxs-lookup"><span data-stu-id="407be-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="407be-145">例如，考虑在 <xref:Microsoft.Office.Interop.Excel> 程序集中定义的 <xref:Microsoft.Office.Interop.Excel.Range> 接口。</span><span class="sxs-lookup"><span data-stu-id="407be-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="407be-146">如果某个库从 <xref:Microsoft.Office.Interop.Excel> 程序集嵌入互操作类型，并且公开的一个方法返回具有类型是 <xref:Microsoft.Office.Interop.Excel.Range> 接口的参数的泛型类型，则该方法必须返回泛型接口，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="407be-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="407be-147">在下面的示例中，客户端代码可以调用返回 <xref:System.Collections.IList> 泛型接口的方法而不会出现错误。</span><span class="sxs-lookup"><span data-stu-id="407be-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="407be-148">示例</span><span class="sxs-lookup"><span data-stu-id="407be-148">Example</span></span>  
 <span data-ttu-id="407be-149">下面的命令行编译源文件 `OfficeApp.vb` 并引用来自 `COMData1.dll` 和 `COMData2.dll` 的程序集以生成 `OfficeApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="407be-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="407be-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="407be-150">See also</span></span>

- [<span data-ttu-id="407be-151">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="407be-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="407be-152">演练：嵌入托管程序集中的类型</span><span class="sxs-lookup"><span data-stu-id="407be-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="407be-153">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="407be-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="407be-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="407be-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="407be-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="407be-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="407be-156">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="407be-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="407be-157">COM 互操作介绍</span><span class="sxs-lookup"><span data-stu-id="407be-157">Introduction to COM Interop</span></span>](../../programming-guide/com-interop/introduction-to-com-interop.md)
