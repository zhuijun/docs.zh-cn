---
title: ExceptionHelper 类（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ExceptionHelper
- System.Net.ExceptionHelper.WebPermissionUnrestricted
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 14a6172f7a0321ba9b2dd1744799017271c4332c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990445"
---
# <a name="exceptionhelper-class"></a><span data-ttu-id="a1d99-102">ExceptionHelper 类</span><span class="sxs-lookup"><span data-stu-id="a1d99-102">ExceptionHelper class</span></span>

<span data-ttu-id="a1d99-103">提供具有标准化错误消息的异常。</span><span class="sxs-lookup"><span data-stu-id="a1d99-103">Provides exceptions with standardized error messages.</span></span> <span data-ttu-id="a1d99-104">无法继承此类。</span><span class="sxs-lookup"><span data-stu-id="a1d99-104">This class cannot be inherited.</span></span>

```csharp
internal static class ExceptionHelper
```

> [!WARNING]
> <span data-ttu-id="a1d99-105">此类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="a1d99-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a1d99-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="a1d99-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="webpermissionunrestricted-field"></a><span data-ttu-id="a1d99-107">WebPermissionUnrestricted 字段</span><span class="sxs-lookup"><span data-stu-id="a1d99-107">WebPermissionUnrestricted field</span></span>

<span data-ttu-id="a1d99-108">指定应用程序可以连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="a1d99-108">Specifies that the app can connect to internet resources.</span></span>

```csharp
internal static readonly WebPermission WebPermissionUnrestricted
```

## <a name="requirements"></a><span data-ttu-id="a1d99-109">要求</span><span class="sxs-lookup"><span data-stu-id="a1d99-109">Requirements</span></span>

<span data-ttu-id="a1d99-110">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a1d99-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a1d99-111">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="a1d99-111">**Assembly:** System (in System.dll)</span></span>
