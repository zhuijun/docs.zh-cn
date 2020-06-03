---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720891"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a><span data-ttu-id="95d17-101">Linux 上的根证书不再支持“BEGIN TRUSTED CERTIFICATE”语法</span><span class="sxs-lookup"><span data-stu-id="95d17-101">"BEGIN TRUSTED CERTIFICATE" syntax no longer supported for root certificates on Linux</span></span>

<span data-ttu-id="95d17-102">Linux 和其他类似 Unix 的系统（但不是 macOS）上的根证书可以采用两种形式显示：标准 `BEGIN CERTIFICATE` PEM 标头和特定于 OpenSSL 的 `BEGIN TRUSTED CERTIFICATE` PEM 标头。</span><span class="sxs-lookup"><span data-stu-id="95d17-102">Root certificates on Linux and other Unix-like systems (but not macOS) can be presented in two forms: the standard `BEGIN CERTIFICATE` PEM header, and the OpenSSL-specific `BEGIN TRUSTED CERTIFICATE` PEM header.</span></span> <span data-ttu-id="95d17-103">后一种语法允许进行其他配置，这些配置已导致与 .NET Core 的 <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> 类之间的兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="95d17-103">The latter syntax allows for additional configuration that has caused compatibility issues with .NET Core's <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> class.</span></span> <span data-ttu-id="95d17-104">从 .NET Core 3.0 开始，链引擎不再加载 `BEGIN TRUSTED CERTIFICATE` 根证书内容。</span><span class="sxs-lookup"><span data-stu-id="95d17-104">`BEGIN TRUSTED CERTIFICATE` root certificate contents are no longer loaded by the chain engine starting in .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="95d17-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="95d17-105">Change description</span></span>

<span data-ttu-id="95d17-106">以前，`BEGIN CERTIFICATE` 和 `BEGIN TRUSTED CERTIFICATE` 语法均用于填充根信任列表。</span><span class="sxs-lookup"><span data-stu-id="95d17-106">Previously, both the `BEGIN CERTIFICATE` and `BEGIN TRUSTED CERTIFICATE` syntaxes were used to populate the root trust list.</span></span> <span data-ttu-id="95d17-107">如果使用了 `BEGIN TRUSTED CERTIFICATE` 语法，并且在文件中指定了其他选项，则 <xref:System.Security.Cryptography.X509Certificates.X509Chain> 可能报告已明确禁止链信任 (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="95d17-107">If the `BEGIN TRUSTED CERTIFICATE` syntax was used and additional options were specified in the file, <xref:System.Security.Cryptography.X509Certificates.X509Chain> may have reported that the chain trust was explicitly disallowed (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span></span> <span data-ttu-id="95d17-108">但是，如果在以前加载的文件中同时使用 `BEGIN CERTIFICATE` 语法指定了证书，则允许链信任。</span><span class="sxs-lookup"><span data-stu-id="95d17-108">However, if the certificate was also specified with the `BEGIN CERTIFICATE` syntax in a previously loaded file, the chain trust was allowed.</span></span>

<span data-ttu-id="95d17-109">从 .NET Core 3.0 开始，不再读取 `BEGIN TRUSTED CERTIFICATE` 内容。</span><span class="sxs-lookup"><span data-stu-id="95d17-109">Starting in .NET Core 3.0, `BEGIN TRUSTED CERTIFICATE` contents are no longer read.</span></span> <span data-ttu-id="95d17-110">如果还没有通过标准 `BEGIN CERTIFICATE` 语法指定证书，则 <xref:System.Security.Cryptography.X509Certificates.X509Chain> 会报告根不受信任 (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="95d17-110">If the certificate is not also specified via a standard `BEGIN CERTIFICATE` syntax, the <xref:System.Security.Cryptography.X509Certificates.X509Chain> reports that the root is not trusted (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="95d17-111">引入的版本</span><span class="sxs-lookup"><span data-stu-id="95d17-111">Version introduced</span></span>

<span data-ttu-id="95d17-112">3.0</span><span class="sxs-lookup"><span data-stu-id="95d17-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="95d17-113">建议操作</span><span class="sxs-lookup"><span data-stu-id="95d17-113">Recommended action</span></span>

<span data-ttu-id="95d17-114">大多数应用程序不受此更改的影响，但是由于权限问题而无法同时看到两个根证书源的应用程序可能会在升级后遇到意外的 `UntrustedRoot` 错误。</span><span class="sxs-lookup"><span data-stu-id="95d17-114">Most applications are unaffected by this change, but applications that cannot see both root certificate sources because of permissions problems may experience unexpected `UntrustedRoot` errors after upgrading.</span></span>

<span data-ttu-id="95d17-115">许多 Linux 分发版（或发行版）将根证书写入两个位置：每个文件一个证书目录和一个文件串联。</span><span class="sxs-lookup"><span data-stu-id="95d17-115">Many Linux distributions (or distros) write root certificates into two locations: a one-certificate-per-file directory, and a one-file concatenation.</span></span> <span data-ttu-id="95d17-116">在某些发行版上，每个文件一个证书目录使用 `BEGIN TRUSTED CERTIFICATE` 语法，而一个文件串联则使用标准 `BEGIN CERTIFICATE` 语法。</span><span class="sxs-lookup"><span data-stu-id="95d17-116">On some distros, the one-certificate-per-file directory uses the `BEGIN TRUSTED CERTIFICATE` syntax while the file concatenation uses the standard `BEGIN CERTIFICATE` syntax.</span></span> <span data-ttu-id="95d17-117">请确保将任何自定义根证书作为 `BEGIN CERTIFICATE` 添加到这些位置中的至少一个位置，并且你的应用程序可以读取这两个位置。</span><span class="sxs-lookup"><span data-stu-id="95d17-117">Ensure that any custom root certificates are added as `BEGIN CERTIFICATE` in at least one of these locations, and that both locations can be read by your application.</span></span>

<span data-ttu-id="95d17-118">典型的目录是 /etc/ssl/certs/ */* ，典型的串联文件是 /etc/ssl/cert.pem。</span><span class="sxs-lookup"><span data-stu-id="95d17-118">The typical directory is */etc/ssl/certs/* and the typical concatenated file is */etc/ssl/cert.pem*.</span></span> <span data-ttu-id="95d17-119">使用命令 `openssl version -d` 来确定特定于平台的根目录，这可能不同于 /etc/ssl/。</span><span class="sxs-lookup"><span data-stu-id="95d17-119">Use the command `openssl version -d` to determine the platform-specific root, which may differ from */etc/ssl/*.</span></span> <span data-ttu-id="95d17-120">例如，在 Ubuntu 18.04 上，目录是 /usr/lib/ssl/certs/，文件是 /usr/lib/ssl/cert.pem。</span><span class="sxs-lookup"><span data-stu-id="95d17-120">For example, on Ubuntu 18.04, the directory is */usr/lib/ssl/certs/* and the file is */usr/lib/ssl/cert.pem*.</span></span> <span data-ttu-id="95d17-121">不过，/usr/lib/ssl/certs/ 是 /etc/ssl/certs/ 的符号链接，并且 /usr/lib/ssl/cert.pem 不存在。</span><span class="sxs-lookup"><span data-stu-id="95d17-121">However, */usr/lib/ssl/certs/* is a symlink to */etc/ssl/certs/* and */usr/lib/ssl/cert.pem* does not exist.</span></span>

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

#### <a name="category"></a><span data-ttu-id="95d17-122">类别</span><span class="sxs-lookup"><span data-stu-id="95d17-122">Category</span></span>

<span data-ttu-id="95d17-123">密码</span><span class="sxs-lookup"><span data-stu-id="95d17-123">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="95d17-124">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="95d17-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
