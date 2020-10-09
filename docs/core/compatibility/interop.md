---
title: 互操作中断性变更
description: 列出 .NET Core 和 .NET 5.0 及更高版本中互操作的中断性变更。
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438032"
---
# <a name="interop-breaking-changes"></a><span data-ttu-id="be150-103">互操作中断性变更</span><span class="sxs-lookup"><span data-stu-id="be150-103">Interop breaking changes</span></span>

<span data-ttu-id="be150-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="be150-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="be150-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="be150-105">Breaking change</span></span> | <span data-ttu-id="be150-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="be150-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="be150-107">将 RCW 强制转换为 `InterfaceIsIInspectable` 接口会引发 PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="be150-107">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | <span data-ttu-id="be150-108">5.0</span><span class="sxs-lookup"><span data-stu-id="be150-108">5.0</span></span> |
| [<span data-ttu-id="be150-109">不在非 Windows 平台上探测 A/W 后缀</span><span class="sxs-lookup"><span data-stu-id="be150-109">No A/W suffix probing on non-Windows platforms</span></span>](#no-aw-suffix-probing-on-non-windows-platforms) | <span data-ttu-id="be150-110">5.0</span><span class="sxs-lookup"><span data-stu-id="be150-110">5.0</span></span> |
| [<span data-ttu-id="be150-111">已从 .NET 中删除对 WinRT 的内置支持</span><span class="sxs-lookup"><span data-stu-id="be150-111">Built-in support for WinRT is removed from .NET</span></span>](#built-in-support-for-winrt-is-removed-from-net) | <span data-ttu-id="be150-112">5.0</span><span class="sxs-lookup"><span data-stu-id="be150-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="be150-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="be150-113">.NET 5.0</span></span>

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
