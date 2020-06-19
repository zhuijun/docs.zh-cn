---
title: ComNetOS 类（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990456"
---
# <a name="comnetos-class"></a><span data-ttu-id="10086-102">ComNetOS 类</span><span class="sxs-lookup"><span data-stu-id="10086-102">ComNetOS class</span></span>

<span data-ttu-id="10086-103">提供有关当前操作系统的信息，如其版本和安装类型（客户端或服务器）。</span><span class="sxs-lookup"><span data-stu-id="10086-103">Provides information about the current operating system, such as its version and installation type (client or server).</span></span> <span data-ttu-id="10086-104">无法继承此类。</span><span class="sxs-lookup"><span data-stu-id="10086-104">This class cannot be inherited.</span></span>
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> <span data-ttu-id="10086-105">此类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="10086-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="10086-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="10086-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="iswin7orlater-field"></a><span data-ttu-id="10086-107">IsWin7orLater 字段</span><span class="sxs-lookup"><span data-stu-id="10086-107">IsWin7orLater field</span></span>

<span data-ttu-id="10086-108">指定操作系统版本是否为 Windows 7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="10086-108">Specifies whether the operating system version is Windows 7 or later.</span></span>

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a><span data-ttu-id="10086-109">要求</span><span class="sxs-lookup"><span data-stu-id="10086-109">Requirements</span></span>

<span data-ttu-id="10086-110">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="10086-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="10086-111">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="10086-111">**Assembly:** System (in System.dll)</span></span>
