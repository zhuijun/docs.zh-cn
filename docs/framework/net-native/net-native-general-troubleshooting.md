---
title: .NET Native 一般疑难解答
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
ms.openlocfilehash: 2bea81e380fed6c456898e9883658ef874c8dd97
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128230"
---
# <a name="net-native-general-troubleshooting"></a><span data-ttu-id="1d62d-102">.NET Native 一般疑难解答</span><span class="sxs-lookup"><span data-stu-id="1d62d-102">.NET Native General Troubleshooting</span></span>

<span data-ttu-id="1d62d-103">本主题介绍如何解决在 .NET Native 开发应用程序时可能遇到的潜在问题。</span><span class="sxs-lookup"><span data-stu-id="1d62d-103">This topic describes how to troubleshoot potential issues that you might encounter when developing apps with .NET Native.</span></span>

- <span data-ttu-id="1d62d-104">问题：生成输出窗口未正确更新\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d62d-104">**Issue:** Your build output window isn't properly updated.</span></span>

  <span data-ttu-id="1d62d-105">解决方法：该生成输出窗口在生成完成之前不会更新\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d62d-105">**Resolution:** The build output window isn't updated until the build completes.</span></span> <span data-ttu-id="1d62d-106">生成时间可能会长达数分钟，因此在可能看到更新之前可能会有一个延误。</span><span class="sxs-lookup"><span data-stu-id="1d62d-106">Build times may be up to several minutes, so you might experience a delay in seeing the updates.</span></span>

- <span data-ttu-id="1d62d-107">问题：应用的 ARM 零售生成时间已经后推\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d62d-107">**Issue:** Your app’s retail build time for ARM has increased.</span></span>

  <span data-ttu-id="1d62d-108">**解决方法：** 将应用部署到 ARM 设备时，将调用 .NET Native 基础结构。</span><span class="sxs-lookup"><span data-stu-id="1d62d-108">**Resolution:** When you deploy an app to your ARM device, the .NET Native infrastructure is invoked.</span></span> <span data-ttu-id="1d62d-109">该编译执行了大量的优化，同时还确保反射等非静态语义继续工作。</span><span class="sxs-lookup"><span data-stu-id="1d62d-109">This compilation performs a large number of optimizations while ensuring that non-static semantics such as reflection continue to work.</span></span> <span data-ttu-id="1d62d-110">此外，.NET 框架中应用使用的那部分得到动态链接，以达到最佳性能，并且还必须编译到本机代码之中。</span><span class="sxs-lookup"><span data-stu-id="1d62d-110">In addition, the portion of the .NET Framework that the app uses is statically linked in for optimal performance and has to be compiled into native code as well.</span></span> <span data-ttu-id="1d62d-111">这就是编译花费时间较长的原因。</span><span class="sxs-lookup"><span data-stu-id="1d62d-111">This is why compilation takes longer.</span></span>

  <span data-ttu-id="1d62d-112">然而，对于标准开发机器上的大多数应用而言，标准编译的编译时间仍在一分钟以内。</span><span class="sxs-lookup"><span data-stu-id="1d62d-112">However, compilation times are still within a minute of standard compilation for most apps on a standard development machine.</span></span>  <span data-ttu-id="1d62d-113">通常，在标准开发机器上仅为 .NET Framework 生成本机映像就要花上数分钟。</span><span class="sxs-lookup"><span data-stu-id="1d62d-113">Typically, just generating native images for the .NET Framework on a standard development machine takes several minutes.</span></span>  <span data-ttu-id="1d62d-114">即使所有的优化可改善生成的代码并且包含 .NET 框架，应用版本时间通常要花费一两分钟。</span><span class="sxs-lookup"><span data-stu-id="1d62d-114">Even with all the optimizations to improve the generated code and with including the .NET Framework, app build times are typically a minute or two.</span></span>

  <span data-ttu-id="1d62d-115">我们将继续工作，通过调查多线程编译和其他优化方法来提升编译性能。</span><span class="sxs-lookup"><span data-stu-id="1d62d-115">We are continuing to work on improving compilation performance by investigating multi-threaded compilation and other optimizations.</span></span>

- <span data-ttu-id="1d62d-116">**问题：** 您不知道您的应用程序是使用 .NET Native 编译的。</span><span class="sxs-lookup"><span data-stu-id="1d62d-116">**Issue:** You don’t know if your app was compiled using .NET Native.</span></span>

  <span data-ttu-id="1d62d-117">**解决方法：** 如果调用 .NET Native 编译器，你会注意到生成时间较长，并且任务管理器将显示各种 .NET Native 组件进程，如 ILC 和 nutc_driver。</span><span class="sxs-lookup"><span data-stu-id="1d62d-117">**Resolution:** If the .NET Native compiler is invoked, you'll notice longer build times, and Task Manager will show various .NET Native component processes such as ILC.exe and nutc_driver.exe.</span></span>

  <span data-ttu-id="1d62d-118">成功生成具有 .NET Native 的项目后，可以在 "obj \\ *config* \  *arch* \\ *projectname*ilc\out 目录" 最终的本机包内容可在 bin " \\ *arch* \\ *配置*\AppX." 下找到。</span><span class="sxs-lookup"><span data-stu-id="1d62d-118">After you successfully build your project with .NET Native, you'll find the output under obj\\*config*\ *arch*\\*projectname*.ilc\out.  The final native package contents can be found under bin\\*arch*\\*config*\AppX.</span></span> <span data-ttu-id="1d62d-119">如果已部署应用，则最终的本机包内容低于 \bin 的 \\ *arch* \\ *配置*\AppX。</span><span class="sxs-lookup"><span data-stu-id="1d62d-119">The final native package contents are under \bin\\*arch*\\*config*\AppX if you have deployed the app.</span></span>

- <span data-ttu-id="1d62d-120">问题：.NET Native 编译的应用正在引发运行时异常（通常为 [MissingMetadataException](missingmetadataexception-class-net-native.md) 或 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 异常），而应用未使用 .NET Native 进行编译时则不会引发该异常\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d62d-120">**Issue:** Your .NET Native-compiled app is throwing runtime exceptions (typically [MissingMetadataException](missingmetadataexception-class-net-native.md) or [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions) that it did not throw when compiled without .NET Native.</span></span>

  <span data-ttu-id="1d62d-121">解决方法：引发异常的原因是 .NET Native 未提供元数据或通过反射可用的实现代码\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d62d-121">**Resolution:** The exceptions are thrown because .NET Native did not provide either the metadata or the implementation code that is otherwise available through reflection.</span></span> <span data-ttu-id="1d62d-122">（有关详细信息，请参阅[.NET Native 和编译](net-native-and-compilation.md)。）若要消除此异常，必须将条目添加到[运行时指令（研发）文件](runtime-directives-rd-xml-configuration-file-reference.md)，以便 .NET Native 工具链可以使元数据或实现代码在运行时可用。</span><span class="sxs-lookup"><span data-stu-id="1d62d-122">(For more information, see [.NET Native and Compilation](net-native-and-compilation.md).) To eliminate the exception, you have to add an entry to your [runtime directives (rd.xml) file](runtime-directives-rd-xml-configuration-file-reference.md) so that the .NET Native tool chain can make the metadata or implementation code available at runtime.</span></span> <span data-ttu-id="1d62d-123">有两个可用的故障排除程序，将生成要添加到运行时指令文件的必需条目：</span><span class="sxs-lookup"><span data-stu-id="1d62d-123">Two troubleshooters are available that will generate the necessary entry to add to your runtime directives file:</span></span>

  - <span data-ttu-id="1d62d-124">类型的 [MissingMetadataException 故障排除程序](https://dotnet.github.io/native/troubleshooter/type.html) 。</span><span class="sxs-lookup"><span data-stu-id="1d62d-124">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>

  - <span data-ttu-id="1d62d-125">方法的 [MissingMetadataException 故障排除程序](https://dotnet.github.io/native/troubleshooter/method.html) 。</span><span class="sxs-lookup"><span data-stu-id="1d62d-125">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>

  <span data-ttu-id="1d62d-126">有关详细信息，请参阅[反射和 .NET Native](reflection-and-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="1d62d-126">For more information, see [Reflection and .NET Native](reflection-and-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d62d-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d62d-127">See also</span></span>

- [<span data-ttu-id="1d62d-128">将 Windows 应用商店应用迁移到 .NET Native</span><span class="sxs-lookup"><span data-stu-id="1d62d-128">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)
