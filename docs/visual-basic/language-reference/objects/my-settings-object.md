---
title: My.Settings 对象
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: c905ff85c8e9729dd4d6068f0d34f729962bbb57
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372396"
---
# <a name="mysettings-object"></a><span data-ttu-id="bab37-102">My.Settings 对象</span><span class="sxs-lookup"><span data-stu-id="bab37-102">My.Settings Object</span></span>
<span data-ttu-id="bab37-103">提供用于访问应用程序设置的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="bab37-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bab37-104">备注</span><span class="sxs-lookup"><span data-stu-id="bab37-104">Remarks</span></span>  
 <span data-ttu-id="bab37-105">`My.Settings`对象提供对应用程序设置的访问权限，并允许您动态存储和检索应用程序的属性设置和其他信息。</span><span class="sxs-lookup"><span data-stu-id="bab37-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="bab37-106">有关详细信息，请参阅[管理应用程序设置 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="bab37-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bab37-107">属性</span><span class="sxs-lookup"><span data-stu-id="bab37-107">Properties</span></span>  
 <span data-ttu-id="bab37-108">`My.Settings` 对象的属性提供对应用程序设置的访问。</span><span class="sxs-lookup"><span data-stu-id="bab37-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="bab37-109">若要添加或删除设置，请使用 "**设置设计器**"。</span><span class="sxs-lookup"><span data-stu-id="bab37-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="bab37-110">每个设置都具有**名称**、**类型**、**作用域**和**值**，并且这些设置确定如何在对象中显示每个设置的属性 `My.Settings` ：</span><span class="sxs-lookup"><span data-stu-id="bab37-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="bab37-111">**名称**确定属性的名称。</span><span class="sxs-lookup"><span data-stu-id="bab37-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="bab37-112">**类型**确定属性的类型。</span><span class="sxs-lookup"><span data-stu-id="bab37-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="bab37-113">**Scope**指示属性是否为只读。</span><span class="sxs-lookup"><span data-stu-id="bab37-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="bab37-114">如果值为 "**应用程序**"，则属性是只读的;如果值是**User**，则属性是可读写的。</span><span class="sxs-lookup"><span data-stu-id="bab37-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="bab37-115">**值**是属性的默认值。</span><span class="sxs-lookup"><span data-stu-id="bab37-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bab37-116">方法</span><span class="sxs-lookup"><span data-stu-id="bab37-116">Methods</span></span>  
  
|<span data-ttu-id="bab37-117">方法</span><span class="sxs-lookup"><span data-stu-id="bab37-117">Method</span></span>|<span data-ttu-id="bab37-118">说明</span><span class="sxs-lookup"><span data-stu-id="bab37-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="bab37-119">重新加载上次保存的值中的用户设置。</span><span class="sxs-lookup"><span data-stu-id="bab37-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="bab37-120">保存当前用户设置。</span><span class="sxs-lookup"><span data-stu-id="bab37-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="bab37-121">`My.Settings`对象还提供从类继承的高级属性和方法 <xref:System.Configuration.ApplicationSettingsBase> 。</span><span class="sxs-lookup"><span data-stu-id="bab37-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="bab37-122">任务</span><span class="sxs-lookup"><span data-stu-id="bab37-122">Tasks</span></span>  
 <span data-ttu-id="bab37-123">下表列出了涉及对象的任务的示例 `My.Settings` 。</span><span class="sxs-lookup"><span data-stu-id="bab37-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="bab37-124">功能</span><span class="sxs-lookup"><span data-stu-id="bab37-124">To</span></span>|<span data-ttu-id="bab37-125">查看</span><span class="sxs-lookup"><span data-stu-id="bab37-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="bab37-126">读取应用程序设置</span><span class="sxs-lookup"><span data-stu-id="bab37-126">Read an application setting</span></span>|[<span data-ttu-id="bab37-127">如何：在 Visual Basic 中读取应用程序设置</span><span class="sxs-lookup"><span data-stu-id="bab37-127">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="bab37-128">更改用户设置</span><span class="sxs-lookup"><span data-stu-id="bab37-128">Change a user setting</span></span>|[<span data-ttu-id="bab37-129">如何：在 Visual Basic 中更改用户设置</span><span class="sxs-lookup"><span data-stu-id="bab37-129">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="bab37-130">持久保存用户设置</span><span class="sxs-lookup"><span data-stu-id="bab37-130">Persist user settings</span></span>|[<span data-ttu-id="bab37-131">如何：在 Visual Basic 中暂留用户设置</span><span class="sxs-lookup"><span data-stu-id="bab37-131">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="bab37-132">创建用户设置的属性网格</span><span class="sxs-lookup"><span data-stu-id="bab37-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="bab37-133">如何：在 Visual Basic 中为用户设置创建属性网格</span><span class="sxs-lookup"><span data-stu-id="bab37-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="bab37-134">示例</span><span class="sxs-lookup"><span data-stu-id="bab37-134">Example</span></span>  
 <span data-ttu-id="bab37-135">此示例显示 `Nickname` 设置的值。</span><span class="sxs-lookup"><span data-stu-id="bab37-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="bab37-136">若要使此示例正常工作，应用程序必须具有类型为 `String` 的 `Nickname` 设置。</span><span class="sxs-lookup"><span data-stu-id="bab37-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab37-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bab37-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="bab37-138">如何：在 Visual Basic 中读取应用程序设置</span><span class="sxs-lookup"><span data-stu-id="bab37-138">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="bab37-139">如何：在 Visual Basic 中更改用户设置</span><span class="sxs-lookup"><span data-stu-id="bab37-139">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="bab37-140">如何：在 Visual Basic 中暂留用户设置</span><span class="sxs-lookup"><span data-stu-id="bab37-140">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="bab37-141">如何：在 Visual Basic 中为用户设置创建属性网格</span><span class="sxs-lookup"><span data-stu-id="bab37-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="bab37-142">管理应用程序设置 (.NET)</span><span class="sxs-lookup"><span data-stu-id="bab37-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
