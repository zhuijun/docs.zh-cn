---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614338"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a><span data-ttu-id="132b8-101">.NET Framework 4.7.1 中的 ASP.NET 辅助功能改进</span><span class="sxs-lookup"><span data-stu-id="132b8-101">ASP.NET Accessibility Improvements in .NET Framework 4.7.1</span></span>

#### <a name="details"></a><span data-ttu-id="132b8-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="132b8-102">Details</span></span>

<span data-ttu-id="132b8-103">从 .NET Framework 4.7.1 开始，ASP.NET 改进了 ASP.NET Web 控件与 Visual Studio 中的辅助功能技术配合使用的方式，以更好地支持 ASP.NET 客户。</span><span class="sxs-lookup"><span data-stu-id="132b8-103">Starting with the .NET Framework 4.7.1, ASP.NET has improved how ASP.NET Web Controls work with accessibility technology in Visual Studio to better support ASP.NET customers.</span></span>  <span data-ttu-id="132b8-104">其中包括以下更改：</span><span class="sxs-lookup"><span data-stu-id="132b8-104">These include the following changes:</span></span>

- <span data-ttu-id="132b8-105">在以下控件中实现缺失 UI 的辅助功能模式：例如“详细信息视图”向导中的“添加字段”对话框或“ListView”向导的“配置 ListView”对话框。</span><span class="sxs-lookup"><span data-stu-id="132b8-105">Changes to implement missing UI accessibility patterns in controls, like the Add Field dialog in the Details View wizard, or the Configure ListView dialog of the ListView wizard.</span></span>
- <span data-ttu-id="132b8-106">改善在高对比度模式下（如数据页导航字段编辑器）的显示。</span><span class="sxs-lookup"><span data-stu-id="132b8-106">Changes to improve the display in High Contrast mode, like the Data Pager Fields Editor.</span></span>
- <span data-ttu-id="132b8-107">更改用于改善以下控件的键盘导航体验：如 DataPager 控件的“编辑页导航字段”向导中的“字段”对话框、“配置 ObjectContext”对话框或“配置数据源”向导的“配置数据选择”对话框。</span><span class="sxs-lookup"><span data-stu-id="132b8-107">Changes to improve the keyboard navigation experiences for controls, like the Fields dialog in the Edit Pager Fields wizard of the DataPager control, the Configure ObjectContext dialog, or the Configure Data Selection dialog of the Configure Data Source wizard.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="132b8-108">建议</span><span class="sxs-lookup"><span data-stu-id="132b8-108">Suggestion</span></span>

<span data-ttu-id="132b8-109">**如何选择启用或弃用这些更改** 为使 Visual Studio 设计器从这些更改中获益，它必须在 .NET Framework 4.7.1 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="132b8-109">**How to opt in or out of these changes** In order for the Visual Studio Designer to benefit from these changes, it must run on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="132b8-110">Web 应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="132b8-110">The web application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="132b8-111">安装 Visual Studio 2017 15.3 或更高版本，它在默认情况下使用以下 AppContext 开关支持新的辅助功能。</span><span class="sxs-lookup"><span data-stu-id="132b8-111">Install Visual Studio 2017 15.3 or later, which supports the new accessibility features with the following AppContext Switch by default.</span></span>
- <span data-ttu-id="132b8-112">如以下示例所示，通过将 `Switch.UseLegacyAccessibilityFeatures` AppContext 开关添加到 devenv.exe.config 文件中的 `<runtime>` 部分并将其设置为 `false`，可选择弃用旧版辅助功能行为。</span><span class="sxs-lookup"><span data-stu-id="132b8-112">Opt out of the legacy accessibility behaviors by adding the `Switch.UseLegacyAccessibilityFeatures` AppContext switch to the `<runtime>` section in the devenv.exe.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

<span data-ttu-id="132b8-113">面向 .NET Framework 4.7.1 或更高版本并希望保留旧版辅助功能行为的应用程序，可通过将此 AppContext 开关显式设置为 `true` 来选择启用旧版辅助功能。</span><span class="sxs-lookup"><span data-stu-id="132b8-113">Applications that target the .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="132b8-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="132b8-114">Name</span></span>    | <span data-ttu-id="132b8-115">“值”</span><span class="sxs-lookup"><span data-stu-id="132b8-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="132b8-116">范围</span><span class="sxs-lookup"><span data-stu-id="132b8-116">Scope</span></span>   | <span data-ttu-id="132b8-117">次要</span><span class="sxs-lookup"><span data-stu-id="132b8-117">Minor</span></span>       |
| <span data-ttu-id="132b8-118">Version</span><span class="sxs-lookup"><span data-stu-id="132b8-118">Version</span></span> | <span data-ttu-id="132b8-119">4.7.1</span><span class="sxs-lookup"><span data-stu-id="132b8-119">4.7.1</span></span>       |
| <span data-ttu-id="132b8-120">类型</span><span class="sxs-lookup"><span data-stu-id="132b8-120">Type</span></span>    | <span data-ttu-id="132b8-121">重定目标</span><span class="sxs-lookup"><span data-stu-id="132b8-121">Retargeting</span></span> |
