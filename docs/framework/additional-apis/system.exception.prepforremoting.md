---
title: PrepForRemoting 方法（系统）
description: 查看 .NET 中的 PrepForRemoting 方法。 方法将服务器端堆栈跟踪添加到消息中，然后在客户端重新引发异常。
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105265"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="6a199-104">Exception.PrepForRemoting 方法</span><span class="sxs-lookup"><span data-stu-id="6a199-104">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="6a199-105">保留服务器端堆栈跟踪，方法是将其追加到消息，然后在客户端调用站点重新引发异常。</span><span class="sxs-lookup"><span data-stu-id="6a199-105">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="6a199-106">返回</span><span class="sxs-lookup"><span data-stu-id="6a199-106">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="6a199-107">此 <xref:System.Exception> 实例。</span><span class="sxs-lookup"><span data-stu-id="6a199-107">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a199-108">备注</span><span class="sxs-lookup"><span data-stu-id="6a199-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6a199-109">`Exception.PrepForRemoting`方法是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="6a199-109">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6a199-110">在任何情况下，Microsoft 不支持在生产应用程序中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="6a199-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a199-111">要求</span><span class="sxs-lookup"><span data-stu-id="6a199-111">Requirements</span></span>

<span data-ttu-id="6a199-112">**命名空间：** <xref:System></span><span class="sxs-lookup"><span data-stu-id="6a199-112">**Namespace:** <xref:System></span></span>

<span data-ttu-id="6a199-113">**程序集：** mscorlib.dll （在 mscorlib.dll 中）</span><span class="sxs-lookup"><span data-stu-id="6a199-113">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="6a199-114">**.NET Framework 版本：** 自1.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="6a199-114">**.NET Framework versions:** Available since 1.0.</span></span>
