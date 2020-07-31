---
title: Lc.exe（许可证编译器）
description: 使用 Lc.exe（许可证编译器）。 此工具读取包含授权信息的文本文件，并生成一个二进制文件作为资源嵌入到 CLR 可执行文件中。
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 45a80ba7c3e24c0f419758315b2d2daafd3890f4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164251"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="77a79-104">Lc.exe（许可证编译器）</span><span class="sxs-lookup"><span data-stu-id="77a79-104">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="77a79-105">许可证编译器读取包含授权信息的文本文件，并产生一个可作为资源嵌入到公共语言运行时可执行文件中的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-105">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="77a79-106">每当将一个授权控件添加到窗体中时，Windows 窗体设计器就会自动生成或更新 .licx 文本文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-106">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="77a79-107">作为编译的一部分，项目系统将 .licx 文本文件转换为 .licenses 二进制资源，此资源提供对 .NET 控件授权的支持。</span><span class="sxs-lookup"><span data-stu-id="77a79-107">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="77a79-108">然后该二进制资源将被嵌入到项目输出中。</span><span class="sxs-lookup"><span data-stu-id="77a79-108">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="77a79-109">在生成项目时，如果使用许可证编译器，则不支持在 32 位与 64 位之间进行交叉编译。</span><span class="sxs-lookup"><span data-stu-id="77a79-109">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="77a79-110">这是因为，许可证编译器必须加载程序集，而不允许从 32 位应用程序加载 64 位程序集，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="77a79-110">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="77a79-111">在这种情况下，使用许可证编译器从命令行手动编译许可证，并指定相应的体系结构。</span><span class="sxs-lookup"><span data-stu-id="77a79-111">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="77a79-112">此工具会自动随 Visual Studio 一起安装。</span><span class="sxs-lookup"><span data-stu-id="77a79-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="77a79-113">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="77a79-113">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="77a79-114">有关详细信息，请参阅[命令提示](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="77a79-114">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="77a79-115">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="77a79-115">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a79-116">语法</span><span class="sxs-lookup"><span data-stu-id="77a79-116">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="77a79-117">选项</span><span class="sxs-lookup"><span data-stu-id="77a79-117">Option</span></span>|<span data-ttu-id="77a79-118">说明</span><span class="sxs-lookup"><span data-stu-id="77a79-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="77a79-119">/complist: filename</span><span class="sxs-lookup"><span data-stu-id="77a79-119">**/complist:** *filename*</span></span>|<span data-ttu-id="77a79-120">指定包含授权组件列表的文件名，这些授权组件要包含在 .licenses 文件中。</span><span class="sxs-lookup"><span data-stu-id="77a79-120">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="77a79-121">每个组件用它的全名引用，并且每行只有一个组件。</span><span class="sxs-lookup"><span data-stu-id="77a79-121">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="77a79-122">命令行用户可为项目中的每个窗体指定一个单独的文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-122">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="77a79-123">Lc.exe 接受多个输入文件并产生一个 .licenses 文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-123">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="77a79-124">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="77a79-124">**/h**[**elp**]</span></span>|<span data-ttu-id="77a79-125">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="77a79-125">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="77a79-126">/i: module</span><span class="sxs-lookup"><span data-stu-id="77a79-126">**/i:** *module*</span></span>|<span data-ttu-id="77a79-127">指定模块，这些模块包含 **/complist** 文件中列出的组件。</span><span class="sxs-lookup"><span data-stu-id="77a79-127">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="77a79-128">若要指定多个模块，请使用多个 **/i** 标志。</span><span class="sxs-lookup"><span data-stu-id="77a79-128">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="77a79-129">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="77a79-129">**/nologo**</span></span>|<span data-ttu-id="77a79-130">取消显示 Microsoft 启动版权标志。</span><span class="sxs-lookup"><span data-stu-id="77a79-130">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="77a79-131">/outdir: path</span><span class="sxs-lookup"><span data-stu-id="77a79-131">**/outdir:** *path*</span></span>|<span data-ttu-id="77a79-132">指定用来放置输出 .licenses 文件的目录。</span><span class="sxs-lookup"><span data-stu-id="77a79-132">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="77a79-133">/target: targetPE</span><span class="sxs-lookup"><span data-stu-id="77a79-133">**/target:** *targetPE*</span></span>|<span data-ttu-id="77a79-134">指定为其生成 .licenses 文件的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-134">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="77a79-135">**/v**</span><span class="sxs-lookup"><span data-stu-id="77a79-135">**/v**</span></span>|<span data-ttu-id="77a79-136">指定详细模式；显示编译进度信息。</span><span class="sxs-lookup"><span data-stu-id="77a79-136">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="77a79-137">@ file </span><span class="sxs-lookup"><span data-stu-id="77a79-137">**@** *file*</span></span>|<span data-ttu-id="77a79-138">指定响应 (.rsp) 文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-138">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="77a79-139">**/?**</span><span class="sxs-lookup"><span data-stu-id="77a79-139">**/?**</span></span>|<span data-ttu-id="77a79-140">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="77a79-140">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77a79-141">示例</span><span class="sxs-lookup"><span data-stu-id="77a79-141">Example</span></span>  
  
1. <span data-ttu-id="77a79-142">如果使用的是包含在名为 `HostApp.exe` *的应用程序中的 `Samples.DLL` 中的授权控件 `MyCompany.Samples.LicControl1`，* 则可创建包含以下内容的 `HostAppLic.txt`。</span><span class="sxs-lookup"><span data-stu-id="77a79-142">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="77a79-143">使用以下命令创建名为 `HostApp.exe.licenses` 的 .licenses 文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-143">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="77a79-144">生成将 .licenses 文件作为资源包含在内的 `HostApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="77a79-144">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="77a79-145">如果生成的是 C# 应用程序，则应使用以下命令生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="77a79-145">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="77a79-146">以下命令从由 `myApp.licenses`、`hostapplic.txt` 和 `hostapplic2.txt` 指定的授权组件列表来编译 `hostapplic3.txt`。</span><span class="sxs-lookup"><span data-stu-id="77a79-146">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="77a79-147">`modulesList` 参数指定包含授权组件的模块。</span><span class="sxs-lookup"><span data-stu-id="77a79-147">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="77a79-148">响应文件示例</span><span class="sxs-lookup"><span data-stu-id="77a79-148">Response File Example</span></span>  
 <span data-ttu-id="77a79-149">下面的列表显示响应文件 `response.rsp` 的示例。</span><span class="sxs-lookup"><span data-stu-id="77a79-149">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="77a79-150">有关响应文件的详细信息，请参阅[响应文件](/visualstudio/msbuild/msbuild-response-files)。</span><span class="sxs-lookup"><span data-stu-id="77a79-150">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="77a79-151">下面的命令行使用 `response.rsp` 文件。</span><span class="sxs-lookup"><span data-stu-id="77a79-151">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="77a79-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="77a79-152">See also</span></span>

- [<span data-ttu-id="77a79-153">工具</span><span class="sxs-lookup"><span data-stu-id="77a79-153">Tools</span></span>](index.md)
- [<span data-ttu-id="77a79-154">Al.exe（程序集链接器）</span><span class="sxs-lookup"><span data-stu-id="77a79-154">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="77a79-155">命令提示</span><span class="sxs-lookup"><span data-stu-id="77a79-155">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
