---
title: 设置了 webheadercollection. AddInternal 方法（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990432"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="89708-102">设置了 webheadercollection. AddInternal 方法</span><span class="sxs-lookup"><span data-stu-id="89708-102">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="89708-103">将具有指定名称和值的新标头添加到集合，并跳过检查。</span><span class="sxs-lookup"><span data-stu-id="89708-103">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="89708-104">此方法是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="89708-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="89708-105">在任何情况下，Microsoft 不支持在生产应用程序中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="89708-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="89708-106">参数</span><span class="sxs-lookup"><span data-stu-id="89708-106">Parameters</span></span>

- <span data-ttu-id="89708-107">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="89708-107">`name` <xref:System.String></span></span>

  <span data-ttu-id="89708-108">标头的名称。</span><span class="sxs-lookup"><span data-stu-id="89708-108">The name of the header.</span></span>

- <span data-ttu-id="89708-109">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="89708-109">`value` <xref:System.String></span></span>

  <span data-ttu-id="89708-110">标头的值。</span><span class="sxs-lookup"><span data-stu-id="89708-110">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="89708-111">要求</span><span class="sxs-lookup"><span data-stu-id="89708-111">Requirements</span></span>

<span data-ttu-id="89708-112">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="89708-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="89708-113">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="89708-113">**Assembly:** System (in System.dll)</span></span>
