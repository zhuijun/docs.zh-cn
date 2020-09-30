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
# <a name="cryptography-breaking-changes"></a>加密中断性变更

本页记录了以下中断性变更：

| 重大更改 | 引入的版本 |
| - | :-: |
| [Blazor WebAssembly 不支持的 System.Security.Cryptography API](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | 5.0 |
| [System.Security.Cryptography.Oid 在功能上仅用于初始化](#systemsecuritycryptographyoid-is-functionally-init-only) | 5.0 |
| [Linux 不再支持 BEGIN TRUSTED CERTIFICATE 语法](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3.0 |
| [EnvelopedCms 默认为 AES-256 加密](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [RSAOpenSsl 密钥生成的最小大小已增加](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [.NET Core 3.0 倾向于使用 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [CryptoStream.Dispose 仅在写入时转换最终块](#cryptostreamdispose-transforms-final-block-only-when-writing) | 3.0 |
| [已考虑 SignedCms.ComputeSignature 的布尔参数](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
