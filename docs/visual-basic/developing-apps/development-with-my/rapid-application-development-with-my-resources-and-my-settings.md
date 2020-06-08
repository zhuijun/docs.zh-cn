---
title: 使用 My.Resources 和 My.Settings 快速开发应用程序
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 6c53d11a3830a5a8a2cb898728bed8694a226686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411663"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="56032-102">使用 My.Resources 和 My.Settings 快速开发应用程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56032-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="56032-103">`My.Resources` 对象提供对应用程序资源的访问权限，并允许你动态检索应用程序的资源。</span><span class="sxs-lookup"><span data-stu-id="56032-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="56032-104">检索资源</span><span class="sxs-lookup"><span data-stu-id="56032-104">Retrieving Resources</span></span>  

 <span data-ttu-id="56032-105">某些资源（如音频文件、图标、图像和字符串）可通过 `My.Resources` 对象进行检索。</span><span class="sxs-lookup"><span data-stu-id="56032-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="56032-106">例如，你可以访问应用程序特定于区域性的资源文件。</span><span class="sxs-lookup"><span data-stu-id="56032-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="56032-107">下面的示例将窗体图标设置为存储在应用程序的资源文件中的名为 `Form1Icon` 的图标。</span><span class="sxs-lookup"><span data-stu-id="56032-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="56032-108">`My.Resources` 对象只公开全局资源。</span><span class="sxs-lookup"><span data-stu-id="56032-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="56032-109">它不提供对与窗体关联的资源文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="56032-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="56032-110">必须从窗体访问窗体资源。</span><span class="sxs-lookup"><span data-stu-id="56032-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="56032-111">同样，`My.Settings` 对象提供对应用程序设置的访问，并允许你动态地存储和检索应用程序的属性设置和其他信息。</span><span class="sxs-lookup"><span data-stu-id="56032-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="56032-112">有关详细信息，请参阅 [My.Resources 对象](../../language-reference/objects/my-resources-object.md)和 [My.Settings 对象](../../language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="56032-112">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56032-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="56032-113">See also</span></span>

- [<span data-ttu-id="56032-114">My.Resources 对象</span><span class="sxs-lookup"><span data-stu-id="56032-114">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="56032-115">My.Settings 对象</span><span class="sxs-lookup"><span data-stu-id="56032-115">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="56032-116">访问应用程序设置</span><span class="sxs-lookup"><span data-stu-id="56032-116">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
