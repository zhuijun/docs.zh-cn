---
title: 加密中断性变更
description: 列出 .NET Core 中与加密相关的中断性变更。
ms.date: 04/22/2020
ms.openlocfilehash: 621a3dad28b67ee33056dce3df0379efaeb90776
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065094"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="cb081-103">加密中断性变更</span><span class="sxs-lookup"><span data-stu-id="cb081-103">Cryptography breaking changes</span></span>

<span data-ttu-id="cb081-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="cb081-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="cb081-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="cb081-105">Breaking change</span></span> | <span data-ttu-id="cb081-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="cb081-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="cb081-107">System.Security.Cryptography.Oid 在功能上仅用于初始化</span><span class="sxs-lookup"><span data-stu-id="cb081-107">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="cb081-108">5.0</span><span class="sxs-lookup"><span data-stu-id="cb081-108">5.0</span></span> |
| [<span data-ttu-id="cb081-109">Linux 不再支持 BEGIN TRUSTED CERTIFICATE 语法</span><span class="sxs-lookup"><span data-stu-id="cb081-109">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="cb081-110">3.0</span><span class="sxs-lookup"><span data-stu-id="cb081-110">3.0</span></span> |
| [<span data-ttu-id="cb081-111">EnvelopedCms 默认为 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="cb081-111">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="cb081-112">3.0</span><span class="sxs-lookup"><span data-stu-id="cb081-112">3.0</span></span> |
| [<span data-ttu-id="cb081-113">RSAOpenSsl 密钥生成的最小大小已增加</span><span class="sxs-lookup"><span data-stu-id="cb081-113">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="cb081-114">3.0</span><span class="sxs-lookup"><span data-stu-id="cb081-114">3.0</span></span> |
| [<span data-ttu-id="cb081-115">.NET Core 3.0 倾向于使用 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="cb081-115">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="cb081-116">3.0</span><span class="sxs-lookup"><span data-stu-id="cb081-116">3.0</span></span> |
| [<span data-ttu-id="cb081-117">CryptoStream.Dispose 仅在写入时转换最终块</span><span class="sxs-lookup"><span data-stu-id="cb081-117">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="cb081-118">3.0</span><span class="sxs-lookup"><span data-stu-id="cb081-118">3.0</span></span> |
| [<span data-ttu-id="cb081-119">已考虑 SignedCms.ComputeSignature 的布尔参数</span><span class="sxs-lookup"><span data-stu-id="cb081-119">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="cb081-120">2.1</span><span class="sxs-lookup"><span data-stu-id="cb081-120">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="cb081-121">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="cb081-121">.NET 5.0</span></span>

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="cb081-122">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cb081-122">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="cb081-123">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cb081-123">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
