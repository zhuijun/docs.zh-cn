---
title: ConnectionGroup 类
description: 阅读有关 ConnectionGroup 类的信息，该类在 ServicePoint 上下文中对连接进行分组，并用于维护 .NET 中网络资源的上下文。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 25c08217-fdeb-44b9-9cd6-1b4955d6e602
ms.openlocfilehash: 7121713b26880f2490b40d59d92d431a567519b3
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989814"
---
# <a name="connectiongroup-class"></a><span data-ttu-id="6db5c-103">ConnectionGroup 类</span><span class="sxs-lookup"><span data-stu-id="6db5c-103">ConnectionGroup Class</span></span>

<span data-ttu-id="6db5c-104">`ConnectionGroup`类对上下文内的连接列表进行分组 <xref:System.Net.ServicePoint> ，并用于维护网络资源（例如，代理和单独的客户端）的上下文。</span><span class="sxs-lookup"><span data-stu-id="6db5c-104">The `ConnectionGroup` class groups a list of connections within the <xref:System.Net.ServicePoint> context and is used to maintain context for network resources (for example, proxies and separate clients).</span></span>

## <a name="syntax"></a><span data-ttu-id="6db5c-105">语法</span><span class="sxs-lookup"><span data-stu-id="6db5c-105">Syntax</span></span>
  
```csharp  
internal class ConnectionGroup
```

> [!WARNING]
> <span data-ttu-id="6db5c-106">`ConnectionGroup`类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="6db5c-106">The `ConnectionGroup` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6db5c-107">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="6db5c-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6db5c-108">要求</span><span class="sxs-lookup"><span data-stu-id="6db5c-108">Requirements</span></span>

<span data-ttu-id="6db5c-109">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6db5c-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6db5c-110">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="6db5c-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="6db5c-111">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="6db5c-111">**.NET Framework versions:** Available since 2.0.</span></span>
