---
ms.openlocfilehash: 15418d1ac3ade6a0fa35ca61a02134e20af1baea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602740"
---

<span data-ttu-id="aa5ff-101">安装 .NET Core 包时，可能会看到类似于 `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` 的错误。</span><span class="sxs-lookup"><span data-stu-id="aa5ff-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="aa5ff-102">此错误表示 .NET Core 的包源正在通过更新的包版本进行更新，应稍后重试。</span><span class="sxs-lookup"><span data-stu-id="aa5ff-102">This error could mean that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="aa5ff-103">升级期间，包源的不可用时间不应超过 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="aa5ff-103">During an upgrade, the package feed shouldn't be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="aa5ff-104">如果持续收到此错误超过 30 分钟，请在 <https://github.com/dotnet/core/issues> 中提交问题。</span><span class="sxs-lookup"><span data-stu-id="aa5ff-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
