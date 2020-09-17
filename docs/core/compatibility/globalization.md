---
title: 全球化中断性变更
description: 列出 .NET Core 中全球化过程内的中断性变更。
ms.date: 04/07/2020
ms.openlocfilehash: 93990d89204df1b2d7498e1d748378fae05598c3
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065055"
---
# <a name="globalization-breaking-changes"></a><span data-ttu-id="17f00-103">全球化中断性变更</span><span class="sxs-lookup"><span data-stu-id="17f00-103">Globalization breaking changes</span></span>

<span data-ttu-id="17f00-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="17f00-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="17f00-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="17f00-105">Breaking change</span></span> | <span data-ttu-id="17f00-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="17f00-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="17f00-107">某些 Latin-1 字符的 Unicode 类别已更改</span><span class="sxs-lookup"><span data-stu-id="17f00-107">Unicode category changed for some Latin-1 characters</span></span>](#unicode-category-changed-for-some-latin-1-characters) | <span data-ttu-id="17f00-108">5.0</span><span class="sxs-lookup"><span data-stu-id="17f00-108">5.0</span></span> |
| [<span data-ttu-id="17f00-109">全球化 API 在 Windows 上使用 ICU 库</span><span class="sxs-lookup"><span data-stu-id="17f00-109">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="17f00-110">5.0</span><span class="sxs-lookup"><span data-stu-id="17f00-110">5.0</span></span> |
| [<span data-ttu-id="17f00-111">StringInfo 和 TextElementEnumerator 现在与 UAX29 兼容</span><span class="sxs-lookup"><span data-stu-id="17f00-111">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="17f00-112">5.0</span><span class="sxs-lookup"><span data-stu-id="17f00-112">5.0</span></span> |
| [<span data-ttu-id="17f00-113">“C”区域设置映射到固定区域设置</span><span class="sxs-lookup"><span data-stu-id="17f00-113">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="17f00-114">3.0</span><span class="sxs-lookup"><span data-stu-id="17f00-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="17f00-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="17f00-115">.NET 5.0</span></span>

[!INCLUDE [unicode-categories-for-latin1-chars](../../../includes/core-changes/globalization/5.0/unicode-categories-for-latin1-chars.md)]

***

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="17f00-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="17f00-116">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
