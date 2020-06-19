---
title: ServicePoint 字段 m_ConnectionGroupList
description: 了解 "m_ConnectionGroupList ServicePoint" 字段，它是一个连接组哈希表，其中每个连接组都在 .NET 中保存 ServicePoint URI 的连接。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989712"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="d3b2f-103">ServicePoint \_ ConnectionGroupList 字段</span><span class="sxs-lookup"><span data-stu-id="d3b2f-103">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="d3b2f-104">`ServicePoint.m_ConnectionGroupList`是一个 <xref:System.Collections.Hashtable> 连接组，每个组都有一个用于的 URI 的连接 <xref:System.Net.ServicePoint> 。</span><span class="sxs-lookup"><span data-stu-id="d3b2f-104">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3b2f-105">语法</span><span class="sxs-lookup"><span data-stu-id="d3b2f-105">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="d3b2f-106">此 `ServicePoint.m_ConnectionGroupList` 字段是专用的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="d3b2f-106">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d3b2f-107">在任何情况下，Microsoft 不支持在生产应用程序中使用此字段。</span><span class="sxs-lookup"><span data-stu-id="d3b2f-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3b2f-108">要求</span><span class="sxs-lookup"><span data-stu-id="d3b2f-108">Requirements</span></span>

<span data-ttu-id="d3b2f-109">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d3b2f-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d3b2f-110">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="d3b2f-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="d3b2f-111">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="d3b2f-111">**.NET Framework versions:** Available since 2.0.</span></span>
