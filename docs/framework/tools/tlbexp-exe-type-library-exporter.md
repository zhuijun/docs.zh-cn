---
title: Tlbexp.exe（类型库导出程序）
description: 查看 Tlbexp.exe（类型库导出程序）。 此工具生成一个类型库，其中描述在一个公共语言运行时 (CLR) 程序集中定义的类型。
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
ms.openlocfilehash: 3cfaa83590fefe31c437d2ff607fb579aec1da61
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517030"
---
# <a name="tlbexpexe-type-library-exporter"></a><span data-ttu-id="44e0a-104">Tlbexp.exe（类型库导出程序）</span><span class="sxs-lookup"><span data-stu-id="44e0a-104">Tlbexp.exe (Type Library Exporter)</span></span>
<span data-ttu-id="44e0a-105">类型库导出程序生成一个类型库，该类型库描述公共语言运行时程序集中定义的类型。</span><span class="sxs-lookup"><span data-stu-id="44e0a-105">The Type Library Exporter generates a type library that describes the types defined in a common language runtime assembly.</span></span>  
  
 <span data-ttu-id="44e0a-106">此工具会自动随 Visual Studio 一起安装。</span><span class="sxs-lookup"><span data-stu-id="44e0a-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="44e0a-107">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="44e0a-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="44e0a-108">有关详细信息，请参阅[命令提示](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="44e0a-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="44e0a-109">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="44e0a-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e0a-110">语法</span><span class="sxs-lookup"><span data-stu-id="44e0a-110">Syntax</span></span>  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e0a-111">参数</span><span class="sxs-lookup"><span data-stu-id="44e0a-111">Parameters</span></span>  
  
|<span data-ttu-id="44e0a-112">参数</span><span class="sxs-lookup"><span data-stu-id="44e0a-112">Argument</span></span>|<span data-ttu-id="44e0a-113">描述</span><span class="sxs-lookup"><span data-stu-id="44e0a-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="44e0a-114">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="44e0a-114">*assemblyName*</span></span>|<span data-ttu-id="44e0a-115">为其导出类型库的程序集。</span><span class="sxs-lookup"><span data-stu-id="44e0a-115">The assembly for which to export a type library.</span></span>|  
  
|<span data-ttu-id="44e0a-116">选项</span><span class="sxs-lookup"><span data-stu-id="44e0a-116">Option</span></span>|<span data-ttu-id="44e0a-117">描述</span><span class="sxs-lookup"><span data-stu-id="44e0a-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="44e0a-118">/asmpath: directory</span><span class="sxs-lookup"><span data-stu-id="44e0a-118">**/asmpath:** *directory*</span></span>|<span data-ttu-id="44e0a-119">指定要在其中搜索程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="44e0a-119">Specifies the location to search for assemblies.</span></span> <span data-ttu-id="44e0a-120">如果使用此选项，则必须显式指定要在其中搜索所引用的程序集的位置（包括当前目录）。</span><span class="sxs-lookup"><span data-stu-id="44e0a-120">If you use this option, you must explicitly specify the locations to search for referenced assemblies, including the current directory.</span></span><br /><br /> <span data-ttu-id="44e0a-121">当使用 asmpath 选项时，类型库导出程序不会在全局程序集缓存 (GAC) 中查找程序集。</span><span class="sxs-lookup"><span data-stu-id="44e0a-121">When you use the **asmpath** option, the Type Library Exporter will not look for an assembly in the global assembly cache (GAC).</span></span>|  
|<span data-ttu-id="44e0a-122">**/help**</span><span class="sxs-lookup"><span data-stu-id="44e0a-122">**/help**</span></span>|<span data-ttu-id="44e0a-123">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="44e0a-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="44e0a-124">/names: filename</span><span class="sxs-lookup"><span data-stu-id="44e0a-124">**/names:** *filename*</span></span>|<span data-ttu-id="44e0a-125">指定类型库中名称的大小写。</span><span class="sxs-lookup"><span data-stu-id="44e0a-125">Specifies the capitalization of names in a type library.</span></span> <span data-ttu-id="44e0a-126">filename 参数是一个文本文件。</span><span class="sxs-lookup"><span data-stu-id="44e0a-126">The *filename* argument is a text file.</span></span> <span data-ttu-id="44e0a-127">文件中的每一行均指定类型库中一个名称的大小写。</span><span class="sxs-lookup"><span data-stu-id="44e0a-127">Each line in the file specifies the capitalization of one name in the type library.</span></span>|  
|<span data-ttu-id="44e0a-128">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="44e0a-128">**/nologo**</span></span>|<span data-ttu-id="44e0a-129">取消显示 Microsoft 启动版权标志。</span><span class="sxs-lookup"><span data-stu-id="44e0a-129">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="44e0a-130">/oldnames</span><span class="sxs-lookup"><span data-stu-id="44e0a-130">**/oldnames**</span></span>|<span data-ttu-id="44e0a-131">强制 Tlbexp.exe 导出修饰类型名（如果存在类型名冲突）。</span><span class="sxs-lookup"><span data-stu-id="44e0a-131">Forces Tlbexp.exe to export decorated type names if there is a type name conflict.</span></span> <span data-ttu-id="44e0a-132">请注意，这是 .NET Framework 2.0 版之前的版本中的默认行为。</span><span class="sxs-lookup"><span data-stu-id="44e0a-132">Note that this was the default behavior in versions prior to the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="44e0a-133">/out: file</span><span class="sxs-lookup"><span data-stu-id="44e0a-133">**/out:** *file*</span></span>|<span data-ttu-id="44e0a-134">指定要生成的类型库文件的名称。</span><span class="sxs-lookup"><span data-stu-id="44e0a-134">Specifies the name of the type library file to generate.</span></span> <span data-ttu-id="44e0a-135">如果省略该选项，则 Tlbexp.exe 将生成一个与程序集的名称（实际的程序集名称，不一定与包含程序集的文件同名）相同且具有 .tlb 扩展名的类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-135">If you omit this option, Tlbexp.exe generates a type library with the same name as the assembly (the actual assembly name, which might not necessarily be the same as the file containing the assembly) and a .tlb extension.</span></span>|  
|<span data-ttu-id="44e0a-136">/silence: `warningnumber`</span><span class="sxs-lookup"><span data-stu-id="44e0a-136">**/silence:** `warningnumber`</span></span>|<span data-ttu-id="44e0a-137">禁止显示指定的警告。</span><span class="sxs-lookup"><span data-stu-id="44e0a-137">Suppresses the display of the specified warning.</span></span> <span data-ttu-id="44e0a-138">此选项不能与 **/silent** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="44e0a-138">This option cannot be used with **/silent**.</span></span>|  
|<span data-ttu-id="44e0a-139">**/Silent**</span><span class="sxs-lookup"><span data-stu-id="44e0a-139">**/silent**</span></span>|<span data-ttu-id="44e0a-140">取消显示成功消息。</span><span class="sxs-lookup"><span data-stu-id="44e0a-140">Suppresses the display of success messages.</span></span> <span data-ttu-id="44e0a-141">此选项不能与 **/silence** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="44e0a-141">This option cannot be used with **/silence**.</span></span>|  
|<span data-ttu-id="44e0a-142">/tlbreference: typelibraryname</span><span class="sxs-lookup"><span data-stu-id="44e0a-142">**/tlbreference:** *typelibraryname*</span></span>|<span data-ttu-id="44e0a-143">强制 Tlbexp.exe 在不参考注册表的情况下显式解析类型库引用。</span><span class="sxs-lookup"><span data-stu-id="44e0a-143">Forces Tlbexp.exe to explicitly resolve type library references without consulting the registry.</span></span> <span data-ttu-id="44e0a-144">例如，如果程序集 B 引用程序集 A，则可使用此选项来提供显式类型库引用而不依赖于注册表中指定的类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-144">For example, if assembly B references assembly A, you can use this option to provide an explicit type library reference, rather than relying on the type library specified in the registry.</span></span> <span data-ttu-id="44e0a-145">Tlbexp.exe 将执行版本检查以确保类型库版本与程序集版本相匹配；否则将生成错误。</span><span class="sxs-lookup"><span data-stu-id="44e0a-145">Tlbexp.exe performs a version check to ensure that the type library version matches the assembly version; otherwise, it generates an error.</span></span><br /><br /> <span data-ttu-id="44e0a-146">请注意，在将 <xref:System.Runtime.InteropServices.ComImportAttribute> 特性应用于一个接口，然后该接口由另一类型实现的情况下，tlbreference 选项仍咨询注册表。</span><span class="sxs-lookup"><span data-stu-id="44e0a-146">Note that the **tlbreference** option still consults the registry in cases where the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute is applied to an interface that is then implemented by another type.</span></span>|  
|<span data-ttu-id="44e0a-147">/tlbrefpath: path</span><span class="sxs-lookup"><span data-stu-id="44e0a-147">**/tlbrefpath:** *path*</span></span>|<span data-ttu-id="44e0a-148">所引用的类型库的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="44e0a-148">Fully qualified path to a referenced type library.</span></span>|  
|<span data-ttu-id="44e0a-149">/win32</span><span class="sxs-lookup"><span data-stu-id="44e0a-149">**/win32**</span></span>|<span data-ttu-id="44e0a-150">在 64 位计算机上编译时，此选项指定 Tlbexp.exe 生成一个 32 位类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-150">When compiling on a 64-bit computer, this option specifies that Tlbexp.exe generates a 32-bit type library.</span></span>|  
|<span data-ttu-id="44e0a-151">/win64</span><span class="sxs-lookup"><span data-stu-id="44e0a-151">**/win64**</span></span>|<span data-ttu-id="44e0a-152">在 32 位计算机上编译时，此选项指定 Tlbexp.exe 生成一个 64 位类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-152">When compiling on a 32-bit computer, this option specifies that Tlbexp.exe generates a 64-bit type library.</span></span>|  
|<span data-ttu-id="44e0a-153">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="44e0a-153">**/verbose**</span></span>|<span data-ttu-id="44e0a-154">指定详细模式；显示需要为其生成类型库的任何引用程序集的列表。</span><span class="sxs-lookup"><span data-stu-id="44e0a-154">Specifies verbose mode; displays a list of any referenced assemblies for which a type library needs to be generated.</span></span>|  
|<span data-ttu-id="44e0a-155">**/?**</span><span class="sxs-lookup"><span data-stu-id="44e0a-155">**/?**</span></span>|<span data-ttu-id="44e0a-156">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="44e0a-156">Displays command syntax and options for the tool.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="44e0a-157">Tlbexp.exe 的命令行选项不区分大小写，并可以按任何顺序提供。</span><span class="sxs-lookup"><span data-stu-id="44e0a-157">The command-line options for Tlbexp.exe are case-insensitive and can be supplied in any order.</span></span> <span data-ttu-id="44e0a-158">只需指定足够的选项来唯一标识它。</span><span class="sxs-lookup"><span data-stu-id="44e0a-158">You only need to specify enough of the option to uniquely identify it.</span></span> <span data-ttu-id="44e0a-159">例如，/n 等效于 /nologo，/o: outfile.tlb 等效于 /out: outfile.tlb  。</span><span class="sxs-lookup"><span data-stu-id="44e0a-159">For example, **/n** is equivalent to **/nologo**, and **/o:** *outfile.tlb* is equivalent to **/out:** *outfile.tlb*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44e0a-160">备注</span><span class="sxs-lookup"><span data-stu-id="44e0a-160">Remarks</span></span>  
 <span data-ttu-id="44e0a-161">Tlbexp.exe 生成一个类型库，该类型库包含程序集中定义的类型的定义。</span><span class="sxs-lookup"><span data-stu-id="44e0a-161">Tlbexp.exe generates a type library that contains definitions of the types defined in the assembly.</span></span> <span data-ttu-id="44e0a-162">应用程序（如 Visual Basic 6.0）可以使用生成的类型库来绑定到程序集中定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="44e0a-162">Applications such as Visual Basic 6.0 can use the generated type library to bind to the .NET types defined in the assembly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44e0a-163">不能使用 Tlbexp.exe 导出 Windows 元数据 (.winmd) 文件。</span><span class="sxs-lookup"><span data-stu-id="44e0a-163">You cannot use Tlbexp.exe to export Windows metadata (.winmd) files.</span></span> <span data-ttu-id="44e0a-164">不支持导出 Windows 运行时程序集。</span><span class="sxs-lookup"><span data-stu-id="44e0a-164">Exporting Windows Runtime assemblies is not supported.</span></span>  
  
 <span data-ttu-id="44e0a-165">立即转换整个程序集。</span><span class="sxs-lookup"><span data-stu-id="44e0a-165">The entire assembly is converted at once.</span></span> <span data-ttu-id="44e0a-166">不能使用 Tlbexp.exe 生成程序集中定义的类型子集的类型信息。</span><span class="sxs-lookup"><span data-stu-id="44e0a-166">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
 <span data-ttu-id="44e0a-167">不能使用 Tlbexp.exe 从使用[类型库导入程序 (Tlbimp.exe)](tlbimp-exe-type-library-importer.md) 导入的程序集生成类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-167">You cannot use Tlbexp.exe to produce a type library from an assembly that was imported using the [Type Library Importer (Tlbimp.exe)](tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="44e0a-168">相反，应参考用 Tlbimp.exe 导入的原始类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-168">Instead, you should refer to the original type library that was imported with Tlbimp.exe.</span></span> <span data-ttu-id="44e0a-169">你可以从引用程序集（使用 Tlbimp.exe 导入）的程序集导出类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-169">You can export a type library from an assembly that references assemblies that were imported using Tlbimp.exe.</span></span> <span data-ttu-id="44e0a-170">请参见下面的示例部分。</span><span class="sxs-lookup"><span data-stu-id="44e0a-170">See the examples section below.</span></span>  
  
 <span data-ttu-id="44e0a-171">Tlbexp.exe 将生成的类型库置于当前工作目录中或为输出文件指定的目录中。</span><span class="sxs-lookup"><span data-stu-id="44e0a-171">Tlbexp.exe places generated type libraries in the current working directory or the directory specified for the output file.</span></span> <span data-ttu-id="44e0a-172">一个程序集可能会导致生成多个类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-172">A single assembly might cause several type libraries to be generated.</span></span>  
  
 <span data-ttu-id="44e0a-173">Tlbexp.exe 生成类型库，但不注册它。</span><span class="sxs-lookup"><span data-stu-id="44e0a-173">Tlbexp.exe generates a type library but does not register it.</span></span> <span data-ttu-id="44e0a-174">这与[程序集注册工具 (Regasm.exe)](regasm-exe-assembly-registration-tool.md) 不同，后者生成并注册类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-174">This is in contrast to the [Assembly Registration tool (Regasm.exe)](regasm-exe-assembly-registration-tool.md), which both generates and registers a type library.</span></span> <span data-ttu-id="44e0a-175">若要使用 COM 生成和注册类型库，请使用 Regasm.exe。</span><span class="sxs-lookup"><span data-stu-id="44e0a-175">To generate and register a type library with COM, use Regasm.exe.</span></span>  
  
 <span data-ttu-id="44e0a-176">如果未指定 `/win32` 或 `/win64` 选项，则 Tlbexp.exe 将生成一个 32 位或 64 位类型库，该类型库与执行编译所用的计算机的类型（32 位或 64 位计算机）相对应。</span><span class="sxs-lookup"><span data-stu-id="44e0a-176">If you do not specify either the `/win32` or `/win64` option, Tlbexp.exe generates a 32-bit or 64-bit type library that corresponds to the type of computer on which you are performing the compilation (32-bit or 64-bit computer).</span></span> <span data-ttu-id="44e0a-177">为了交叉编译，可以在 32 位计算机上使用 `/win64` 选项来生成 64 位类型库，也可以在 64 位计算机上使用 `/win32` 选项来生成 32 位类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-177">For cross-compilation purposes, you can use the `/win64` option on a 32-bit computer to generate a 64-bit type library and you can use the `/win32` option on a 64-bit computer to generate a 32-bit type library.</span></span> <span data-ttu-id="44e0a-178">在 32 位类型库中，将 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 值设置为 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>。</span><span class="sxs-lookup"><span data-stu-id="44e0a-178">In 32-bit type libraries, the <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> value is set to <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>.</span></span> <span data-ttu-id="44e0a-179">在 64 位类型库中，将 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 值设置为 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>。</span><span class="sxs-lookup"><span data-stu-id="44e0a-179">In 64-bit type libraries, the <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> value is set to <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>.</span></span> <span data-ttu-id="44e0a-180">相应地转换所有数据类型转换（例如，指针大小的数据类型，如 `IntPtr` 和 `UIntPtr`）。</span><span class="sxs-lookup"><span data-stu-id="44e0a-180">All data type transformations (for example, pointer-sized data types such as `IntPtr` and `UIntPtr`) are converted appropriately.</span></span>  
  
 <span data-ttu-id="44e0a-181">如果使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性指定 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> 或 `VT_UNKOWN` 的 `VT_DISPATCH` 值，则 Tlbexp.exe 将忽略随后使用的任何 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> 字段。</span><span class="sxs-lookup"><span data-stu-id="44e0a-181">If you use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> value of `VT_UNKOWN` or `VT_DISPATCH`, Tlbexp.exe ignores any subsequent use of the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> field.</span></span> <span data-ttu-id="44e0a-182">例如，对于以下签名：</span><span class="sxs-lookup"><span data-stu-id="44e0a-182">For example, given the following signatures:</span></span>  
  
```csharp
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 <span data-ttu-id="44e0a-183">生成以下类型库：</span><span class="sxs-lookup"><span data-stu-id="44e0a-183">the following type library is generated:</span></span>  
  
```cpp
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 <span data-ttu-id="44e0a-184">请注意，Tlbexp.exe 忽略 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> 字段。</span><span class="sxs-lookup"><span data-stu-id="44e0a-184">Note that Tlbexp.exe ignores the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> field.</span></span>  
  
 <span data-ttu-id="44e0a-185">由于类型库无法容纳在程序集中找到的所有信息，因此在导出过程中，Tlbexp.exe 可能会放弃一些数据。</span><span class="sxs-lookup"><span data-stu-id="44e0a-185">Because type libraries cannot accommodate all the information found in assemblies, Tlbexp.exe might discard some data during the export process.</span></span> <span data-ttu-id="44e0a-186">有关对转换过程的说明和发出到类型库中的每条信息的源的标识，请参见[有关从程序集转换到类型库的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="44e0a-186">For an explanation of the transformation process and identification of the source of each piece of information emitted to a type library, see the [Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).</span></span>  
  
 <span data-ttu-id="44e0a-187">请注意，类型库导出程序导出具有 <xref:System.TypedReference> 类型的 `VARIANT` 参数的方法，尽管该 <xref:System.TypedReference> 对象在非托管代码中没有意义。</span><span class="sxs-lookup"><span data-stu-id="44e0a-187">Note that the Type Library Exporter exports methods that have <xref:System.TypedReference> parameters as `VARIANT`, even though the <xref:System.TypedReference> object has no meaning in unmanaged code.</span></span> <span data-ttu-id="44e0a-188">在导出具有 <xref:System.TypedReference> 参数的方法时，类型库导出程序不会生成警告或错误，但使用结果类型库的非托管代码将无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="44e0a-188">When you export methods that have <xref:System.TypedReference> parameters, the Type Library Exporter will not generate a warning or error and unmanaged code that uses the resulting type library will not run properly.</span></span>  
  
 <span data-ttu-id="44e0a-189">Microsoft Windows 2000 和更高版本支持类型库导出程序。</span><span class="sxs-lookup"><span data-stu-id="44e0a-189">The Type Library Exporter is supported on Microsoft Windows 2000 and later.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="44e0a-190">示例</span><span class="sxs-lookup"><span data-stu-id="44e0a-190">Examples</span></span>  
 <span data-ttu-id="44e0a-191">下面的命令生成一个与 `myTest.dll` 中找到的程序集同名的类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-191">The following command generates a type library with the same name as the assembly found in `myTest.dll`.</span></span>  
  
```console  
tlbexp myTest.dll  
```  
  
 <span data-ttu-id="44e0a-192">下面的命令生成一个名为 `clipper.tlb` 的类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-192">The following command generates a type library with the name `clipper.tlb`.</span></span>  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 <span data-ttu-id="44e0a-193">下面的示例阐释使用 Tlbexp.exe 从一个程序集导出类型库，该类型库引用使用 Tlbimp.exe 导入的程序集。</span><span class="sxs-lookup"><span data-stu-id="44e0a-193">The following example illustrates using Tlbexp.exe to export a type library from an assembly that references assemblies that were imported using Tlbimp.exe.</span></span>  
  
 <span data-ttu-id="44e0a-194">首先使用 Tlbimp.exe 导入类型库 `myLib.tlb`，然后将其另存为 `myLib.dll`。</span><span class="sxs-lookup"><span data-stu-id="44e0a-194">First use Tlbimp.exe to import the type library `myLib.tlb` and save it as `myLib.dll`.</span></span>  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 <span data-ttu-id="44e0a-195">下面的命令使用 C# 编译器编译 `Sample.dll,`，后者引用前面的示例中创建的 `myLib.dll`。</span><span class="sxs-lookup"><span data-stu-id="44e0a-195">The following command uses the C# compiler to compile the `Sample.dll,` which references `myLib.dll` created in the previous example.</span></span>  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 <span data-ttu-id="44e0a-196">下面的命令为引用 `Sample.dll` 的 `myLib.dll` 生成类型库。</span><span class="sxs-lookup"><span data-stu-id="44e0a-196">The following command generates a type library for `Sample.dll` that references `myLib.dll`.</span></span>  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="44e0a-197">请参阅</span><span class="sxs-lookup"><span data-stu-id="44e0a-197">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [<span data-ttu-id="44e0a-198">工具</span><span class="sxs-lookup"><span data-stu-id="44e0a-198">Tools</span></span>](index.md)
- [<span data-ttu-id="44e0a-199">Regasm.exe（程序集注册工具）</span><span class="sxs-lookup"><span data-stu-id="44e0a-199">Regasm.exe (Assembly Registration Tool)</span></span>](regasm-exe-assembly-registration-tool.md)
- <span data-ttu-id="44e0a-200">[有关从程序集转换到类型库的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="44e0a-200">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>
- [<span data-ttu-id="44e0a-201">Tlbimp.exe（类型库导入程序）</span><span class="sxs-lookup"><span data-stu-id="44e0a-201">Tlbimp.exe (Type Library Importer)</span></span>](tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="44e0a-202">命令提示</span><span class="sxs-lookup"><span data-stu-id="44e0a-202">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
