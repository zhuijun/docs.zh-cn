---
title: '.NET Framework 4.8、4.7、4.6 和 4.5 的迁移指南 '
description: 关于如何迁移到更高版本 .NET Framework 的指南，其中包括新功能和应用程序兼容性的资源。
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: a5b632824efacdb5e99228727b8751dc7f17d363
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86443411"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a><span data-ttu-id="fa6a6-103">迁移到 .NET Framework 4.8、4.7、4.6 和 4.5</span><span class="sxs-lookup"><span data-stu-id="fa6a6-103">Migrate to .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="fa6a6-104">如果你使用更早版本的 .NET Framework 创建了应用，则通常可将它轻松升级到 .NET Framework 4.5 及其小数点版本（4.5.1 和 4.5.2）、.NET Framework 4.6 及其小数点版本（4.6.1 和 4.6.2）、.NET Framework 4.7 及其小数点版本（4.7.1 和 4.7.2）或者 .NET Framework 4.8。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-104">If you created your app using an earlier version of .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="fa6a6-105">在 Visual Studio 中打开项目。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-105">Open your project in Visual Studio.</span></span> <span data-ttu-id="fa6a6-106">如果项目是在之前版本的 Visual Studio 中创建的，则会自动打开“项目兼容性”对话框。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-106">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="fa6a6-107">有关在 Visual Studio 中升级项目的详细信息，请参阅[移植、迁移和升级 Visual Studio 项目](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2019 平台目标以及兼容性](/visualstudio/releases/2019/compatibility)。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-107">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="fa6a6-108">但是，.NET Framework 中的某些更改要求你你代码进行更改。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-108">However, some changes in .NET Framework require changes to your code.</span></span> <span data-ttu-id="fa6a6-109">也可利用 .NET Framework 4.5 及其子版本、.NET Framework 4.6 及其子版本、.NET Framework 4.7 及其子版本或 .NET Framework 4.8 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-109">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="fa6a6-110">针对新版本的 .NET Framework 对应用进行这些类型的更改通常被称为“迁移”。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-110">Making these types of changes to your app for a new version of .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="fa6a6-111">如果无需迁移应用，则不用重新编译它就可在 .NET Framework 4.5 或更高版本中运行它。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-111">If your app doesn't have to be migrated, you can run it in .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="fa6a6-112">迁移资源</span><span class="sxs-lookup"><span data-stu-id="fa6a6-112">Migration resources</span></span>

<span data-ttu-id="fa6a6-113">请在将应用从更旧版本的 .NET Framework 迁移到 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8 之前，阅读以下文档：</span><span class="sxs-lookup"><span data-stu-id="fa6a6-113">Review the following documents before you migrate your app from earlier versions of .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="fa6a6-114">请参阅[版本和依赖关系](versions-and-dependencies.md)以了解作为每个 .NET Framework 版本基础的 CLR 版本，并查看成功设定应用目标的指南。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-114">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="fa6a6-115">查看[应用程序兼容性](application-compatibility.md)以了解可能影响应用的运行时和重定目标更改以及如何处理这些更改。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-115">Review [Application compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="fa6a6-116">查看[类库中过时的内容](../whats-new/whats-obsolete.md)以确定代码中已过时的任何类型或成员以及建议的备选项。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-116">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="fa6a6-117">查看[新增功能](../whats-new/index.md)以了解可能需要向应用添加的新功能的说明。</span><span class="sxs-lookup"><span data-stu-id="fa6a6-117">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa6a6-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="fa6a6-118">See also</span></span>

- [<span data-ttu-id="fa6a6-119">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="fa6a6-119">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="fa6a6-120">从 .NET Framework 1.1 迁移</span><span class="sxs-lookup"><span data-stu-id="fa6a6-120">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="fa6a6-121">版本兼容性</span><span class="sxs-lookup"><span data-stu-id="fa6a6-121">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="fa6a6-122">版本和依赖关系</span><span class="sxs-lookup"><span data-stu-id="fa6a6-122">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="fa6a6-123">如何：将应用配置为支持 .NET Framework 4 或更高版本</span><span class="sxs-lookup"><span data-stu-id="fa6a6-123">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="fa6a6-124">新增功能</span><span class="sxs-lookup"><span data-stu-id="fa6a6-124">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="fa6a6-125">类库中过时的内容</span><span class="sxs-lookup"><span data-stu-id="fa6a6-125">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="fa6a6-126">.NET Framework 官方支持策略</span><span class="sxs-lookup"><span data-stu-id="fa6a6-126">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="fa6a6-127">.NET Framework 4 迁移问题</span><span class="sxs-lookup"><span data-stu-id="fa6a6-127">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)
