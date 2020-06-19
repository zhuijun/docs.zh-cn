---
title: ServicePointManager 字段 s_ServicePointTable
description: 阅读有关 .NET 中的 s_ServicePointTable ServicePointManager 字段的信息。 此哈希表字段包含 AppDomain 中的活动 HTTP 连接（ServicePoints）。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989544"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="99931-104">ServicePointManager \_ ServicePointTable 字段</span><span class="sxs-lookup"><span data-stu-id="99931-104">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="99931-105">`ServicePointManager.s_ServicePointTable`一个 <xref:System.Collections.Hashtable> ，它包含中的活动 HTTP 连接的列表 <xref:System.Net.ServicePoint> <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="99931-105">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="99931-106">语法</span><span class="sxs-lookup"><span data-stu-id="99931-106">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="99931-107">此 `ServicePointManager.s_ServicePointTable` 字段是专用的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="99931-107">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="99931-108">在任何情况下，Microsoft 不支持在生产应用程序中使用此字段。</span><span class="sxs-lookup"><span data-stu-id="99931-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="99931-109">要求</span><span class="sxs-lookup"><span data-stu-id="99931-109">Requirements</span></span>

<span data-ttu-id="99931-110">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="99931-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="99931-111">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="99931-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="99931-112">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="99931-112">**.NET Framework versions:** Available since 2.0.</span></span>
