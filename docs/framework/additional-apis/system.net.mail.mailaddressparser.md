---
title: MailAddressParser 类（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990441"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="0c162-102">MailAddressParser 类</span><span class="sxs-lookup"><span data-stu-id="0c162-102">MailAddressParser class</span></span>

<span data-ttu-id="0c162-103">如 RFC 2822 中所述分析电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="0c162-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="0c162-104">无法继承此类。</span><span class="sxs-lookup"><span data-stu-id="0c162-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="0c162-105">此类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="0c162-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0c162-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="0c162-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="0c162-107">ParseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="0c162-107">ParseAddress method</span></span>

<span data-ttu-id="0c162-108">分析指定字符串中的单个电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="0c162-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="0c162-109">参数</span><span class="sxs-lookup"><span data-stu-id="0c162-109">Parameters</span></span>

<span data-ttu-id="0c162-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0c162-110">`data` <xref:System.String></span></span>

<span data-ttu-id="0c162-111">包含要分析的电子邮件地址的字符串。</span><span class="sxs-lookup"><span data-stu-id="0c162-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="0c162-112">返回值</span><span class="sxs-lookup"><span data-stu-id="0c162-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="0c162-113">有效的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="0c162-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="0c162-114">例外</span><span class="sxs-lookup"><span data-stu-id="0c162-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="0c162-115">电子邮件地址无效。</span><span class="sxs-lookup"><span data-stu-id="0c162-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c162-116">要求</span><span class="sxs-lookup"><span data-stu-id="0c162-116">Requirements</span></span>

<span data-ttu-id="0c162-117">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0c162-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0c162-118">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="0c162-118">**Assembly:** System (in System.dll)</span></span>
