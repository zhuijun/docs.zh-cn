---
title: 全球化中断性变更
description: 列出 .NET Core 中全球化过程内的中断性变更。
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702283"
---
# <a name="globalization-breaking-changes"></a><span data-ttu-id="85190-103">全球化中断性变更</span><span class="sxs-lookup"><span data-stu-id="85190-103">Globalization breaking changes</span></span>

<span data-ttu-id="85190-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="85190-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="85190-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="85190-105">Breaking change</span></span> | <span data-ttu-id="85190-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="85190-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="85190-107">全球化 API 在 Windows 上使用 ICU 库</span><span class="sxs-lookup"><span data-stu-id="85190-107">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="85190-108">5.0</span><span class="sxs-lookup"><span data-stu-id="85190-108">5.0</span></span> |
| [<span data-ttu-id="85190-109">StringInfo 和 TextElementEnumerator 现在与 UAX29 兼容</span><span class="sxs-lookup"><span data-stu-id="85190-109">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="85190-110">5.0</span><span class="sxs-lookup"><span data-stu-id="85190-110">5.0</span></span> |
| [<span data-ttu-id="85190-111">“C”区域设置映射到固定区域设置</span><span class="sxs-lookup"><span data-stu-id="85190-111">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="85190-112">3.0</span><span class="sxs-lookup"><span data-stu-id="85190-112">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="85190-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="85190-113">.NET 5.0</span></span>

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="85190-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="85190-114">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
