---
title: Windows 窗体重大更改
description: 列出适用于 .NET Core 的 Windows 窗体中的中断性变更。
ms.date: 01/08/2020
ms.openlocfilehash: beb9a42e4b5007f03480cd74f57bbfbbfc3f48b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556138"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="fde6e-103">Windows 窗体中的中断性变更</span><span class="sxs-lookup"><span data-stu-id="fde6e-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="fde6e-104">已在 .NET Core 的版本 3.0 中添加 Windows 窗体支持。</span><span class="sxs-lookup"><span data-stu-id="fde6e-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="fde6e-105">本文按引入中断性变更的 .NET Core 版本列出了 Windows 窗体的中断性变更。</span><span class="sxs-lookup"><span data-stu-id="fde6e-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="fde6e-106">如果要从 .NET Framework 或 .NET Core 的早期版本（3.0 或更高版本）升级 Windows 窗体应用，本文能为你提供帮助。</span><span class="sxs-lookup"><span data-stu-id="fde6e-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="fde6e-107">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="fde6e-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="fde6e-108">重大更改</span><span class="sxs-lookup"><span data-stu-id="fde6e-108">Breaking change</span></span> | <span data-ttu-id="fde6e-109">引入的版本</span><span class="sxs-lookup"><span data-stu-id="fde6e-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="fde6e-110">已删除的状态栏控件</span><span class="sxs-lookup"><span data-stu-id="fde6e-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="fde6e-111">5.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-111">5.0</span></span> |
| [<span data-ttu-id="fde6e-112">WinForms 方法现在会引发 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="fde6e-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="fde6e-113">5.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-113">5.0</span></span> |
| [<span data-ttu-id="fde6e-114">WinForms 方法现在会引发 ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="fde6e-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="fde6e-115">5.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-115">5.0</span></span> |
| [<span data-ttu-id="fde6e-116">WinForms 属性现在引发 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="fde6e-116">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="fde6e-117">5.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-117">5.0</span></span> |
| [<span data-ttu-id="fde6e-118">已删除的控件</span><span class="sxs-lookup"><span data-stu-id="fde6e-118">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="fde6e-119">3.1</span><span class="sxs-lookup"><span data-stu-id="fde6e-119">3.1</span></span> |
| [<span data-ttu-id="fde6e-120">如果显示工具提示，则不引发 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="fde6e-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="fde6e-121">3.1</span><span class="sxs-lookup"><span data-stu-id="fde6e-121">3.1</span></span> |
| [<span data-ttu-id="fde6e-122">Control.DefaultFont 已更改为 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="fde6e-122">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="fde6e-123">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-123">3.0</span></span> |
| [<span data-ttu-id="fde6e-124">FolderBrowserDialog 的现代化</span><span class="sxs-lookup"><span data-stu-id="fde6e-124">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="fde6e-125">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-125">3.0</span></span> |
| [<span data-ttu-id="fde6e-126">已从一些 Windows 窗体类型中删除 SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="fde6e-126">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="fde6e-127">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-127">3.0</span></span> |
| [<span data-ttu-id="fde6e-128">不支持 AllowUpdateChildControlIndexForTabControls 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-128">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-129">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-129">3.0</span></span> |
| [<span data-ttu-id="fde6e-130">不支持 DomainUpDown.UseLegacyScrolling 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-130">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-131">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-131">3.0</span></span> |
| [<span data-ttu-id="fde6e-132">不支持 DoNotLoadLatestRichEditControl 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-132">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-133">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-133">3.0</span></span> |
| [<span data-ttu-id="fde6e-134">不支持 DoNotSupportSelectAllShortcutInMultilineTextBox 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-134">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-135">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-135">3.0</span></span> |
| [<span data-ttu-id="fde6e-136">不支持 DontSupportReentrantFilterMessage 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-136">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-137">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-137">3.0</span></span> |
| [<span data-ttu-id="fde6e-138">不支持 EnableVisualStyleValidation 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-138">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-139">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-139">3.0</span></span> |
| [<span data-ttu-id="fde6e-140">不支持 UseLegacyContextMenuStripSourceControlValue 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-140">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-141">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-141">3.0</span></span> |
| [<span data-ttu-id="fde6e-142">不支持 UseLegacyImages 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="fde6e-142">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="fde6e-143">3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-143">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="fde6e-144">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-144">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="fde6e-145">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="fde6e-145">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="fde6e-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fde6e-146">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

## <a name="see-also"></a><span data-ttu-id="fde6e-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="fde6e-147">See also</span></span>

- [<span data-ttu-id="fde6e-148">将 Windows 窗体应用移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="fde6e-148">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
