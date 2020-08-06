---
title: 序列化中断性变更
description: 列出 .NET Core 和 .NET 5.0 及更高版本中序列化类别的中断性变更。
ms.date: 07/30/2020
ms.openlocfilehash: f635ff2cd233922a0bbb327de23c8bf25d344fa0
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517407"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="02874-103">序列化中断性变更</span><span class="sxs-lookup"><span data-stu-id="02874-103">Serialization breaking changes</span></span>

<span data-ttu-id="02874-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="02874-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="02874-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="02874-105">Breaking change</span></span> | <span data-ttu-id="02874-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="02874-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="02874-107">BinaryFormatter.Deserialize 重新包装 SerializationException 中的一些异常</span><span class="sxs-lookup"><span data-stu-id="02874-107">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="02874-108">5.0</span><span class="sxs-lookup"><span data-stu-id="02874-108">5.0</span></span> |

## <a name="net-core-50"></a><span data-ttu-id="02874-109">.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="02874-109">.NET Core 5.0</span></span>

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
