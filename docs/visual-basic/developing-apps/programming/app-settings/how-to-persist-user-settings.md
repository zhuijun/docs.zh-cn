---
title: 如何：永久保存用户设置
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 817111060259bdfbbb26d9f8eafeae439e1f651f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410148"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="ee140-102">如何：在 Visual Basic 中保存用户设置</span><span class="sxs-lookup"><span data-stu-id="ee140-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="ee140-103">可以使用 `My.Settings.Save` 方法来保存对用户设置的更改。</span><span class="sxs-lookup"><span data-stu-id="ee140-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="ee140-104">通常情况下，将应用程序设计为在应用程序关闭时保存用户设置的更改。</span><span class="sxs-lookup"><span data-stu-id="ee140-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="ee140-105">这是因为保存设置需要几秒钟，具体取决于多种因素。</span><span class="sxs-lookup"><span data-stu-id="ee140-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="ee140-106">有关详细信息，请参阅 [My.Settings 对象](../../../language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="ee140-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee140-107">虽然可以在运行时更改并保存用户范围设置的值，但是应用程序范围设置是只读的，不能以编程方式进行更改。</span><span class="sxs-lookup"><span data-stu-id="ee140-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="ee140-108">可以在创建应用程序时通过**项目设计器**，或者编辑应用程序的配置文件来更改应用程序范围设置。</span><span class="sxs-lookup"><span data-stu-id="ee140-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="ee140-109">有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="ee140-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee140-110">示例</span><span class="sxs-lookup"><span data-stu-id="ee140-110">Example</span></span>  

 <span data-ttu-id="ee140-111">本示例更改 `LastChanged` 用户设置的值，并通过调用 `My.Settings.Save` 方法来保存此更改。</span><span class="sxs-lookup"><span data-stu-id="ee140-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="ee140-112">若要使用本示例，应用程序必须具有类型为 `Date` 的 `LastChanged` 用户设置。</span><span class="sxs-lookup"><span data-stu-id="ee140-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="ee140-113">有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="ee140-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee140-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="ee140-114">See also</span></span>

- [<span data-ttu-id="ee140-115">My.Settings 对象</span><span class="sxs-lookup"><span data-stu-id="ee140-115">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="ee140-116">如何：在 Visual Basic 中读取应用程序设置</span><span class="sxs-lookup"><span data-stu-id="ee140-116">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="ee140-117">如何：在 Visual Basic 中更改用户设置</span><span class="sxs-lookup"><span data-stu-id="ee140-117">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="ee140-118">如何：在 Visual Basic 中为用户设置创建属性网格</span><span class="sxs-lookup"><span data-stu-id="ee140-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="ee140-119">管理应用程序设置 (.NET)</span><span class="sxs-lookup"><span data-stu-id="ee140-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
