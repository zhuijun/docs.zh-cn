---
title: 加密中断性变更
description: 列出 .NET Core 中与加密相关的中断性变更。
ms.date: 04/22/2020
ms.openlocfilehash: 667d983fc6f2592c2169f97d328cd7947c8bcc81
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406137"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="4cac3-103">加密中断性变更</span><span class="sxs-lookup"><span data-stu-id="4cac3-103">Cryptography breaking changes</span></span>

<span data-ttu-id="4cac3-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="4cac3-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4cac3-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="4cac3-105">Breaking change</span></span> | <span data-ttu-id="4cac3-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="4cac3-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="4cac3-107">Blazor WebAssembly 不支持的 System.Security.Cryptography API</span><span class="sxs-lookup"><span data-stu-id="4cac3-107">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="4cac3-108">5.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-108">5.0</span></span> |
| [<span data-ttu-id="4cac3-109">System.Security.Cryptography.Oid 在功能上仅用于初始化</span><span class="sxs-lookup"><span data-stu-id="4cac3-109">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="4cac3-110">5.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-110">5.0</span></span> |
| [<span data-ttu-id="4cac3-111">Linux 不再支持 BEGIN TRUSTED CERTIFICATE 语法</span><span class="sxs-lookup"><span data-stu-id="4cac3-111">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="4cac3-112">3.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-112">3.0</span></span> |
| [<span data-ttu-id="4cac3-113">EnvelopedCms 默认为 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="4cac3-113">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="4cac3-114">3.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-114">3.0</span></span> |
| [<span data-ttu-id="4cac3-115">RSAOpenSsl 密钥生成的最小大小已增加</span><span class="sxs-lookup"><span data-stu-id="4cac3-115">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="4cac3-116">3.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-116">3.0</span></span> |
| [<span data-ttu-id="4cac3-117">.NET Core 3.0 倾向于使用 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="4cac3-117">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="4cac3-118">3.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-118">3.0</span></span> |
| [<span data-ttu-id="4cac3-119">CryptoStream.Dispose 仅在写入时转换最终块</span><span class="sxs-lookup"><span data-stu-id="4cac3-119">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="4cac3-120">3.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-120">3.0</span></span> |
| [<span data-ttu-id="4cac3-121">已考虑 SignedCms.ComputeSignature 的布尔参数</span><span class="sxs-lookup"><span data-stu-id="4cac3-121">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="4cac3-122">2.1</span><span class="sxs-lookup"><span data-stu-id="4cac3-122">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="4cac3-123">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-123">.NET 5.0</span></span>

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="4cac3-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4cac3-124">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="4cac3-125">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4cac3-125">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
