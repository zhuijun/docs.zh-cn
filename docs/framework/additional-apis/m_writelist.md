---
title: 连接 m_WriteList 字段
description: 获取有关 .NET 中 m_WriteList 字段的信息。 此 ArrayList 字段包含排队等候通过 HTTP 发送的 HttpWebRequest 对象。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
ms.openlocfilehash: a627cb062036e3ab098c2d6e97f9a77ebfa75a33
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989589"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="a6439-104">Connection \_ WriteList 字段</span><span class="sxs-lookup"><span data-stu-id="a6439-104">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="a6439-105">`Connection.m_WriteList`是对象的，已 <xref:System.Collections.ArrayList> <xref:System.Net.HttpWebRequest> 排队等待通过 HTTP 发送。</span><span class="sxs-lookup"><span data-stu-id="a6439-105">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6439-106">语法</span><span class="sxs-lookup"><span data-stu-id="a6439-106">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="a6439-107">此 `Connection.m_WriteList` 字段是专用的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="a6439-107">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a6439-108">在任何情况下，Microsoft 不支持在生产应用程序中使用此字段。</span><span class="sxs-lookup"><span data-stu-id="a6439-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6439-109">要求</span><span class="sxs-lookup"><span data-stu-id="a6439-109">Requirements</span></span>

<span data-ttu-id="a6439-110">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a6439-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a6439-111">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="a6439-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="a6439-112">**.NET Framework 版本：** 自2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="a6439-112">**.NET Framework versions:** Available since 2.0.</span></span>
