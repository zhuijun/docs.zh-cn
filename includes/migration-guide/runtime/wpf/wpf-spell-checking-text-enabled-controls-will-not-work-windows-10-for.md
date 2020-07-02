---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621159"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="c7d44-101">支持文本的控件中的 WPF 拼写检查在 Windows 10 中将不适用于 OS 输入语言列表以外的语言</span><span class="sxs-lookup"><span data-stu-id="c7d44-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="c7d44-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c7d44-102">Details</span></span>

<span data-ttu-id="c7d44-103">在 Windows 10 上运行时，拼写检查器可能不适用于支持 WPF 文本的控件，因为平台拼写检查功能仅适用于输入语言列表中的语言。在 Windows 10 中，将语言添加到可用键盘的列表时，Windows 自动下载并安装相应的按需功能 (FOD) 包，以提供拼写检查功能。</span><span class="sxs-lookup"><span data-stu-id="c7d44-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="c7d44-104">通过将语言添加到输入语言列表，将支持拼写检查器。</span><span class="sxs-lookup"><span data-stu-id="c7d44-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c7d44-105">建议</span><span class="sxs-lookup"><span data-stu-id="c7d44-105">Suggestion</span></span>

<span data-ttu-id="c7d44-106">请注意，必须将要进行拼写检查的语言或文本添加到输入语言以在 Windows 10 中使用拼写检查功能。</span><span class="sxs-lookup"><span data-stu-id="c7d44-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="c7d44-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="c7d44-107">Name</span></span>    | <span data-ttu-id="c7d44-108">值</span><span class="sxs-lookup"><span data-stu-id="c7d44-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c7d44-109">范围</span><span class="sxs-lookup"><span data-stu-id="c7d44-109">Scope</span></span>   |<span data-ttu-id="c7d44-110">边缘</span><span class="sxs-lookup"><span data-stu-id="c7d44-110">Edge</span></span>|
|<span data-ttu-id="c7d44-111">Version</span><span class="sxs-lookup"><span data-stu-id="c7d44-111">Version</span></span>|<span data-ttu-id="c7d44-112">4.6</span><span class="sxs-lookup"><span data-stu-id="c7d44-112">4.6</span></span>|
|<span data-ttu-id="c7d44-113">类型</span><span class="sxs-lookup"><span data-stu-id="c7d44-113">Type</span></span>|<span data-ttu-id="c7d44-114">运行时</span><span class="sxs-lookup"><span data-stu-id="c7d44-114">Runtime</span></span>|
