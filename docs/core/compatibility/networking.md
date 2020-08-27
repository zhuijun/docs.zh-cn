---
title: 网络中断性变更
description: 列出 .NET Core 中网络的中断性变更。
ms.date: 05/05/2020
ms.openlocfilehash: 568d26bde43ccd6e19fbe2d947f576ef5f99450a
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608476"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="b821f-103">网络中断性变更</span><span class="sxs-lookup"><span data-stu-id="b821f-103">Networking breaking changes</span></span>

<span data-ttu-id="b821f-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="b821f-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b821f-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="b821f-105">Breaking change</span></span> | <span data-ttu-id="b821f-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="b821f-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="b821f-107">已从 .NET 运行时中删除 WinHttpHandler</span><span class="sxs-lookup"><span data-stu-id="b821f-107">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="b821f-108">5.0</span><span class="sxs-lookup"><span data-stu-id="b821f-108">5.0</span></span> |
| [<span data-ttu-id="b821f-109">MulticastOption.Group 不接受 Null 值</span><span class="sxs-lookup"><span data-stu-id="b821f-109">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="b821f-110">5.0</span><span class="sxs-lookup"><span data-stu-id="b821f-110">5.0</span></span> |
| [<span data-ttu-id="b821f-111">HttpRequestMessage.Version 的默认值已更改为 1.1</span><span class="sxs-lookup"><span data-stu-id="b821f-111">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="b821f-112">3.0</span><span class="sxs-lookup"><span data-stu-id="b821f-112">3.0</span></span> |
| [<span data-ttu-id="b821f-113">WebClient.CancelAsync 并不总是立即取消</span><span class="sxs-lookup"><span data-stu-id="b821f-113">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="b821f-114">2.0</span><span class="sxs-lookup"><span data-stu-id="b821f-114">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="b821f-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b821f-115">.NET 5.0</span></span>

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="b821f-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b821f-116">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="b821f-117">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b821f-117">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
