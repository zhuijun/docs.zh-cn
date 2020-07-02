---
title: XAML 浏览器应用程序概述
description: 了解 XAML 浏览器应用程序如何结合 Windows Presentation Foundation （WPF）中的 Web 应用程序和丰富客户端应用程序的功能。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: 3395445dd5639e25f62aeef09d070e326704ed40
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617907"
---
# <a name="wpf-xaml-browser-applications-overview"></a><span data-ttu-id="3a450-103">WPF XAML 浏览器应用程序概述</span><span class="sxs-lookup"><span data-stu-id="3a450-103">WPF XAML Browser Applications Overview</span></span>
<a name="introduction"></a><span data-ttu-id="3a450-104">XAML 浏览器应用程序（Xbap）结合了 Web 应用程序和丰富客户端应用程序的功能。</span><span class="sxs-lookup"><span data-stu-id="3a450-104">XAML browser applications (XBAPs) combines features of both Web applications and rich-client applications.</span></span> <span data-ttu-id="3a450-105">与 Web 应用程序类似，可以将 XBAP 部署到 Web 服务器并从 Internet Explorer 或 Firefox 启动。</span><span class="sxs-lookup"><span data-stu-id="3a450-105">Like Web applications, XBAPs can be deployed to a Web server and started from Internet Explorer or Firefox.</span></span> <span data-ttu-id="3a450-106">与胖客户端应用程序一样，Xbap 可以利用 WPF 的功能。</span><span class="sxs-lookup"><span data-stu-id="3a450-106">Like rich-client applications, XBAPs can take advantage of the capabilities of WPF.</span></span> <span data-ttu-id="3a450-107">开发 XBAP 也与开发丰富客户端类似。</span><span class="sxs-lookup"><span data-stu-id="3a450-107">Developing XBAPs is also similar to rich-client development.</span></span> <span data-ttu-id="3a450-108">本主题提供简单、高级的 XBAP 开发简介，并介绍 XBAP 开发与标准的丰富客户端开发的不同之处。</span><span class="sxs-lookup"><span data-stu-id="3a450-108">This topic provides a simple, high-level introduction to XBAP development and describes where XBAP development differs from standard rich-client development.</span></span>

 <span data-ttu-id="3a450-109">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="3a450-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="3a450-110">创建新的 XAML 浏览器应用程序 (XBAP)</span><span class="sxs-lookup"><span data-stu-id="3a450-110">Creating a New XAML Browser Application (XBAP)</span></span>](#creating_a_new_xaml_browser_application_xbap)

- [<span data-ttu-id="3a450-111">部署 XBAP</span><span class="sxs-lookup"><span data-stu-id="3a450-111">Deploying an XBAP</span></span>](#deploying_a_xbap)

- [<span data-ttu-id="3a450-112">与宿主网页通信</span><span class="sxs-lookup"><span data-stu-id="3a450-112">Communicating with the Host Web Page</span></span>](#communicating_with_the_host_web_page)

- [<span data-ttu-id="3a450-113">XBAP 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="3a450-113">XBAP Security Considerations</span></span>](#xbap_security_considerations)

- [<span data-ttu-id="3a450-114">XBAP 启动时间性能注意事项</span><span class="sxs-lookup"><span data-stu-id="3a450-114">XBAP Start Time Performance Considerations</span></span>](#xbap_start_time_performance_considerations)

<a name="creating_a_new_xaml_browser_application_xbap"></a>
## <a name="creating-a-new-xaml-browser-application-xbap"></a><span data-ttu-id="3a450-115">创建新的 XAML 浏览器应用程序 (XBAP)</span><span class="sxs-lookup"><span data-stu-id="3a450-115">Creating a New XAML Browser Application (XBAP)</span></span>
 <span data-ttu-id="3a450-116">创建新的 XBAP 项目的最简单方法是使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3a450-116">The simplest way to create a new XBAP project is with Visual Studio.</span></span> <span data-ttu-id="3a450-117">创建新项目时，从模板列表中选择“WPF 浏览器应用程序”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3a450-117">When creating a new project, select **WPF Browser Application** from the list of templates.</span></span> <span data-ttu-id="3a450-118">有关详细信息，请参阅[如何：创建新的 WPF 浏览器应用程序项目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="3a450-118">For more information, see [How to: Create a New WPF Browser Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).</span></span>

 <span data-ttu-id="3a450-119">运行 XBAP 项目时，它将在浏览器窗口而不是在单独的窗口中打开。</span><span class="sxs-lookup"><span data-stu-id="3a450-119">When you run the XBAP project, it opens in a browser window instead of a stand-alone window.</span></span> <span data-ttu-id="3a450-120">当你从 Visual Studio 调试 XBAP 时，应用程序将以 Internet 区域权限运行，因此，如果超出这些权限，则会引发安全异常。</span><span class="sxs-lookup"><span data-stu-id="3a450-120">When you debug the XBAP from Visual Studio, the application runs with Internet zone permission and will therefore throw security exceptions if those permissions are exceeded.</span></span> <span data-ttu-id="3a450-121">有关详细信息，请参阅[安全性](../security-wpf.md)和 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="3a450-121">For more information, see [Security](../security-wpf.md) and [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3a450-122">如果不使用 Visual Studio 进行开发，或想要了解有关项目文件的详细信息，请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="3a450-122">If you are not developing with Visual Studio or want to learn more about the project files, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>

<a name="deploying_a_xbap"></a>
## <a name="deploying-an-xbap"></a><span data-ttu-id="3a450-123">部署 XBAP</span><span class="sxs-lookup"><span data-stu-id="3a450-123">Deploying an XBAP</span></span>
 <span data-ttu-id="3a450-124">生成 XBAP 时，输出将包括以下三个文件：</span><span class="sxs-lookup"><span data-stu-id="3a450-124">When you build an XBAP, the output includes the following three files:</span></span>

|<span data-ttu-id="3a450-125">文件</span><span class="sxs-lookup"><span data-stu-id="3a450-125">File</span></span>|<span data-ttu-id="3a450-126">描述</span><span class="sxs-lookup"><span data-stu-id="3a450-126">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="3a450-127">可执行文件 (.exe)</span><span class="sxs-lookup"><span data-stu-id="3a450-127">Executable (.exe)</span></span>|<span data-ttu-id="3a450-128">此文件包含已编译的代码且具有 .exe 扩展名。</span><span class="sxs-lookup"><span data-stu-id="3a450-128">This contains the compiled code and has an .exe extension.</span></span>|
|<span data-ttu-id="3a450-129">应用程序清单 (.manifest)</span><span class="sxs-lookup"><span data-stu-id="3a450-129">Application manifest (.manifest)</span></span>|<span data-ttu-id="3a450-130">此文件包含与应用程序关联的元数据且具有 .manifest 扩展名。</span><span class="sxs-lookup"><span data-stu-id="3a450-130">This contains metadata associated with the application and has a .manifest extension.</span></span>|
|<span data-ttu-id="3a450-131">部署清单 (.xbap)</span><span class="sxs-lookup"><span data-stu-id="3a450-131">Deployment manifest (.xbap)</span></span>|<span data-ttu-id="3a450-132">此文件包含 ClickOnce 用于部署应用程序并具有 xbap 扩展名的信息。</span><span class="sxs-lookup"><span data-stu-id="3a450-132">This file contains the information that ClickOnce uses to deploy the application and has the .xbap extension.</span></span>|

 <span data-ttu-id="3a450-133">将 Xbap 部署到 Web 服务器，例如 Microsoft Internet Information Services （IIS）5.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="3a450-133">You deploy XBAPs to a Web server, for example Microsoft Internet Information Services (IIS) 5.0 or later versions.</span></span> <span data-ttu-id="3a450-134">无需在 Web 服务器上安装 .NET Framework，但必须注册 WPF 多用途 Internet 邮件扩展（MIME）类型和文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="3a450-134">You do not have to install the .NET Framework on the Web server, but you do have to register the WPF Multipurpose Internet Mail Extensions (MIME) types and file name extensions.</span></span> <span data-ttu-id="3a450-135">有关详细信息，请参阅[配置 IIS 5.0 和 IIS 6.0 以部署 WPF 应用程序](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="3a450-135">For more information, see [Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).</span></span>

 <span data-ttu-id="3a450-136">若要将 XBAP 准备好进行部署，请将 .exe 和关联的清单复制到 Web 服务器。</span><span class="sxs-lookup"><span data-stu-id="3a450-136">To prepare your XBAP for deployment, copy the .exe and the associated manifests to the Web server.</span></span> <span data-ttu-id="3a450-137">创建包含超链接的 HTML 页以打开部署清单，即扩展名为 .xbap 的文件。</span><span class="sxs-lookup"><span data-stu-id="3a450-137">Create an HTML page that contains a hyperlink to open the deployment manifest, which is the file that has the .xbap extension.</span></span> <span data-ttu-id="3a450-138">当用户单击到 xbap 文件的链接时，ClickOnce 会自动处理下载和启动应用程序的机制。</span><span class="sxs-lookup"><span data-stu-id="3a450-138">When the user clicks the link to the .xbap file, ClickOnce automatically handles the mechanics of downloading and starting the application.</span></span> <span data-ttu-id="3a450-139">下面的代码示例显示包含指向 XBAP 的超链接的 HTML 页面。</span><span class="sxs-lookup"><span data-stu-id="3a450-139">The following example code shows an HTML page that contains a hyperlink that points to an XBAP.</span></span>

```html
<html>
    <head></head>
    <body>
        <a href="XbapEx.xbap">Click this link to launch the application</a>
    </body>
</html>
```

 <span data-ttu-id="3a450-140">还可以在网页框架中承载 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-140">You can also host an XBAP in the frame of a Web page.</span></span> <span data-ttu-id="3a450-141">创建具有一个或多个框架的网页。</span><span class="sxs-lookup"><span data-stu-id="3a450-141">Create a Web page with one or more frames.</span></span> <span data-ttu-id="3a450-142">将框架的源属性设置为部署清单文件。</span><span class="sxs-lookup"><span data-stu-id="3a450-142">Set the source property of a frame to the deployment manifest file.</span></span> <span data-ttu-id="3a450-143">如果想要使用内置机制在宿主网页和 XBAP 之间进行通信，则必须在框架中承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="3a450-143">If you want to use the built-in mechanism to communicate between the hosting Web page and the XBAP, you must host the application in a frame.</span></span> <span data-ttu-id="3a450-144">下面的示例代码演示了具有两个框架的 HTML 页面，第二个框架的源设置为 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-144">The following example code shows an HTML page with two frames, the source for the second frame is set to an XBAP.</span></span>

```html
<html>
    <head>
        <title>A page with frames</title>
    </head>
    <frameset cols="50%,50%">
        <frame src="introduction.htm">
        <frame src="XbapEx.xbap">
    </frameset>
</html>
```

### <a name="clearing-cached-xbaps"></a><span data-ttu-id="3a450-145">清除缓存的 XBAP</span><span class="sxs-lookup"><span data-stu-id="3a450-145">Clearing Cached XBAPs</span></span>
 <span data-ttu-id="3a450-146">在某些情况下，重新生成并启动 XBAP 后，可能会发现打开了早期版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-146">In some situations after rebuilding and starting your XBAP, you may find that an earlier version of the XBAP is opened.</span></span> <span data-ttu-id="3a450-147">例如，当 XBAP 程序集版本号是静态的，并从命令行启动 XBAP 时，可能会出现此行为。</span><span class="sxs-lookup"><span data-stu-id="3a450-147">For example, this behavior may occur when your XBAP assembly version number is static and you start the XBAP from the command line.</span></span> <span data-ttu-id="3a450-148">在这种情况下，由于缓存的版本（以前启动的版本）和新版本的版本号相同，因此不会下载 XBAP 的新版本。</span><span class="sxs-lookup"><span data-stu-id="3a450-148">In this case, because the version number between the cached version (the version that was previously started) and the new version remains the same, the new version of the XBAP is not downloaded.</span></span> <span data-ttu-id="3a450-149">而会加载缓存的版本。</span><span class="sxs-lookup"><span data-stu-id="3a450-149">Instead, the cached version is loaded.</span></span>

 <span data-ttu-id="3a450-150">在这些情况下，可以在命令提示符下使用**Mage**命令（随 Visual Studio 或 Windows SDK 一起安装）删除缓存版本。</span><span class="sxs-lookup"><span data-stu-id="3a450-150">In these situations, you can remove the cached version by using the **Mage** command (installed with Visual Studio or the Windows SDK) at the command prompt.</span></span> <span data-ttu-id="3a450-151">以下命令可清除应用程序缓存。</span><span class="sxs-lookup"><span data-stu-id="3a450-151">The following command clears the application cache.</span></span>

 ```console
 Mage.exe -cc
 ```

 <span data-ttu-id="3a450-152">此命令可保证启动最新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-152">This command guarantees that the latest version of your XBAP is started.</span></span> <span data-ttu-id="3a450-153">在 Visual Studio 中调试应用程序时，应启动最新版本的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-153">When you debug your application in Visual Studio, the latest version of your XBAP should be started.</span></span> <span data-ttu-id="3a450-154">一般情况下，应在每次生成时更新部署版本号。</span><span class="sxs-lookup"><span data-stu-id="3a450-154">In general, you should update your deployment version number with each build.</span></span> <span data-ttu-id="3a450-155">有关 Mage 的详细信息，请参阅 [Mage.exe（清单生成和编辑工具）](../../tools/mage-exe-manifest-generation-and-editing-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="3a450-155">For more information about Mage, see [Mage.exe (Manifest Generation and Editing Tool)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).</span></span>

<a name="communicating_with_the_host_web_page"></a>
## <a name="communicating-with-the-host-web-page"></a><span data-ttu-id="3a450-156">与宿主网页通信</span><span class="sxs-lookup"><span data-stu-id="3a450-156">Communicating with the Host Web Page</span></span>
 <span data-ttu-id="3a450-157">当在 HTML 框架中承载应用程序时，可以与包含 XBAP 的网页进行通信。</span><span class="sxs-lookup"><span data-stu-id="3a450-157">When the application is hosted in an HTML frame, you can communicate with the Web page that contains the XBAP.</span></span> <span data-ttu-id="3a450-158">可以通过检索的属性来执行此操作 <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> <xref:System.Windows.Interop.BrowserInteropHelper> 。</span><span class="sxs-lookup"><span data-stu-id="3a450-158">You do this by retrieving the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> property of <xref:System.Windows.Interop.BrowserInteropHelper>.</span></span> <span data-ttu-id="3a450-159">此属性返回一个表示 HTML 窗口的脚本对象。</span><span class="sxs-lookup"><span data-stu-id="3a450-159">This property returns a script object that represents the HTML window.</span></span> <span data-ttu-id="3a450-160">然后可以通过使用常规的点语法访问 [window object](https://developer.mozilla.org/en-US/docs/Web/API/Window)（window 对象）上的属性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="3a450-160">You can then access the properties, methods, and events on the [window object](https://developer.mozilla.org/en-US/docs/Web/API/Window) by using regular dot syntax.</span></span> <span data-ttu-id="3a450-161">还可以访问脚本方法和全局变量。</span><span class="sxs-lookup"><span data-stu-id="3a450-161">You can also access script methods and global variables.</span></span> <span data-ttu-id="3a450-162">以下示例演示如何检索脚本对象和关闭浏览器。</span><span class="sxs-lookup"><span data-stu-id="3a450-162">The following example shows how to retrieve the script object and close the browser.</span></span>

 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]

### <a name="debugging-xbaps-that-use-hostscript"></a><span data-ttu-id="3a450-163">调试使用 HostScript 的 XBAP</span><span class="sxs-lookup"><span data-stu-id="3a450-163">Debugging XBAPs that Use HostScript</span></span>
 <span data-ttu-id="3a450-164">如果 XBAP 使用对象与 <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> HTML 窗口通信，则在 Visual Studio 中运行和调试应用程序时必须指定两个设置。</span><span class="sxs-lookup"><span data-stu-id="3a450-164">If your XBAP uses the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> object to communicate with the HTML window, there are two settings that you must specify to run and debug the application in Visual Studio.</span></span> <span data-ttu-id="3a450-165">应用程序必须有权访问其源站点，并且必须使用包含 XBAP 的 HTML 页启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="3a450-165">The application must have access to its site of origin and you must start the application with the HTML page that contains the XBAP.</span></span> <span data-ttu-id="3a450-166">以下步骤介绍如何检查这两个设置：</span><span class="sxs-lookup"><span data-stu-id="3a450-166">The following steps describe how to check these two settings:</span></span>

1. <span data-ttu-id="3a450-167">在 Visual Studio 中，打开项目属性。</span><span class="sxs-lookup"><span data-stu-id="3a450-167">In Visual Studio, open the project properties.</span></span>

2. <span data-ttu-id="3a450-168">在“**安全**”选项卡上，单击“**高级**”。</span><span class="sxs-lookup"><span data-stu-id="3a450-168">On the **Security** tab, click **Advanced**.</span></span>

     <span data-ttu-id="3a450-169">将出现高级安全设置对话框。</span><span class="sxs-lookup"><span data-stu-id="3a450-169">The Advanced Security Settings dialog box appears.</span></span>

3. <span data-ttu-id="3a450-170">请确保选中“授予应用程序对其源站点的访问权”\*\*\*\* 复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3a450-170">Make sure that the **Grant the application access to its site of origin** check box is checked and then click **OK**.</span></span>

4. <span data-ttu-id="3a450-171">在“调试”\*\*\*\* 选项卡上，选择“使用 URL 启动浏览器”\*\*\*\* 选项，然后指定包含 XBAP 的 HTML 页的 URL。</span><span class="sxs-lookup"><span data-stu-id="3a450-171">On the **Debug** tab, select the **Start browser with URL** option and specify the URL for the HTML page that contains the XBAP.</span></span>

5. <span data-ttu-id="3a450-172">在 Internet Explorer 中，单击“工具”\*\*\*\* 按钮，然后选择“Internet 选项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3a450-172">In Internet Explorer, click the **Tools** button and then select **Internet Options**.</span></span>

     <span data-ttu-id="3a450-173">将显示“Internet 选项”对话框。</span><span class="sxs-lookup"><span data-stu-id="3a450-173">The Internet Options dialog box appears.</span></span>

6. <span data-ttu-id="3a450-174">单击“高级”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3a450-174">Click the **Advanced** tab.</span></span>

7. <span data-ttu-id="3a450-175">在“安全性”\*\*\*\* 下面的“设置”\*\*\*\* 列表中，选中“允许活动内容在我的计算机上的文件中运行”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="3a450-175">In the **Settings** list under **Security**, check the **Allow active content to run in files on My Computer** check box.</span></span>

8. <span data-ttu-id="3a450-176">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3a450-176">Click **OK**.</span></span>

     <span data-ttu-id="3a450-177">重启 Internet Explorer 后更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="3a450-177">The changes will take effect after you restart Internet Explorer.</span></span>

> [!CAUTION]
> <span data-ttu-id="3a450-178">在 Internet Explorer 中启用活动内容可能会给计算机带来风险。</span><span class="sxs-lookup"><span data-stu-id="3a450-178">Enabling active content in Internet Explorer may put your computer at risk.</span></span> <span data-ttu-id="3a450-179">如果您不想更改您的 Internet Explorer 安全设置，则可以从服务器启动 HTML 页面，并将 Visual Studio 调试器附加到该进程。</span><span class="sxs-lookup"><span data-stu-id="3a450-179">If you do not want to change your Internet Explorer security settings, you can launch the HTML page from a server and attach the Visual Studio debugger to the process.</span></span>

<a name="xbap_security_considerations"></a>
## <a name="xbap-security-considerations"></a><span data-ttu-id="3a450-180">XBAP 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="3a450-180">XBAP Security Considerations</span></span>
 <span data-ttu-id="3a450-181">通常在被限制到 Internet 区域权限集的部分信任的安全沙盒中执行 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-181">XBAPs typically execute in a partial-trust security sandbox that is restricted to the Internet zone permission set.</span></span> <span data-ttu-id="3a450-182">因此，你的实现必须支持 Internet 区域中支持的 WPF 元素的子集，或者必须提升应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="3a450-182">Consequently, your implementation must support the subset of WPF elements that are supported in the Internet zone or you must elevate the permissions of your application.</span></span> <span data-ttu-id="3a450-183">有关详细信息，请参阅[安全性](../security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="3a450-183">For more information, see [Security](../security-wpf.md).</span></span>

 <span data-ttu-id="3a450-184">在 <xref:System.Windows.Controls.WebBrowser> 应用程序中使用控件时，WPF 会在内部实例化本机 WebBrowser ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="3a450-184">When you use a <xref:System.Windows.Controls.WebBrowser> control in your application, WPF internally instantiates the native WebBrowser ActiveX control.</span></span> <span data-ttu-id="3a450-185">如果应用程序是 Internet Explorer 中运行的部分信任的 XBAP，则 ActiveX 控件会在 Internet Explorer 进程的专用线程中运行。</span><span class="sxs-lookup"><span data-stu-id="3a450-185">When your application is a partial-trust XBAP running in Internet Explorer, the ActiveX control runs in a dedicated thread of the Internet Explorer process.</span></span> <span data-ttu-id="3a450-186">因此，存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="3a450-186">Therefore, the following limitations apply:</span></span>

- <span data-ttu-id="3a450-187"><xref:System.Windows.Controls.WebBrowser>控件应提供类似于主机浏览器的行为，包括安全限制。</span><span class="sxs-lookup"><span data-stu-id="3a450-187">The <xref:System.Windows.Controls.WebBrowser> control should provide behavior similar to the host browser, including security restrictions.</span></span> <span data-ttu-id="3a450-188">可以通过 Internet Explorer 安全设置控制这些安全限制中的某些限制。</span><span class="sxs-lookup"><span data-stu-id="3a450-188">Some of these security restrictions can be controlled through the Internet Explorer security settings.</span></span> <span data-ttu-id="3a450-189">有关详细信息，请参阅[安全性](../security-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="3a450-189">For more information, see [Security](../security-wpf.md).</span></span>

- <span data-ttu-id="3a450-190">在 HTML 页中跨域加载 XBAP 时，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="3a450-190">An exception is thrown when an XBAP is loaded cross-domain in an HTML page.</span></span>

- <span data-ttu-id="3a450-191">输入在独立于 WPF 的线程上 <xref:System.Windows.Controls.WebBrowser> ，因此无法截获键盘输入且不共享 IME 状态。</span><span class="sxs-lookup"><span data-stu-id="3a450-191">Input is on a separate thread from the WPF <xref:System.Windows.Controls.WebBrowser>, so keyboard input cannot be intercepted and the IME state is not shared.</span></span>

- <span data-ttu-id="3a450-192">由于 ActiveX 控件在另一个线程上运行，导航的计时或顺序可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="3a450-192">The timing or order of navigation may be different due to the ActiveX control running on another thread.</span></span> <span data-ttu-id="3a450-193">例如，并不总是通过启动另一个导航请求来取消到某页的导航。</span><span class="sxs-lookup"><span data-stu-id="3a450-193">For example, navigating to a page is not always cancelled by starting another navigation request.</span></span>

- <span data-ttu-id="3a450-194">自定义 ActiveX 控件可能会在通信方面出现问题，因为 WPF 应用程序在另一个线程上运行。</span><span class="sxs-lookup"><span data-stu-id="3a450-194">A custom ActiveX control may have trouble with communication since the WPF application is running in a separate thread.</span></span>

- <span data-ttu-id="3a450-195"><xref:System.Windows.Interop.HwndHost.MessageHook>不会引发，因为 <xref:System.Windows.Interop.HwndHost> 不能为在另一个线程或进程中运行的窗口划分子类。</span><span class="sxs-lookup"><span data-stu-id="3a450-195"><xref:System.Windows.Interop.HwndHost.MessageHook> does not get raised because <xref:System.Windows.Interop.HwndHost> cannot subclass a window running in another thread or process.</span></span>

### <a name="creating-a-full-trust-xbap"></a><span data-ttu-id="3a450-196">创建完全信任的 XBAP</span><span class="sxs-lookup"><span data-stu-id="3a450-196">Creating a Full-Trust XBAP</span></span>
 <span data-ttu-id="3a450-197">如果 XBAP 需要完全信任，则可以更改项目以启用此权限。</span><span class="sxs-lookup"><span data-stu-id="3a450-197">If your XBAP requires full trust, you can change your project to enable this permission.</span></span> <span data-ttu-id="3a450-198">以下步骤介绍如何启用完全信任：</span><span class="sxs-lookup"><span data-stu-id="3a450-198">The following steps describe how to enable full trust:</span></span>

1. <span data-ttu-id="3a450-199">在 Visual Studio 中，打开项目属性。</span><span class="sxs-lookup"><span data-stu-id="3a450-199">In Visual Studio, open the project properties.</span></span>

2. <span data-ttu-id="3a450-200">在“安全性”\*\*\*\* 选项卡上，选择“这是完全可信的应用程序”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="3a450-200">On the **Security** tab, select the **This is a full trust application** option.</span></span>

 <span data-ttu-id="3a450-201">此设置将进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="3a450-201">This setting makes the following changes:</span></span>

- <span data-ttu-id="3a450-202">在项目文件中，将 `<TargetZone>` 元素值更改为 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="3a450-202">In the project file, the `<TargetZone>` element value is changed to `Custom`.</span></span>

- <span data-ttu-id="3a450-203">在应用程序清单（app.config）中， `Unrestricted="true"` 属性添加到 "" <xref:System.Security.PermissionSet> 元素中。</span><span class="sxs-lookup"><span data-stu-id="3a450-203">In the application manifest (app.manifest), an `Unrestricted="true"` attribute is added to the \`<xref:System.Security.PermissionSet> element.</span></span>

    ```xml
    <PermissionSet class="System.Security.PermissionSet"
                   version="1"
                   ID="Custom"
                   SameSite="site"
                   Unrestricted="true" />
    ```

### <a name="deploying-a-full-trust-xbap"></a><span data-ttu-id="3a450-204">部署完全信任的 XBAP</span><span class="sxs-lookup"><span data-stu-id="3a450-204">Deploying a Full-Trust XBAP</span></span>
 <span data-ttu-id="3a450-205">部署不遵循 ClickOnce 受信任部署模型的完全信任的 XBAP 时，用户运行该应用程序时的行为将取决于安全区域。</span><span class="sxs-lookup"><span data-stu-id="3a450-205">When you deploy a full-trust XBAP that does not follow the ClickOnce Trusted Deployment model, the behavior when the user runs the application will depend on the security zone.</span></span> <span data-ttu-id="3a450-206">在某些情况下，用户会在尝试安装它时收到警告。</span><span class="sxs-lookup"><span data-stu-id="3a450-206">In some cases, the user will receive a warning when they attempt to install it.</span></span> <span data-ttu-id="3a450-207">用户可以选择继续或取消安装。</span><span class="sxs-lookup"><span data-stu-id="3a450-207">The user can choose to continue or cancel the installation.</span></span> <span data-ttu-id="3a450-208">下表描述每个安全区域的应用程序的行为，以及为了使应用程序接收完全信任而必须执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3a450-208">The following table describes the behavior of the application for each security zone and what you have to do for the application to receive full trust.</span></span>

|<span data-ttu-id="3a450-209">安全区域</span><span class="sxs-lookup"><span data-stu-id="3a450-209">Security Zone</span></span>|<span data-ttu-id="3a450-210">行为</span><span class="sxs-lookup"><span data-stu-id="3a450-210">Behavior</span></span>|<span data-ttu-id="3a450-211">获取完全信任</span><span class="sxs-lookup"><span data-stu-id="3a450-211">Getting Full Trust</span></span>|
|-------------------|--------------|------------------------|
|<span data-ttu-id="3a450-212">本地计算机</span><span class="sxs-lookup"><span data-stu-id="3a450-212">Local computer</span></span>|<span data-ttu-id="3a450-213">自动完全信任</span><span class="sxs-lookup"><span data-stu-id="3a450-213">Automatic full trust</span></span>|<span data-ttu-id="3a450-214">无需采取任何措施。</span><span class="sxs-lookup"><span data-stu-id="3a450-214">No action is needed.</span></span>|
|<span data-ttu-id="3a450-215">Intranet 和受信任的站点</span><span class="sxs-lookup"><span data-stu-id="3a450-215">Intranet and trusted sites</span></span>|<span data-ttu-id="3a450-216">提示完全信任</span><span class="sxs-lookup"><span data-stu-id="3a450-216">Prompt for full trust</span></span>|<span data-ttu-id="3a450-217">使用证书对 XBAP 进行签名，以便用户在提示中看到源。</span><span class="sxs-lookup"><span data-stu-id="3a450-217">Sign the XBAP with a certificate so that the user sees the source in the prompt.</span></span>|
|<span data-ttu-id="3a450-218">Internet</span><span class="sxs-lookup"><span data-stu-id="3a450-218">Internet</span></span>|<span data-ttu-id="3a450-219">失败，并显示“未授予信任”</span><span class="sxs-lookup"><span data-stu-id="3a450-219">Fails with "Trust Not Granted"</span></span>|<span data-ttu-id="3a450-220">使用证书对 XBAP 进行签名。</span><span class="sxs-lookup"><span data-stu-id="3a450-220">Sign the XBAP with a certificate.</span></span>|

> [!NOTE]
> <span data-ttu-id="3a450-221">上表中描述的行为针对的是不遵循 ClickOnce 受信任部署模型的完全信任的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-221">The behavior described in the previous table is for full-trust XBAPs that do not follow the ClickOnce Trusted Deployment model.</span></span>

 <span data-ttu-id="3a450-222">建议使用 ClickOnce 受信任部署模型部署完全信任的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="3a450-222">It is recommended that you use the ClickOnce Trusted Deployment model for deploying a full-trust XBAP.</span></span> <span data-ttu-id="3a450-223">此模型允许自动向 XBAP 授予完全信任（与安全区域无关），这样用户便不会收到提示。</span><span class="sxs-lookup"><span data-stu-id="3a450-223">This model allows your XBAP to be granted full trust automatically, regardless of the security zone, so that the user is not prompted.</span></span> <span data-ttu-id="3a450-224">作为此模型的一部分，必须使用来自受信任发行者提供的证书来对应用程序进行签名。</span><span class="sxs-lookup"><span data-stu-id="3a450-224">As part of this model, you must sign your application with a certificate from a trusted publisher.</span></span> <span data-ttu-id="3a450-225">有关详细信息，请参阅[受信任的应用程序部署概述](/visualstudio/deployment/trusted-application-deployment-overview)和 [Introduction to Code Signing](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))（代码签名简介）。</span><span class="sxs-lookup"><span data-stu-id="3a450-225">For more information, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) and [Introduction to Code Signing](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85)).</span></span>

<a name="xbap_start_time_performance_considerations"></a>
## <a name="xbap-start-time-performance-considerations"></a><span data-ttu-id="3a450-226">XBAP 启动时间性能注意事项</span><span class="sxs-lookup"><span data-stu-id="3a450-226">XBAP Start Time Performance Considerations</span></span>
 <span data-ttu-id="3a450-227">XBAP 性能的一个重要方面是其启动时间。</span><span class="sxs-lookup"><span data-stu-id="3a450-227">An important aspect of XBAP performance is its start time.</span></span> <span data-ttu-id="3a450-228">如果 XBAP 是要加载的第一个 WPF 应用程序，则冷启动\*\* 时间可能为十秒或更长。</span><span class="sxs-lookup"><span data-stu-id="3a450-228">If an XBAP is the first WPF application to load, the *cold start* time can be ten seconds or more.</span></span> <span data-ttu-id="3a450-229">这是因为进度页面由 WPF 呈现，且 CLR 和 WPF 都必须冷启动才能显示应用程序。</span><span class="sxs-lookup"><span data-stu-id="3a450-229">This is because the progress page is rendered by WPF, and both the CLR and WPF must be cold-started to display the application.</span></span>

 <span data-ttu-id="3a450-230">从 .NET Framework 3.5 SP1 开始，将在部署周期的初期显示非托管进度页面，从而减轻 XBAP 冷启动时间。</span><span class="sxs-lookup"><span data-stu-id="3a450-230">Starting in .NET Framework 3.5 SP1, XBAP cold-start time is mitigated by displaying an unmanaged progress page early in the deployment cycle.</span></span> <span data-ttu-id="3a450-231">启动应用程序后几乎会立即显示进度页，因为它由本机宿主代码显示，并以 HTML 格式呈现。</span><span class="sxs-lookup"><span data-stu-id="3a450-231">The progress page appears almost immediately after the application is started, because it is displayed by native hosting code and rendered in HTML.</span></span>

 <span data-ttu-id="3a450-232">此外，改进后的 ClickOnce 下载顺序并发性将开始时间提高了10%。</span><span class="sxs-lookup"><span data-stu-id="3a450-232">In addition, improved concurrency of the ClickOnce download sequence improves start time by up to ten percent.</span></span> <span data-ttu-id="3a450-233">ClickOnce 下载并验证清单后，将启动应用程序下载，并开始更新进度栏。</span><span class="sxs-lookup"><span data-stu-id="3a450-233">After ClickOnce downloads and validates manifests, the application download starts, and the progress bar starts to update.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a450-234">请参阅</span><span class="sxs-lookup"><span data-stu-id="3a450-234">See also</span></span>

- [<span data-ttu-id="3a450-235">配置 Visual Studio 以调试 XAML 浏览器应用程序来调用 Web 服务</span><span class="sxs-lookup"><span data-stu-id="3a450-235">Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [<span data-ttu-id="3a450-236">部署 WPF 应用程序</span><span class="sxs-lookup"><span data-stu-id="3a450-236">Deploying a WPF Application</span></span>](deploying-a-wpf-application-wpf.md)
