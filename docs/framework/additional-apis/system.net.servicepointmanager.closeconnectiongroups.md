---
title: ServicePointManager. CloseConnectionGroups 方法（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990435"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="a76aa-102">ServicePointManager. CloseConnectionGroups 方法</span><span class="sxs-lookup"><span data-stu-id="a76aa-102">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="a76aa-103">循环访问所有服务点并关闭具有指定名称的连接组。</span><span class="sxs-lookup"><span data-stu-id="a76aa-103">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="a76aa-104">此方法是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="a76aa-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a76aa-105">在任何情况下，Microsoft 不支持在生产应用程序中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="a76aa-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="a76aa-106">参数</span><span class="sxs-lookup"><span data-stu-id="a76aa-106">Parameters</span></span>

<span data-ttu-id="a76aa-107">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a76aa-107">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="a76aa-108">要关闭的连接组的名称。</span><span class="sxs-lookup"><span data-stu-id="a76aa-108">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="a76aa-109">要求</span><span class="sxs-lookup"><span data-stu-id="a76aa-109">Requirements</span></span>

<span data-ttu-id="a76aa-110">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a76aa-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a76aa-111">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="a76aa-111">**Assembly:** System (in System.dll)</span></span>
