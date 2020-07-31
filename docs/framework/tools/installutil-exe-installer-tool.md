---
title: Installutil.exe（安装程序工具）
description: 使用 Installutil.exe（安装程序工具）。 此工具可用于通过执行指定程序集中的安装程序组件，安装或卸载服务器资源。
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
ms.openlocfilehash: 042e5f64a7a863173db9c4e601d3152b0df46d97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164441"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="6cc2a-104">Installutil.exe（安装程序工具）</span><span class="sxs-lookup"><span data-stu-id="6cc2a-104">Installutil.exe (Installer Tool)</span></span>

<span data-ttu-id="6cc2a-105">安装程序工具是一个命令行实用工具，你可以通过此工具执行指定程序集中的安装程序组件，从而安装和卸载服务器资源。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-105">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="6cc2a-106">此工具与 <xref:System.Configuration.Install> 命名空间中的类配合使用。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-106">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>

<span data-ttu-id="6cc2a-107">此工具会自动随 Visual Studio 一起安装。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6cc2a-108">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6cc2a-109">有关详细信息，请参阅[命令提示](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="6cc2a-110">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="6cc2a-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="6cc2a-111">语法</span><span class="sxs-lookup"><span data-stu-id="6cc2a-111">Syntax</span></span>

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a><span data-ttu-id="6cc2a-112">参数</span><span class="sxs-lookup"><span data-stu-id="6cc2a-112">Parameters</span></span>

|<span data-ttu-id="6cc2a-113">参数</span><span class="sxs-lookup"><span data-stu-id="6cc2a-113">Argument</span></span>|<span data-ttu-id="6cc2a-114">说明</span><span class="sxs-lookup"><span data-stu-id="6cc2a-114">Description</span></span>|
|--------------|-----------------|
|`assembly`|<span data-ttu-id="6cc2a-115">要在其中执行安装程序组件的程序集的文件名称。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-115">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="6cc2a-116">如果你要通过使用 `/AssemblyName` 选项指定程序集的强名称，则忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-116">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|

<a name="options"></a>

## <a name="options"></a><span data-ttu-id="6cc2a-117">选项</span><span class="sxs-lookup"><span data-stu-id="6cc2a-117">Options</span></span>

|<span data-ttu-id="6cc2a-118">选项</span><span class="sxs-lookup"><span data-stu-id="6cc2a-118">Option</span></span>|<span data-ttu-id="6cc2a-119">描述</span><span class="sxs-lookup"><span data-stu-id="6cc2a-119">Description</span></span>|
|------------|-----------------|
|`/h[elp]`<br /><br /> <span data-ttu-id="6cc2a-120">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="6cc2a-120">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="6cc2a-121">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-121">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="6cc2a-122">`/help` assembly</span><span class="sxs-lookup"><span data-stu-id="6cc2a-122">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="6cc2a-123">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="6cc2a-123">-or-</span></span><br /><br /> <span data-ttu-id="6cc2a-124">`/?` assembly</span><span class="sxs-lookup"><span data-stu-id="6cc2a-124">`/?` *assembly*</span></span>|<span data-ttu-id="6cc2a-125">显示由指定的程序集中的个别安装程序识别的其他选项，以及 InstallUtil.exe 的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-125">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="6cc2a-126">此选项将各安装程序组件的 <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> 属性返回的文本添加到 InstallUtil.exe 的帮助文本。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-126">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|
|<span data-ttu-id="6cc2a-127">`/AssemblyName` "*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="6cc2a-127">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="6cc2a-128">,Version=*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="6cc2a-128">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="6cc2a-129">,Culture=*locale*</span><span class="sxs-lookup"><span data-stu-id="6cc2a-129">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="6cc2a-130">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="6cc2a-130">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="6cc2a-131">指定必须在全局程序集缓存中注册的程序集的强名称。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-131">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="6cc2a-132">必须使用程序集的版本、区域性和公钥标记完全限定程序集名称。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-132">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="6cc2a-133">完全限定名必须用引号括起。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-133">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="6cc2a-134">例如，“myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0”是完全限定的程序集名称。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-134">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|
|<span data-ttu-id="6cc2a-135">`/InstallStateDir=[` directoryName `]`</span><span class="sxs-lookup"><span data-stu-id="6cc2a-135">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="6cc2a-136">指定 .InstallState 文件的目录，其中包含用来卸载程序集的数据。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-136">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="6cc2a-137">默认为包含程序集的目录。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-137">The default is the directory that contains the assembly.</span></span>|
|<span data-ttu-id="6cc2a-138">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="6cc2a-138">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="6cc2a-139">指定在其中记录安装进度的日志文件的名称。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-139">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="6cc2a-140">默认情况下，如果省略 `/LogFile` 选项，则会创建名为 *assemblyname*.InstallLog 的日志文件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-140">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="6cc2a-141">如果省略 *filename*，则不生成任何日志文件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-141">If *filename* is omitted, no log file is generated.</span></span>|
|<span data-ttu-id="6cc2a-142">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="6cc2a-142">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="6cc2a-143">如果为 `true`，则会将输出显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-143">If `true`, displays output to the console.</span></span> <span data-ttu-id="6cc2a-144">如果为 `false`（默认值），则取消将输出显示到控制台。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-144">If `false` (the default), suppresses output to the console.</span></span>|
|`/ShowCallStack`|<span data-ttu-id="6cc2a-145">如果在安装过程中的任何时候出现异常，则将调用堆栈输出到日志文件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-145">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|
|<span data-ttu-id="6cc2a-146">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="6cc2a-146">`/u`[`ninstall`]</span></span>|<span data-ttu-id="6cc2a-147">卸载指定的程序集。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-147">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="6cc2a-148">与其他选项不同，`/u` 选项不论出现在命令行的什么位置，都将应用于所有程序集。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-148">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a><span data-ttu-id="6cc2a-149">其他安装程序选项</span><span class="sxs-lookup"><span data-stu-id="6cc2a-149">Additional Installer Options</span></span>

<span data-ttu-id="6cc2a-150">程序集中使用的独立安装程序可识别除[选项](#options)部分列出的选项之外的选项。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-150">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="6cc2a-151">要了解有关这些选项的信息，可以在命令行中运行带有程序集路径的 InstallUtil.exe 以及 `/?` 或 `/help` 选项。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-151">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="6cc2a-152">要指定这些选项，请将它们与 InstallUtil.exe 可识别的选项一起包含在命令行中。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-152">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc2a-153">由单独的安装程序组件所支持的选项的帮助文本由 <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> 属性返回。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-153">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6cc2a-154">已经在命令行中输入的单个选项可通过编程方式从 <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> 属性进行访问。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-154">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="6cc2a-155">所有选项和命令行参数都将写入到安装日志文件中。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-155">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="6cc2a-156">但是，如果你使用 `/Password` 参数（某些安装程序组件可识别这些参数），密码信息将被替换为八个星号 (\*)，且不会出现在日志文件中。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-156">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cc2a-157">在某些情况下，传递给安装程序的参数可能包含敏感信息或个人身份信息，默认情况下，此信息将写入到纯文本日志文件中。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-157">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="6cc2a-158">要阻止此行为，可以通过在命令行中的 Installutil.exe 后指定 `/LogFile=`（没有 *filename* 参数）来禁止日志文件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-158">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cc2a-159">备注</span><span class="sxs-lookup"><span data-stu-id="6cc2a-159">Remarks</span></span>

<span data-ttu-id="6cc2a-160">.NET Framework 应用程序由传统的程序文件和关联资源组成，如必须在部署应用程序时创建的消息队列、事件日志和性能计数器。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-160">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="6cc2a-161">安装应用程序时可以使用程序集的安装程序组件创建这些资源，而在卸载应用程序时可以使用这些组件删除这些资源。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-161">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="6cc2a-162">Installutil.exe 检测并执行这些安装程序组件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-162">Installutil.exe detects and executes these installer components.</span></span>

<span data-ttu-id="6cc2a-163">可以在同一个命令行中指定多个程序集。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-163">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="6cc2a-164">出现在一个程序集名称前面的任何选项都将应用于该程序集的安装。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-164">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="6cc2a-165">除了 `/u` 和 `/AssemblyName` 之外，选项可以是累积的，但也是可重写的。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-165">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="6cc2a-166">就是说，为一个程序集指定的选项适用于所有后续程序集，除非为该选项指定新值。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-166">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>

<span data-ttu-id="6cc2a-167">如果对某个程序集运行 Installutil.exe 但不指定任何选项，则 Installutil.exe 会将下面三个文件放到该程序集的目录中：</span><span class="sxs-lookup"><span data-stu-id="6cc2a-167">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>

- <span data-ttu-id="6cc2a-168">InstallUtil.InstallLog - 包含安装进度的常规说明。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-168">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>

- <span data-ttu-id="6cc2a-169">*assemblyname*.InstallLog - 包含特定于安装过程的提交阶段的信息。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-169">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="6cc2a-170">关于提交阶段的更多信息，请参见 <xref:System.Configuration.Install.Installer.Commit%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-170">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>

- <span data-ttu-id="6cc2a-171">*assemblyname*.InstallState - 包含用于卸载该程序集的数据。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-171">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>

<span data-ttu-id="6cc2a-172">Installutil.exe 使用反射检查指定的程序集以及查找将 <xref:System.Configuration.Install.Installer> 特性设置为 <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> 的所有 `true` 类型。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-172">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="6cc2a-173">该工具然后对 <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> 类型的每个实例执行 <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> 或 <xref:System.Configuration.Install.Installer> 方法。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-173">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="6cc2a-174">Installutil.exe 以事务性方式执行安装；也就是说，如果有一个程序集未能安装，则 Installutil.exe 会回滚其他所有程序集的安装。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-174">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="6cc2a-175">卸载不是事务性的。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-175">Uninstall is not transactional.</span></span>

<span data-ttu-id="6cc2a-176">Installutil.exe 无法安装或卸载延迟签名的程序集，但可以安装或卸载具有强名称的程序集。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-176">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>

<span data-ttu-id="6cc2a-177">从 .NET Framework 2.0 版开始，32 位版本的公共语言运行时 (CLR) 仅随 32 位版本的安装程序工具一起提供，但 64 位版本的 CLR 随 32 位和 64 位版本的安装程序工具一起提供。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-177">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="6cc2a-178">当使用 64 位 CLR 时，使用 32 位安装程序工具可安装 32 位程序集，使用 64 位安装程序工具可安装 64 位和 Microsoft 中间语言 (MSIL) 程序集。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-178">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="6cc2a-179">这两种版本的安装程序工具的行为方式相同。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-179">Both versions of the Installer tool behave the same.</span></span>

<span data-ttu-id="6cc2a-180">你无法使用 Installutil.exe 来部署使用 C++ 创建的 Windows 服务，因为 Installutil.exe 无法识别 C++ 编辑器生成的嵌入式本机代码。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-180">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="6cc2a-181">如果尝试使用 Installutil.exe 部署 C++ Windows 服务，则会引发异常（如 <xref:System.BadImageFormatException>）。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-181">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="6cc2a-182">要处理这种情况，请将服务代码移到 C++ 模块，然后使用 C# 或 Visual Basic 编写安装程序对象。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-182">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>

## <a name="examples"></a><span data-ttu-id="6cc2a-183">示例</span><span class="sxs-lookup"><span data-stu-id="6cc2a-183">Examples</span></span>

<span data-ttu-id="6cc2a-184">下列命令显示了 InstallUtil.exe 的命令语法和选项的说明。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-184">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>

```console
installutil /?
```

<span data-ttu-id="6cc2a-185">下列命令显示了 InstallUtil.exe 的命令语法和选项的说明。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-185">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="6cc2a-186">如果已向安装程序的 `myAssembly.exe` 属性分配了帮助文本，则它还会在 <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> 中显示安装程序组件支持的选项的说明的列表。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-186">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>

```console
installutil /? myAssembly.exe
```

<span data-ttu-id="6cc2a-187">下面的命令执行 `myAssembly.exe` 程序集中的安装程序组件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-187">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>

```console
installutil myAssembly.exe
```

<span data-ttu-id="6cc2a-188">下面的命令通过使用 `/AssemblyName` 开关和完全限定名执行程序集中的安装程序组件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-188">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="6cc2a-189">以下命令执行一个以文件名指定的程序集和一个以强名称指定的程序集中的安装程序组件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-189">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="6cc2a-190">请注意，以文件名称指定的所有程序集必须在以强名称指定的程序集前面，因为无法重写 `/AssemblyName` 选项。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-190">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="6cc2a-191">下面的命令执行 `myAssembly.exe` 程序集中的卸载程序组件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-191">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>

```console
installutil /u myAssembly.exe
```

<span data-ttu-id="6cc2a-192">以下命令执行程序集 `myAssembly1.exe` 和 `myAssembly2.exe` 中的卸载程序组件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-192">The following command executes the uninstaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

<span data-ttu-id="6cc2a-193">由于 `/u` 选项在命令行中所处的位置不重要，因此这就等效于以下命令。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-193">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

<span data-ttu-id="6cc2a-194">下面的命令执行 `myAssembly.exe` 程序集中的安装程序并指定将进度信息写入到 `myLog.InstallLog` 中。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-194">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

<span data-ttu-id="6cc2a-195">以下命令执行程序集 `myAssembly.exe` 中的安装程序，指定将进度信息写入到 `myLog.InstallLog` 中，并使用安装程序的自定义 `/reg` 选项来指定应对系统注册表进行更新。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-195">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

<span data-ttu-id="6cc2a-196">以下命令执行程序集 `myAssembly.exe` 中的安装程序，使用安装程序的自定义选项 `/email` 来指定用户的电子邮件地址，并禁止输出到日志文件。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-196">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

<span data-ttu-id="6cc2a-197">下面的命令将 `myAssembly.exe` 的安装进度写入到 `myLog.InstallLog` 中，并将 `myTestAssembly.exe` 的进度写入到 `myTestLog.InstallLog` 中。</span><span class="sxs-lookup"><span data-stu-id="6cc2a-197">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a><span data-ttu-id="6cc2a-198">请参阅</span><span class="sxs-lookup"><span data-stu-id="6cc2a-198">See also</span></span>

- <xref:System.Configuration.Install>
- [<span data-ttu-id="6cc2a-199">工具</span><span class="sxs-lookup"><span data-stu-id="6cc2a-199">Tools</span></span>](index.md)
- [<span data-ttu-id="6cc2a-200">命令提示</span><span class="sxs-lookup"><span data-stu-id="6cc2a-200">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
