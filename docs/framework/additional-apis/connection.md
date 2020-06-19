---
title: Connection 类（System.Net）
description: 了解 .NET 中的 Connection 类。 此类分析服务器响应、队列请求和管道请求。 它位于 System.NET 命名空间中。
ms.date: 05/01/2017
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
ms.openlocfilehash: cb28724ed782fc5395dc74e9c59249ebdea44ddf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989827"
---
# <a name="connection-class"></a><span data-ttu-id="8cac1-105">连接类</span><span class="sxs-lookup"><span data-stu-id="8cac1-105">Connection Class</span></span>

<span data-ttu-id="8cac1-106">`Connection`类分析服务器响应、队列请求和管道请求。</span><span class="sxs-lookup"><span data-stu-id="8cac1-106">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="8cac1-107">语法</span><span class="sxs-lookup"><span data-stu-id="8cac1-107">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="8cac1-108">`Connection`类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="8cac1-108">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8cac1-109">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="8cac1-109">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8cac1-110">要求</span><span class="sxs-lookup"><span data-stu-id="8cac1-110">Requirements</span></span>

<span data-ttu-id="8cac1-111">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="8cac1-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="8cac1-112">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="8cac1-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="8cac1-113">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="8cac1-113">**.NET Framework versions:** Available since 2.0.</span></span>
