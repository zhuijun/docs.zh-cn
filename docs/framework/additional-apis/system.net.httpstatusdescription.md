---
title: HttpStatusDescription 类（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990443"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="48a09-102">HttpStatusDescription 类</span><span class="sxs-lookup"><span data-stu-id="48a09-102">HttpStatusDescription class</span></span>

<span data-ttu-id="48a09-103">提供标准 HTTP 状态说明。</span><span class="sxs-lookup"><span data-stu-id="48a09-103">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="48a09-104">无法继承此类。</span><span class="sxs-lookup"><span data-stu-id="48a09-104">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="48a09-105">此类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="48a09-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="48a09-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="48a09-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="48a09-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="48a09-107">Get method</span></span>

<span data-ttu-id="48a09-108">返回与指定的 HTTP 状态代码相关联的说明。</span><span class="sxs-lookup"><span data-stu-id="48a09-108">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="48a09-109">参数</span><span class="sxs-lookup"><span data-stu-id="48a09-109">Parameters</span></span>

<span data-ttu-id="48a09-110">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="48a09-110">`code` <xref:System.Int32></span></span>

<span data-ttu-id="48a09-111">HTTP 状态代码，例如 `404` 。</span><span class="sxs-lookup"><span data-stu-id="48a09-111">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="48a09-112">返回值</span><span class="sxs-lookup"><span data-stu-id="48a09-112">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="48a09-113">HTTP 状态说明。</span><span class="sxs-lookup"><span data-stu-id="48a09-113">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="48a09-114">要求</span><span class="sxs-lookup"><span data-stu-id="48a09-114">Requirements</span></span>

<span data-ttu-id="48a09-115">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="48a09-115">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="48a09-116">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="48a09-116">**Assembly:** System (in System.dll)</span></span>
