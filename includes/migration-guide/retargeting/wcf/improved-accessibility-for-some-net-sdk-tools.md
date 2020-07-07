---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614386"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="168f7-101">某些 .NET SDK 工具的改进的辅助功能</span><span class="sxs-lookup"><span data-stu-id="168f7-101">Improved accessibility for some .NET SDK tools</span></span>

#### <a name="details"></a><span data-ttu-id="168f7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="168f7-102">Details</span></span>

<span data-ttu-id="168f7-103">在 .NET Framework SDK 4.7.1 中，已通过修复各种辅助功能问题，改进了 SvcConfigEditor.exe 和 SvcTraceViewer.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="168f7-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="168f7-104">其中大多数都是一些小问题，如未定义名称或未正确实现某些 UI 自动化模式。</span><span class="sxs-lookup"><span data-stu-id="168f7-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="168f7-105">虽然许多用户不会意识到这些小问题的重要性，但使用屏幕阅读器等辅助技术的客户会发现这些 SDK 工具更易于访问。</span><span class="sxs-lookup"><span data-stu-id="168f7-105">While many users wouldn't be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="168f7-106">当然，这些修复程序改变了以前的某些行为，如键盘焦点顺序。为获取这些工具中的所有辅助功能修复程序，可对 app.config 文件执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="168f7-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| <span data-ttu-id="168f7-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="168f7-107">Name</span></span>    | <span data-ttu-id="168f7-108">“值”</span><span class="sxs-lookup"><span data-stu-id="168f7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="168f7-109">范围</span><span class="sxs-lookup"><span data-stu-id="168f7-109">Scope</span></span>   | <span data-ttu-id="168f7-110">边缘</span><span class="sxs-lookup"><span data-stu-id="168f7-110">Edge</span></span>        |
| <span data-ttu-id="168f7-111">Version</span><span class="sxs-lookup"><span data-stu-id="168f7-111">Version</span></span> | <span data-ttu-id="168f7-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="168f7-112">4.7.1</span></span>       |
| <span data-ttu-id="168f7-113">类型</span><span class="sxs-lookup"><span data-stu-id="168f7-113">Type</span></span>    | <span data-ttu-id="168f7-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="168f7-114">Retargeting</span></span> |
