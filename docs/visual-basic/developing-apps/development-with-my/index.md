---
title: 使用 My 开发
ms.date: 07/20/2015
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
ms.openlocfilehash: 3befac591de8fbc7250777a8b87247ee395abf25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "85840284"
---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="e3c74-102">使用 My 开发 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3c74-102">Development with My (Visual Basic)</span></span>

<span data-ttu-id="e3c74-103">Visual Basic 提供了支持快速应用程序开发的新功能，不仅功能强大，还有助于提高工作效率和易用性。</span><span class="sxs-lookup"><span data-stu-id="e3c74-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="e3c74-104">其中一项功能称为 `My`，可提供对与应用程序及其运行时环境相关的信息和默认对象实例的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e3c74-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="e3c74-105">此类信息按可通过 IntelliSense 搜索的格式进行编排，并根据用途进行了逻辑界定。</span><span class="sxs-lookup"><span data-stu-id="e3c74-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="e3c74-106">`My` 的顶级成员作为对象公开。</span><span class="sxs-lookup"><span data-stu-id="e3c74-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="e3c74-107">每个对象的行为类似于包含 `Shared` 成员的命名空间或类，可公开一组相关成员。</span><span class="sxs-lookup"><span data-stu-id="e3c74-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="e3c74-108">下表展示了顶级 `My` 对象及其相互之间的关系。</span><span class="sxs-lookup"><span data-stu-id="e3c74-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 ![显示 My 的对象模型的示意图。](./media/index/my-object-model-relationships.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="e3c74-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="e3c74-110">In This Section</span></span>  

 [<span data-ttu-id="e3c74-111">使用 My.Application、My.Computer 和 My.User 执行任务</span><span class="sxs-lookup"><span data-stu-id="e3c74-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="e3c74-112">介绍了三个主要 `My` 对象（`My.Application`、`My.Computer` 和 `My.User`），这些对象提供对信息和功能的访问权限</span><span class="sxs-lookup"><span data-stu-id="e3c74-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="e3c74-113">My.Forms 和 My.WebServices 提供的默认对象实例</span><span class="sxs-lookup"><span data-stu-id="e3c74-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="e3c74-114">介绍了 `My.Forms` 和 `My.WebServices` 对象，这些对象提供对应用程序使用的窗体、数据源和 XML Web Service 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e3c74-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="e3c74-115">使用 My.Resources 和 My.Settings 快速开发应用程序</span><span class="sxs-lookup"><span data-stu-id="e3c74-115">Rapid Application Development with My.Resources and My.Settings</span></span>](rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="e3c74-116">介绍了 `My.Resources` 和 `My.Settings` 对象，这些对象提供对应用程序资源和设置的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e3c74-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="e3c74-117">Visual Basic 应用程序模型概述</span><span class="sxs-lookup"><span data-stu-id="e3c74-117">Overview of the Visual Basic Application Model</span></span>](overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="e3c74-118">介绍 Visual Basic 应用程序启动/关闭模型。</span><span class="sxs-lookup"><span data-stu-id="e3c74-118">Describes the Visual Basic Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="e3c74-119">My 对项目类型的依赖方式</span><span class="sxs-lookup"><span data-stu-id="e3c74-119">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)  
 <span data-ttu-id="e3c74-120">详细介绍了不同项目类型中可用的 `My` 功能。</span><span class="sxs-lookup"><span data-stu-id="e3c74-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c74-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="e3c74-121">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="e3c74-122">My.Forms 对象</span><span class="sxs-lookup"><span data-stu-id="e3c74-122">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="e3c74-123">My.WebServices 对象</span><span class="sxs-lookup"><span data-stu-id="e3c74-123">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="e3c74-124">My 对项目类型的依赖方式</span><span class="sxs-lookup"><span data-stu-id="e3c74-124">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
