---
title: HttpWebRequest 字段 _HttpResponse
description: 了解 .NET 中的 _HttpResponse HttpWebRequest 字段。 此字段是包含 HTTP 请求中的 HTTP 响应详细信息的 HttpWebResponse 类型。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._HttpResponse
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: eab9b789-beb4-4c28-b2d8-78debc7ba129
ms.openlocfilehash: 70058e1183abf5b6bfd172497f65a3ceb2344060
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989956"
---
# <a name="httpwebrequest_httpresponse-field"></a><span data-ttu-id="249e3-104">HttpWebRequest。 \_Httpresponse.cache 字段</span><span class="sxs-lookup"><span data-stu-id="249e3-104">HttpWebRequest.\_HttpResponse Field</span></span>

<span data-ttu-id="249e3-105">`HttpWebRequest._HttpResponse`是 <xref:System.Net.HttpWebResponse> 包含来自 http 请求的 http 响应详细信息的。</span><span class="sxs-lookup"><span data-stu-id="249e3-105">`HttpWebRequest._HttpResponse` is an <xref:System.Net.HttpWebResponse> containing HTTP response details from an HTTP request.</span></span> <span data-ttu-id="249e3-106">在 `null` 收到 HTTP 响应之前，可以使用此方法。</span><span class="sxs-lookup"><span data-stu-id="249e3-106">It can be `null` until an HTTP response is received.</span></span>

## <a name="syntax"></a><span data-ttu-id="249e3-107">语法</span><span class="sxs-lookup"><span data-stu-id="249e3-107">Syntax</span></span>
  
```csharp  
internal HttpWebResponse _HttpResponse
```

> [!WARNING]
> <span data-ttu-id="249e3-108">此 `HttpWebRequest._HttpResponse` 字段是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="249e3-108">The `HttpWebRequest._HttpResponse` field is internal and not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="249e3-109">在任何情况下，Microsoft 不支持在生产应用程序中使用此字段。</span><span class="sxs-lookup"><span data-stu-id="249e3-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="249e3-110">要求</span><span class="sxs-lookup"><span data-stu-id="249e3-110">Requirements</span></span>

<span data-ttu-id="249e3-111">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="249e3-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="249e3-112">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="249e3-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="249e3-113">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="249e3-113">**.NET Framework versions:** Available since 2.0.</span></span>
