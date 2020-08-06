---
title: Regsvcs.exe（.NET 服务安装工具）
description: 使用 Regsvcs.exe（.NET 服务安装工具）。 加载和注册程序集，配置以编程方式添加到类的服务等。
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 6d0090eda764113407e35a3bcec139f1c7cfb050
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517238"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="7702f-104">Regsvcs.exe（.NET 服务安装工具）</span><span class="sxs-lookup"><span data-stu-id="7702f-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="7702f-105">.NET 服务安装工具执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="7702f-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="7702f-106">加载并注册程序集。</span><span class="sxs-lookup"><span data-stu-id="7702f-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="7702f-107">生成、注册类型库并将其安装到指定的 COM+ 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="7702f-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="7702f-108">配置以编程方式添加到类的服务。</span><span class="sxs-lookup"><span data-stu-id="7702f-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="7702f-109">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="7702f-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="7702f-110">有关详细信息，请参阅[命令提示](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="7702f-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="7702f-111">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="7702f-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7702f-112">语法</span><span class="sxs-lookup"><span data-stu-id="7702f-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="7702f-113">参数</span><span class="sxs-lookup"><span data-stu-id="7702f-113">Parameters</span></span>  
  
|<span data-ttu-id="7702f-114">参数</span><span class="sxs-lookup"><span data-stu-id="7702f-114">Argument</span></span>|<span data-ttu-id="7702f-115">说明</span><span class="sxs-lookup"><span data-stu-id="7702f-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7702f-116">assemblyFile.dll</span><span class="sxs-lookup"><span data-stu-id="7702f-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="7702f-117">源程序集文件。</span><span class="sxs-lookup"><span data-stu-id="7702f-117">The source assembly file.</span></span> <span data-ttu-id="7702f-118">此程序集必须用强名称进行签名。</span><span class="sxs-lookup"><span data-stu-id="7702f-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="7702f-119">有关详细信息，请参阅[使用强名称为程序集签名](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="7702f-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="7702f-120">选项</span><span class="sxs-lookup"><span data-stu-id="7702f-120">Option</span></span>|<span data-ttu-id="7702f-121">描述</span><span class="sxs-lookup"><span data-stu-id="7702f-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7702f-122">/appdir: path</span><span class="sxs-lookup"><span data-stu-id="7702f-122">**/appdir:** *path*</span></span>|<span data-ttu-id="7702f-123">指定应用程序的根目录。</span><span class="sxs-lookup"><span data-stu-id="7702f-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="7702f-124">/appname: applicationName</span><span class="sxs-lookup"><span data-stu-id="7702f-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="7702f-125">指定要查找或创建的 COM+ 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="7702f-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="7702f-126">**/c**</span><span class="sxs-lookup"><span data-stu-id="7702f-126">**/c**</span></span>|<span data-ttu-id="7702f-127">创建目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="7702f-127">Creates the target application.</span></span>|  
|<span data-ttu-id="7702f-128">/componly</span><span class="sxs-lookup"><span data-stu-id="7702f-128">**/componly**</span></span>|<span data-ttu-id="7702f-129">只配置组件；忽略方法和接口。</span><span class="sxs-lookup"><span data-stu-id="7702f-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="7702f-130">/exapp</span><span class="sxs-lookup"><span data-stu-id="7702f-130">**/exapp**</span></span>|<span data-ttu-id="7702f-131">指定此工具需要现有应用程序。</span><span class="sxs-lookup"><span data-stu-id="7702f-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="7702f-132">/extlb</span><span class="sxs-lookup"><span data-stu-id="7702f-132">**/extlb**</span></span>|<span data-ttu-id="7702f-133">使用现有类型库。</span><span class="sxs-lookup"><span data-stu-id="7702f-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="7702f-134">/fc</span><span class="sxs-lookup"><span data-stu-id="7702f-134">**/fc**</span></span>|<span data-ttu-id="7702f-135">查找或创建目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="7702f-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="7702f-136">**/help**</span><span class="sxs-lookup"><span data-stu-id="7702f-136">**/help**</span></span>|<span data-ttu-id="7702f-137">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="7702f-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="7702f-138">/noreconfig</span><span class="sxs-lookup"><span data-stu-id="7702f-138">**/noreconfig**</span></span>|<span data-ttu-id="7702f-139">不重新配置现有的目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="7702f-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="7702f-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="7702f-140">**/nologo**</span></span>|<span data-ttu-id="7702f-141">取消显示 Microsoft 启动版权标志。</span><span class="sxs-lookup"><span data-stu-id="7702f-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="7702f-142">/parname: name</span><span class="sxs-lookup"><span data-stu-id="7702f-142">**/parname:** *name*</span></span>|<span data-ttu-id="7702f-143">指定要查找或创建的 COM+ 应用程序的名称或 ID。</span><span class="sxs-lookup"><span data-stu-id="7702f-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="7702f-144">/reconfig</span><span class="sxs-lookup"><span data-stu-id="7702f-144">**/reconfig**</span></span>|<span data-ttu-id="7702f-145">重新配置现有目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="7702f-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="7702f-146">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="7702f-146">This is the default.</span></span>|  
|<span data-ttu-id="7702f-147">/tlb: typelibraryfile</span><span class="sxs-lookup"><span data-stu-id="7702f-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="7702f-148">指定要安装的类型库文件。</span><span class="sxs-lookup"><span data-stu-id="7702f-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="7702f-149">/u</span><span class="sxs-lookup"><span data-stu-id="7702f-149">**/u**</span></span>|<span data-ttu-id="7702f-150">卸载目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="7702f-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="7702f-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="7702f-151">**/quiet**</span></span>|<span data-ttu-id="7702f-152">指定安静模式；取消显示登录和成功消息。</span><span class="sxs-lookup"><span data-stu-id="7702f-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="7702f-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="7702f-153">**/?**</span></span>|<span data-ttu-id="7702f-154">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="7702f-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7702f-155">备注</span><span class="sxs-lookup"><span data-stu-id="7702f-155">Remarks</span></span>  
 <span data-ttu-id="7702f-156">Regsvcs.exe 需要由 assemblyFile.dll 指定的源程序集文件。</span><span class="sxs-lookup"><span data-stu-id="7702f-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="7702f-157">此程序集必须用强名称进行签名。</span><span class="sxs-lookup"><span data-stu-id="7702f-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="7702f-158">有关强名称签名的更多信息，请参阅[使用强名称为程序集签名](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="7702f-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="7702f-159">目标应用程序的名称和类型库文件的名称都是可选的。</span><span class="sxs-lookup"><span data-stu-id="7702f-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="7702f-160">如果 applicationName 参数尚不存在，则该参数可从源程序集文件生成并且将由 Regsvcs.exe 创建。</span><span class="sxs-lookup"><span data-stu-id="7702f-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="7702f-161">typelibraryfile 参数可以指定类型库名称。</span><span class="sxs-lookup"><span data-stu-id="7702f-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="7702f-162">如果未指定类型库名称，默认情况下，Regsvcs.exe 将使用程序集名称。</span><span class="sxs-lookup"><span data-stu-id="7702f-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="7702f-163">当 Regsvcs.exe 注册组件的方法时，它需要遵从那些方法的[要求](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100))和[链接要求](../misc/link-demands.md)。</span><span class="sxs-lookup"><span data-stu-id="7702f-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="7702f-164">因为该工具在完全受信任的环境中执行，所以大多数权限要求都会成功。</span><span class="sxs-lookup"><span data-stu-id="7702f-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="7702f-165">但是，如果组件中的方法受 <xref:System.Security.Permissions.StrongNameIdentityPermission> 或 <xref:System.Security.Permissions.PublisherIdentityPermission> 的要求或链接要求保护，则 Regsvcs.exe 无法注册这些组件。</span><span class="sxs-lookup"><span data-stu-id="7702f-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="7702f-166">你必须在本地计算机上具有管理特权才能使用 Regsvcs.exe。</span><span class="sxs-lookup"><span data-stu-id="7702f-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="7702f-167">如果 Regsvcs.exe 在执行上述任何操作时失败，它将显示相应的错误信息。</span><span class="sxs-lookup"><span data-stu-id="7702f-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7702f-168">示例</span><span class="sxs-lookup"><span data-stu-id="7702f-168">Examples</span></span>  
 <span data-ttu-id="7702f-169">下面的命令将 `myTest.dll` 中包含的所有公共类添加到 `myTargetApp`（一个现有的 COM+ 应用程序）中，同时生成 `myTest.tlb` 类型库。</span><span class="sxs-lookup"><span data-stu-id="7702f-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="7702f-170">下面的命令将 `myTest.dll` 中包含的所有公共类添加到 `myTargetApp`（一个现有的 COM+ 应用程序）中，同时生成 `newTest.tlb` 类型库。</span><span class="sxs-lookup"><span data-stu-id="7702f-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="7702f-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="7702f-171">See also</span></span>

- [<span data-ttu-id="7702f-172">工具</span><span class="sxs-lookup"><span data-stu-id="7702f-172">Tools</span></span>](index.md)
- [<span data-ttu-id="7702f-173">如何：使用强名称为程序集签名</span><span class="sxs-lookup"><span data-stu-id="7702f-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="7702f-174">命令提示</span><span class="sxs-lookup"><span data-stu-id="7702f-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
