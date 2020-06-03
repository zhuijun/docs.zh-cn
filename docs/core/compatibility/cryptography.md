---
title: 加密中断性变更
description: 列出 .NET Core 中与加密相关的中断性变更。
ms.date: 04/22/2020
ms.openlocfilehash: 66049473083d87b4c84408f35a04193a4563c2b3
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135591"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="eeeef-103">加密中断性变更</span><span class="sxs-lookup"><span data-stu-id="eeeef-103">Cryptography breaking changes</span></span>

<span data-ttu-id="eeeef-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="eeeef-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="eeeef-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="eeeef-105">Breaking change</span></span> | <span data-ttu-id="eeeef-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="eeeef-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="eeeef-107">Linux 不再支持 BEGIN TRUSTED CERTIFICATE 语法</span><span class="sxs-lookup"><span data-stu-id="eeeef-107">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="eeeef-108">3.0</span><span class="sxs-lookup"><span data-stu-id="eeeef-108">3.0</span></span> |
| [<span data-ttu-id="eeeef-109">EnvelopedCms 默认为 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="eeeef-109">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="eeeef-110">3.0</span><span class="sxs-lookup"><span data-stu-id="eeeef-110">3.0</span></span> |
| [<span data-ttu-id="eeeef-111">RSAOpenSsl 密钥生成的最小大小已增加</span><span class="sxs-lookup"><span data-stu-id="eeeef-111">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="eeeef-112">3.0</span><span class="sxs-lookup"><span data-stu-id="eeeef-112">3.0</span></span> |
| [<span data-ttu-id="eeeef-113">.NET Core 3.0 倾向于使用 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="eeeef-113">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="eeeef-114">3.0</span><span class="sxs-lookup"><span data-stu-id="eeeef-114">3.0</span></span> |
| [<span data-ttu-id="eeeef-115">Pkcs8PrivateKeyInfo 构造函数中更好的参数验证</span><span class="sxs-lookup"><span data-stu-id="eeeef-115">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="eeeef-116">3.0</span><span class="sxs-lookup"><span data-stu-id="eeeef-116">3.0</span></span> |
| [<span data-ttu-id="eeeef-117">已考虑 SignedCms.ComputeSignature 的布尔参数</span><span class="sxs-lookup"><span data-stu-id="eeeef-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="eeeef-118">2.1</span><span class="sxs-lookup"><span data-stu-id="eeeef-118">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="eeeef-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="eeeef-119">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="eeeef-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eeeef-120">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
