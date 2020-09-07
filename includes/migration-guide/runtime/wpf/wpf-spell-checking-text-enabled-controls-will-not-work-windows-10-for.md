---
ms.openlocfilehash: 6d7f998cda6326e1f584713576a0aa27b3a68655
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496152"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="392cb-101">支持文本的控件中的 WPF 拼写检查在 Windows 10 中将不适用于 OS 输入语言列表以外的语言</span><span class="sxs-lookup"><span data-stu-id="392cb-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="392cb-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="392cb-102">Details</span></span>

<span data-ttu-id="392cb-103">在 Windows 10 上运行时，拼写检查器可能不适用于支持 WPF 文本的控件，因为平台拼写检查功能仅适用于输入语言列表中的语言。在 Windows 10 中，将语言添加到可用键盘的列表时，Windows 自动下载并安装相应的按需功能 (FOD) 包，以提供拼写检查功能。</span><span class="sxs-lookup"><span data-stu-id="392cb-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="392cb-104">通过将语言添加到输入语言列表，将支持拼写检查器。</span><span class="sxs-lookup"><span data-stu-id="392cb-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="392cb-105">建议</span><span class="sxs-lookup"><span data-stu-id="392cb-105">Suggestion</span></span>

<span data-ttu-id="392cb-106">请注意，必须将要进行拼写检查的语言或文本添加到输入语言以在 Windows 10 中使用拼写检查功能。</span><span class="sxs-lookup"><span data-stu-id="392cb-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="392cb-107">名称</span><span class="sxs-lookup"><span data-stu-id="392cb-107">Name</span></span>    | <span data-ttu-id="392cb-108">值</span><span class="sxs-lookup"><span data-stu-id="392cb-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="392cb-109">范围</span><span class="sxs-lookup"><span data-stu-id="392cb-109">Scope</span></span>   |<span data-ttu-id="392cb-110">边缘</span><span class="sxs-lookup"><span data-stu-id="392cb-110">Edge</span></span>|
|<span data-ttu-id="392cb-111">Version</span><span class="sxs-lookup"><span data-stu-id="392cb-111">Version</span></span>|<span data-ttu-id="392cb-112">4.6</span><span class="sxs-lookup"><span data-stu-id="392cb-112">4.6</span></span>|
|<span data-ttu-id="392cb-113">类型</span><span class="sxs-lookup"><span data-stu-id="392cb-113">Type</span></span>|<span data-ttu-id="392cb-114">运行时</span><span class="sxs-lookup"><span data-stu-id="392cb-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="392cb-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="392cb-115">Affected APIs</span></span>

<span data-ttu-id="392cb-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="392cb-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
