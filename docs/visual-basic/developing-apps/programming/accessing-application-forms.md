---
title: 访问应用程序窗体
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 44f98632fd2fd6c4c087a78b805d5b7da750df87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410200"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="0140d-102">访问应用程序窗体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0140d-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="0140d-103">`My.Forms` 对象提供一种简单方法，用于访问在应用程序项目中声明的每个 Windows 窗体的实例。</span><span class="sxs-lookup"><span data-stu-id="0140d-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="0140d-104">还可以使用 `My.Application` 对象的属性来访问应用程序的初始屏幕和主窗体，并获取应用程序的打开的窗体的列表。</span><span class="sxs-lookup"><span data-stu-id="0140d-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="0140d-105">任务</span><span class="sxs-lookup"><span data-stu-id="0140d-105">Tasks</span></span>  

 <span data-ttu-id="0140d-106">下表列出了演示如何访问应用程序窗体的示例。</span><span class="sxs-lookup"><span data-stu-id="0140d-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="0140d-107">到</span><span class="sxs-lookup"><span data-stu-id="0140d-107">To</span></span>|<span data-ttu-id="0140d-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="0140d-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="0140d-109">在应用程序中从某一窗体访问另一窗体。</span><span class="sxs-lookup"><span data-stu-id="0140d-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="0140d-110">My.Forms 对象</span><span class="sxs-lookup"><span data-stu-id="0140d-110">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="0140d-111">显示应用程序所有打开的窗体的标题。</span><span class="sxs-lookup"><span data-stu-id="0140d-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="0140d-112">在应用程序启动时，使用状态信息更新初始屏幕。</span><span class="sxs-lookup"><span data-stu-id="0140d-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="0140d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0140d-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="0140d-114">My.Forms 对象</span><span class="sxs-lookup"><span data-stu-id="0140d-114">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
