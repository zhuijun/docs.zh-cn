---
title: HttpWebRequest 字段 _CoreResponse
description: 阅读有关 .NET 中的 _CoreResponse HttpWebRequest 字段的信息。 此字段是包含 HTTP 响应分析结果的 CoreResponseData 或 Exception 对象。
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989756"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="edc36-104">HttpWebRequest。 \_CoreResponse 字段</span><span class="sxs-lookup"><span data-stu-id="edc36-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="edc36-105">`HttpWebRequest._CoreResponse`[CoreResponseData](coreresponsedata.md) <xref:System.Exception> 包含 HTTP 响应分析结果的对象（CoreResponseData 或）。</span><span class="sxs-lookup"><span data-stu-id="edc36-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="edc36-106">语法</span><span class="sxs-lookup"><span data-stu-id="edc36-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="edc36-107">此 API 不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="edc36-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="edc36-108">相反，应使用 <xref:System.Diagnostics.DiagnosticSource> 挂钩网络代码。</span><span class="sxs-lookup"><span data-stu-id="edc36-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="edc36-109">请参阅[DiagnosticSource 用户指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="edc36-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="edc36-110">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="edc36-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="edc36-111">要求</span><span class="sxs-lookup"><span data-stu-id="edc36-111">Requirements</span></span>

<span data-ttu-id="edc36-112">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="edc36-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="edc36-113">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="edc36-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="edc36-114">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="edc36-114">**.NET Framework versions:** Available since 2.0.</span></span>
