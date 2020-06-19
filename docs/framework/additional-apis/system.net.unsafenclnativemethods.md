---
title: UnsafeNclNativeMethods 类（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990433"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="af6aa-102">UnsafeNclNativeMethods 类</span><span class="sxs-lookup"><span data-stu-id="af6aa-102">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="af6aa-103">包含导入不安全的本机网络方法的类。</span><span class="sxs-lookup"><span data-stu-id="af6aa-103">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="af6aa-104">无法继承此类。</span><span class="sxs-lookup"><span data-stu-id="af6aa-104">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="af6aa-105">此类是内部的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="af6aa-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="af6aa-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此类。</span><span class="sxs-lookup"><span data-stu-id="af6aa-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="af6aa-107">NativePKI 类</span><span class="sxs-lookup"><span data-stu-id="af6aa-107">NativePKI class</span></span>

<span data-ttu-id="af6aa-108">包含从 crypt32.dll 导入的方法。</span><span class="sxs-lookup"><span data-stu-id="af6aa-108">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="af6aa-109">使用超文本传输协议（HTTPS）时，这些方法会处理证书。</span><span class="sxs-lookup"><span data-stu-id="af6aa-109">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="af6aa-110">无法继承此类。</span><span class="sxs-lookup"><span data-stu-id="af6aa-110">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="af6aa-111">NativePKI. FindClientCertificates 方法</span><span class="sxs-lookup"><span data-stu-id="af6aa-111">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="af6aa-112">发现要发送到服务器的可用客户端证书。</span><span class="sxs-lookup"><span data-stu-id="af6aa-112">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="af6aa-113">返回值</span><span class="sxs-lookup"><span data-stu-id="af6aa-113">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="af6aa-114">可用客户端证书的集合。</span><span class="sxs-lookup"><span data-stu-id="af6aa-114">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="af6aa-115">要求</span><span class="sxs-lookup"><span data-stu-id="af6aa-115">Requirements</span></span>

<span data-ttu-id="af6aa-116">**命名空间：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="af6aa-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="af6aa-117">**程序集：** 系统（System.dll）</span><span class="sxs-lookup"><span data-stu-id="af6aa-117">**Assembly:** System (in System.dll)</span></span>
