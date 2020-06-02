---
title: 使用可移植类库的跨平台开发
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 033c9bc6e506d0ae2b9f20fedb72d1b7f29e434b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288909"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="e79ba-102">具有可移植类库的跨平台开发</span><span class="sxs-lookup"><span data-stu-id="e79ba-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="e79ba-103">Visual Studio 中的可移植类库项目类型可帮助你快速轻松地为 Microsoft 平台构建跨平台应用程序和库。</span><span class="sxs-lookup"><span data-stu-id="e79ba-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="e79ba-104">可移植类库可以帮助你减少开发和测试代码的时间和成本。</span><span class="sxs-lookup"><span data-stu-id="e79ba-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="e79ba-105">使用此项目类型来编写和生成可移植的 .NET Framework 程序集，然后从面向多个平台（如 .NET Framework、iOS 或 Mac）的应用程序中引用这些程序集。</span><span class="sxs-lookup"><span data-stu-id="e79ba-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="e79ba-106">即使是在 Visual Studio 中创建可移植类库项目并开始开发它之后，你仍然可以更改目标平台。</span><span class="sxs-lookup"><span data-stu-id="e79ba-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="e79ba-107">Visual Studio 会将你的库与新的程序集一起编译，这有助于识别你需要在代码中进行的更改。</span><span class="sxs-lookup"><span data-stu-id="e79ba-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="e79ba-108">创建可移植类库项目</span><span class="sxs-lookup"><span data-stu-id="e79ba-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="e79ba-109">若要创建可移植类库，请使用 Visual Studio 中提供的模板。</span><span class="sxs-lookup"><span data-stu-id="e79ba-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="e79ba-110">创建新项目（"**文件**"  >  "**新建项目**"），然后在 "**新建项目**" 对话框中，选择编程语言（Visual c # 或 Visual Basic）。</span><span class="sxs-lookup"><span data-stu-id="e79ba-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="e79ba-111">然后，选择 "类库 **（旧版可移植）** " 模板。</span><span class="sxs-lookup"><span data-stu-id="e79ba-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="e79ba-112">输入项目的名称，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e79ba-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="e79ba-113">此时将显示 "**添加可移植类库**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="e79ba-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="e79ba-114">选择两个或多个目标，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e79ba-114">Choose two or more targets, and then choose **OK**.</span></span>

![在 Visual Studio 中添加可移植类库目标](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="e79ba-116">更改目标</span><span class="sxs-lookup"><span data-stu-id="e79ba-116">Change targets</span></span>

<span data-ttu-id="e79ba-117">您可以在创建可移植类库项目时或在开始开发后更改该项目的目标平台。</span><span class="sxs-lookup"><span data-stu-id="e79ba-117">You can change the target platforms of a portable class library project when you create it or after you've started development.</span></span> <span data-ttu-id="e79ba-118">如果要在创建项目后更改目标，请在**解决方案资源管理器**中打开可移植类库项目（而非解决方案）的快捷菜单，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="e79ba-118">If you want to change the targets after you've created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="e79ba-119">在 "项目属性" 页上，"**库**" 选项卡显示项目当前针对的平台。</span><span class="sxs-lookup"><span data-stu-id="e79ba-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Visual Studio 中可移植类库的项目属性](media/pcl-project-properties.png)

<span data-ttu-id="e79ba-121">若要添加或删除目标，请选择 "**更改**" 按钮，然后选中并清除相应的复选框。</span><span class="sxs-lookup"><span data-stu-id="e79ba-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="e79ba-122">在你更改目标时，供你在开发项目时使用的 API 也将发生更改以匹配你的选择。</span><span class="sxs-lookup"><span data-stu-id="e79ba-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="e79ba-123">Visual Studio 报告因目标更改而可能导致的错误和警告。</span><span class="sxs-lookup"><span data-stu-id="e79ba-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="e79ba-124">如果要在 Visual Studio 中进行更改之前评估程序集的可移植性，可以使用[.net 可移植性分析器](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="e79ba-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="e79ba-125">支持的类型和成员</span><span class="sxs-lookup"><span data-stu-id="e79ba-125">Supported types and members</span></span>

<span data-ttu-id="e79ba-126">可移植类库项目中可用的类型和成员受若干兼容性因素的约束：</span><span class="sxs-lookup"><span data-stu-id="e79ba-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="e79ba-127">它们必须在所选各目标之间共享。</span><span class="sxs-lookup"><span data-stu-id="e79ba-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="e79ba-128">它们必须在这些目标上具有类似的行为方式。</span><span class="sxs-lookup"><span data-stu-id="e79ba-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="e79ba-129">它们不能是要弃用的候选项。</span><span class="sxs-lookup"><span data-stu-id="e79ba-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="e79ba-130">它们必须在可移植环境中有意义，特别是在支持成员不可移植时。</span><span class="sxs-lookup"><span data-stu-id="e79ba-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="e79ba-131">如果一个成员在可移植类库和所选的目标中受支持，它将会你的 IntelliSense 项目中出现。</span><span class="sxs-lookup"><span data-stu-id="e79ba-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="e79ba-132">但是，请记住某一 API 可能在可移植类库中受支持，但你是否可以使用该 API ​​取决于你选择的目标。</span><span class="sxs-lookup"><span data-stu-id="e79ba-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="e79ba-133">可移植类库中的 API 差异</span><span class="sxs-lookup"><span data-stu-id="e79ba-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="e79ba-134">为了使可移植类库程序集在所有支持的平台中都兼容，可移植类库中对部分成员进行了轻微更改。</span><span class="sxs-lookup"><span data-stu-id="e79ba-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="e79ba-135">使用可移植类库</span><span class="sxs-lookup"><span data-stu-id="e79ba-135">Use the Portable Class Library</span></span>

<span data-ttu-id="e79ba-136">构建可移植类库项目后，只需从其他项目中引用它即可。</span><span class="sxs-lookup"><span data-stu-id="e79ba-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="e79ba-137">可以引用该项目或包含你要访问的类的特定程序集。</span><span class="sxs-lookup"><span data-stu-id="e79ba-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="e79ba-138">若要运行引用可移植类库程序集的应用，必须在计算机上安装所需版本（或更高版本）的目标平台。</span><span class="sxs-lookup"><span data-stu-id="e79ba-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="e79ba-139">Visual Studio 包含所有必需的框架，因此你无需进一步修改即可在用来开发应用的计算机上运行该应用。</span><span class="sxs-lookup"><span data-stu-id="e79ba-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="e79ba-140">部署通用 Windows 应用</span><span class="sxs-lookup"><span data-stu-id="e79ba-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="e79ba-141">当你创建一个引用可移植类库程序集的通用 Windows 应用程序时，应用包中将包含你部署该应用所需的所有内容，并且无需执行其他步骤。</span><span class="sxs-lookup"><span data-stu-id="e79ba-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="e79ba-142">部署 .NET Framework 应用</span><span class="sxs-lookup"><span data-stu-id="e79ba-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="e79ba-143">部署引用可移植类库程序集的 .NET Framework 应用时，你必须指定一个对 .NET Framework 正确版本的依赖项。</span><span class="sxs-lookup"><span data-stu-id="e79ba-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="e79ba-144">通过指定此依赖项，可确保与你的应用程序一起安装所需的版本。</span><span class="sxs-lookup"><span data-stu-id="e79ba-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="e79ba-145">使用 ClickOnce 部署创建依赖项：在**解决方案资源管理器**中，选择要发布的项目的项目节点。</span><span class="sxs-lookup"><span data-stu-id="e79ba-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="e79ba-146">（这是引用可移植类库项目的项目。）在菜单栏上，选择 "**项目**  >  **属性**"，然后选择 "**发布**" 选项卡。在 "**发布**" 页上，选择 "**系统必备**"。</span><span class="sxs-lookup"><span data-stu-id="e79ba-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="e79ba-147">选择所需 .NET Framework 版本作为系统必备组件。</span><span class="sxs-lookup"><span data-stu-id="e79ba-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="e79ba-148">若要创建与安装项目的依赖项：在**解决方案资源管理器**中，选择 "安装" 项目。</span><span class="sxs-lookup"><span data-stu-id="e79ba-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="e79ba-149">在菜单栏上，选择 "**项目**  >  **属性**" "  >  **必备组件**"。</span><span class="sxs-lookup"><span data-stu-id="e79ba-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="e79ba-150">选择所需 .NET Framework 版本作为系统必备组件。</span><span class="sxs-lookup"><span data-stu-id="e79ba-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="e79ba-151">有关部署 .NET Framework 应用的详细信息，请参阅面向[开发人员的部署指南](../../framework/deployment/deployment-guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="e79ba-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e79ba-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e79ba-152">See also</span></span>

- [<span data-ttu-id="e79ba-153">将可移植类库与 MVVM 配合使用</span><span class="sxs-lookup"><span data-stu-id="e79ba-153">Using Portable Class Library with MVVM</span></span>](using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="e79ba-154">面向多个平台的库的应用资源</span><span class="sxs-lookup"><span data-stu-id="e79ba-154">App Resources for Libraries That Target Multiple Platforms</span></span>](app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="e79ba-155">.NET 可移植性分析器</span><span class="sxs-lookup"><span data-stu-id="e79ba-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="e79ba-156">.NET Framework 对 Windows 应用商店应用程序和 Windows 运行时的支持情况</span><span class="sxs-lookup"><span data-stu-id="e79ba-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="e79ba-157">部署</span><span class="sxs-lookup"><span data-stu-id="e79ba-157">Deployment</span></span>](../../framework/deployment/net-framework-applications.md)
