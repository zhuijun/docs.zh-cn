---
title: ConnectionGroup 字段 m_ConnectionList
description: 了解 .NET 中的 m_ConnectionList ConnectionGroup 字段，其中包含为其他属性提供相同 URI 和共享值的连接对象。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: 478b2441c062e8df6f4e718bd66d7af329f20f12
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989720"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="504c2-103">ConnectionGroup \_ ConnectionList 字段</span><span class="sxs-lookup"><span data-stu-id="504c2-103">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="504c2-104">`ConnectionGroup.m_ConnectionList`是一个 <xref:System.Collections.ArrayList> 连接对象，它提供相同的 URI 并为某些其他属性（如过期和身份验证）共享相同的值。</span><span class="sxs-lookup"><span data-stu-id="504c2-104">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="504c2-105">语法</span><span class="sxs-lookup"><span data-stu-id="504c2-105">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="504c2-106">此 `ConnectionGroup.m_ConnectionList` 字段是专用的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="504c2-106">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="504c2-107">在任何情况下，Microsoft 不支持在生产应用程序中使用此字段。</span><span class="sxs-lookup"><span data-stu-id="504c2-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="504c2-108">要求</span><span class="sxs-lookup"><span data-stu-id="504c2-108">Requirements</span></span>

<span data-ttu-id="504c2-109">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="504c2-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="504c2-110">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="504c2-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="504c2-111">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="504c2-111">**.NET Framework versions:** Available since 2.0.</span></span>
