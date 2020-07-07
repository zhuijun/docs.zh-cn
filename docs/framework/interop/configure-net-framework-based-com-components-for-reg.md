---
title: 如何：配置基于 .NET Framework 的 COM 组件以进行免注册激活
description: 配置基于 .NET 的 COM 组件以进行免注册激活。 安装程序需要 Win32 样式的应用程序清单和 .NET 组件清单。
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 5263e042bafdb886b313f05751c29de0f5715211
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622193"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="b095d-104">如何：配置基于 .NET Framework 的 COM 组件以进行免注册激活</span><span class="sxs-lookup"><span data-stu-id="b095d-104">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="b095d-105">基于 .NET Framework 的组件的免注册激活略复杂于 COM 组件的免注册激活。</span><span class="sxs-lookup"><span data-stu-id="b095d-105">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="b095d-106">安装需要两个清单：</span><span class="sxs-lookup"><span data-stu-id="b095d-106">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="b095d-107">COM 应用程序必须具有 Win32 样式的应用程序清单，以标识托管的组件。</span><span class="sxs-lookup"><span data-stu-id="b095d-107">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="b095d-108">基于 .NET Framework 的组件必须具有组件清单，以提供运行时所需的激活信息。</span><span class="sxs-lookup"><span data-stu-id="b095d-108">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="b095d-109">本主题将介绍如何应用程序清单与应用程序关联，如何将组件清单与组件关联，以及如何在程序集中嵌入组件清单。</span><span class="sxs-lookup"><span data-stu-id="b095d-109">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="b095d-110">创建应用程序清单</span><span class="sxs-lookup"><span data-stu-id="b095d-110">Create an application manifest</span></span>  
  
1. <span data-ttu-id="b095d-111">使用 XML 编辑器创建（或修改）COM 应用程序拥有的应用程序清单，该应用程序与一个或多个托管组件进行交互操作。</span><span class="sxs-lookup"><span data-stu-id="b095d-111">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="b095d-112">在文件开头插入以下标准标头：</span><span class="sxs-lookup"><span data-stu-id="b095d-112">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="b095d-113">有关清单元素及其属性的信息，请参阅[应用程序清单](/windows/desktop/SbsCs/application-manifests)。</span><span class="sxs-lookup"><span data-stu-id="b095d-113">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="b095d-114">标识清单的所有者。</span><span class="sxs-lookup"><span data-stu-id="b095d-114">Identify the owner of the manifest.</span></span> <span data-ttu-id="b095d-115">以下示例中，`myComApp` 版本 1 拥有清单文件。</span><span class="sxs-lookup"><span data-stu-id="b095d-115">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. <span data-ttu-id="b095d-116">标识依赖程序集。</span><span class="sxs-lookup"><span data-stu-id="b095d-116">Identify dependent assemblies.</span></span> <span data-ttu-id="b095d-117">以下示例中，`myComApp` 依赖于 `myManagedComp`。</span><span class="sxs-lookup"><span data-stu-id="b095d-117">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="b095d-118">保存并命名清单文件。</span><span class="sxs-lookup"><span data-stu-id="b095d-118">Save and name the manifest file.</span></span> <span data-ttu-id="b095d-119">应用程序清单的名称是程序集可执行文件的名称后加 .manifest 扩展名。</span><span class="sxs-lookup"><span data-stu-id="b095d-119">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="b095d-120">例如，myComApp.exe 的应用程序清单文件名称是 myComApp.exe.manifest。</span><span class="sxs-lookup"><span data-stu-id="b095d-120">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="b095d-121">可在与 COM 应用程序相同的目录中安装应用程序清单。</span><span class="sxs-lookup"><span data-stu-id="b095d-121">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="b095d-122">或者，可将其作为资源添加到应用程序的 .exe 文件。</span><span class="sxs-lookup"><span data-stu-id="b095d-122">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="b095d-123">有关详细信息，请参阅[关于并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)。</span><span class="sxs-lookup"><span data-stu-id="b095d-123">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="b095d-124">创建组件清单</span><span class="sxs-lookup"><span data-stu-id="b095d-124">Create a component manifest</span></span>  
  
1. <span data-ttu-id="b095d-125">使用 XML 编辑器创建组件清单，描述托管程序集。</span><span class="sxs-lookup"><span data-stu-id="b095d-125">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="b095d-126">在文件开头插入以下标准标头：</span><span class="sxs-lookup"><span data-stu-id="b095d-126">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="b095d-127">标识文件的所有者。</span><span class="sxs-lookup"><span data-stu-id="b095d-127">Identify the owner of the file.</span></span> <span data-ttu-id="b095d-128">应用程序清单文件中 `<dependentAssembly>` 元素的 `<assemblyIdentity>` 元素必须与组件清单中的该元素相匹配。</span><span class="sxs-lookup"><span data-stu-id="b095d-128">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="b095d-129">以下示例中，`myManagedComp` 版本 1.2.3.4 拥有清单文件。</span><span class="sxs-lookup"><span data-stu-id="b095d-129">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. <span data-ttu-id="b095d-130">标识程序集中的每个类。</span><span class="sxs-lookup"><span data-stu-id="b095d-130">Identify each class in the assembly.</span></span> <span data-ttu-id="b095d-131">使用 `<clrClass>` 元素来唯一地标识托管程序集中的每个类。</span><span class="sxs-lookup"><span data-stu-id="b095d-131">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="b095d-132">该元素是 `<assembly>` 元素的子元素，具有下表中描述的属性。</span><span class="sxs-lookup"><span data-stu-id="b095d-132">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="b095d-133">特性</span><span class="sxs-lookup"><span data-stu-id="b095d-133">Attribute</span></span>|<span data-ttu-id="b095d-134">描述</span><span class="sxs-lookup"><span data-stu-id="b095d-134">Description</span></span>|<span data-ttu-id="b095d-135">必需</span><span class="sxs-lookup"><span data-stu-id="b095d-135">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="b095d-136">用于指定要激活的类的标识符。</span><span class="sxs-lookup"><span data-stu-id="b095d-136">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="b095d-137">是</span><span class="sxs-lookup"><span data-stu-id="b095d-137">Yes</span></span>|  
    |`description`|<span data-ttu-id="b095d-138">用于通知用户组件相关信息的字符串。</span><span class="sxs-lookup"><span data-stu-id="b095d-138">A string that informs the user about the component.</span></span> <span data-ttu-id="b095d-139">空字符串为默认值。</span><span class="sxs-lookup"><span data-stu-id="b095d-139">An empty string is the default.</span></span>|<span data-ttu-id="b095d-140">否</span><span class="sxs-lookup"><span data-stu-id="b095d-140">No</span></span>|  
    |`name`|<span data-ttu-id="b095d-141">用于表示托管类的字符串。</span><span class="sxs-lookup"><span data-stu-id="b095d-141">A string that represents the managed class.</span></span>|<span data-ttu-id="b095d-142">是</span><span class="sxs-lookup"><span data-stu-id="b095d-142">Yes</span></span>|  
    |`progid`|<span data-ttu-id="b095d-143">用于后期绑定激活的标识符。</span><span class="sxs-lookup"><span data-stu-id="b095d-143">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="b095d-144">否</span><span class="sxs-lookup"><span data-stu-id="b095d-144">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="b095d-145">COM 线程模型。</span><span class="sxs-lookup"><span data-stu-id="b095d-145">The COM threading model.</span></span> <span data-ttu-id="b095d-146">“Both”为默认值。</span><span class="sxs-lookup"><span data-stu-id="b095d-146">"Both" is the default value.</span></span>|<span data-ttu-id="b095d-147">否</span><span class="sxs-lookup"><span data-stu-id="b095d-147">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="b095d-148">指定要使用的公共语言运行时 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="b095d-148">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="b095d-149">如未指定此属性，并且尚未加载 CLR，将使用最近安装的早于 CLR 版本 4 的 CLR 版本加载组件。</span><span class="sxs-lookup"><span data-stu-id="b095d-149">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="b095d-150">如果指定 v1.0.3705、v1.1.4322 或 v2.0.50727，版本将自动向前滚到最近安装的早于 CLR 版本 4 的 CLR 版本（通常为 v2.0.50727）。</span><span class="sxs-lookup"><span data-stu-id="b095d-150">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="b095d-151">如果已加载其他 CLR 版本，并且可在进程内并行加载指定版本，那么将加载指定版本；否则使用已加载的 CLR。</span><span class="sxs-lookup"><span data-stu-id="b095d-151">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="b095d-152">这可能会导致加载失败。</span><span class="sxs-lookup"><span data-stu-id="b095d-152">This might cause a load failure.</span></span>|<span data-ttu-id="b095d-153">否</span><span class="sxs-lookup"><span data-stu-id="b095d-153">No</span></span>|  
    |`tlbid`|<span data-ttu-id="b095d-154">包含有关该类的类型信息的类型库的标识符。</span><span class="sxs-lookup"><span data-stu-id="b095d-154">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="b095d-155">否</span><span class="sxs-lookup"><span data-stu-id="b095d-155">No</span></span>|  
  
     <span data-ttu-id="b095d-156">所有属性标记都区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b095d-156">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="b095d-157">通过使用 OLE/COM ObjectViewer (Oleview.exe) 查看程序集的已导出类型库，可以获取 CLSID、ProgID、线程模型和运行时版本。</span><span class="sxs-lookup"><span data-stu-id="b095d-157">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="b095d-158">以下组件清单标识两个类 - `testClass1` 和 `testClass2`。</span><span class="sxs-lookup"><span data-stu-id="b095d-158">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="b095d-159">保存并命名清单文件。</span><span class="sxs-lookup"><span data-stu-id="b095d-159">Save and name the manifest file.</span></span> <span data-ttu-id="b095d-160">组件清单名称是程序集库名称后加 .manifest 扩展名。</span><span class="sxs-lookup"><span data-stu-id="b095d-160">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="b095d-161">例如，myManagedComp.dll 的名称是 myManagedComp.manifest。</span><span class="sxs-lookup"><span data-stu-id="b095d-161">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="b095d-162">必须将组件清单作为资源嵌入程序集。</span><span class="sxs-lookup"><span data-stu-id="b095d-162">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="b095d-163">将组件清单嵌入托管程序集</span><span class="sxs-lookup"><span data-stu-id="b095d-163">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="b095d-164">创建包含以下语句的资源脚本：</span><span class="sxs-lookup"><span data-stu-id="b095d-164">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="b095d-165">在此语句中，`myManagedComp.manifest` 是正在嵌入的组件清单的名称。</span><span class="sxs-lookup"><span data-stu-id="b095d-165">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="b095d-166">对于此示例，脚本文件名称是 `myresource.rc`。</span><span class="sxs-lookup"><span data-stu-id="b095d-166">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="b095d-167">使用 Microsoft Windows 资源编译器 (rc.exe) 编译脚本。</span><span class="sxs-lookup"><span data-stu-id="b095d-167">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="b095d-168">在命令提示符处，键入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b095d-168">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="b095d-169">Rc.exe 生成 `myresource.res` 资源文件。</span><span class="sxs-lookup"><span data-stu-id="b095d-169">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="b095d-170">再次编译该程序集的源文件，并使用 /win32res 选项指定资源文件：</span><span class="sxs-lookup"><span data-stu-id="b095d-170">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="b095d-171">同样，`myresource.res` 是包含嵌入资源的资源文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b095d-171">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b095d-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="b095d-172">See also</span></span>

- [<span data-ttu-id="b095d-173">免注册 COM 互操作</span><span class="sxs-lookup"><span data-stu-id="b095d-173">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="b095d-174">[免注册 COM 互操作的需求](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b095d-174">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="b095d-175">[将 COM 组件配置为免注册激活](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b095d-175">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="b095d-176">[基于 .NET 组件的免注册激活：演练](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="b095d-176">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
