---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615605"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a><span data-ttu-id="5c62b-101">通过 ClickOnce 使用 SHA-256 代码签名证书发布的应用在 Windows 2003 中可能会失败</span><span class="sxs-lookup"><span data-stu-id="5c62b-101">Apps published with ClickOnce that use a SHA-256 code-signing certificate may fail on Windows 2003</span></span>

#### <a name="details"></a><span data-ttu-id="5c62b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="5c62b-102">Details</span></span>

<span data-ttu-id="5c62b-103">使用 SHA256 对可执行文件签名。</span><span class="sxs-lookup"><span data-stu-id="5c62b-103">The executable is signed with SHA256.</span></span> <span data-ttu-id="5c62b-104">以前，无论代码签名证书是 SHA-1 还是 SHA-256，都使用 SHA1 进行签名。</span><span class="sxs-lookup"><span data-stu-id="5c62b-104">Previously, it was signed with SHA1 regardless of whether the code-signing certificate was SHA-1 or SHA-256.</span></span> <span data-ttu-id="5c62b-105">这适用于：</span><span class="sxs-lookup"><span data-stu-id="5c62b-105">This applies to:</span></span>

- <span data-ttu-id="5c62b-106">使用 Visual Studio 2012 或更高版本生成的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="5c62b-106">All applications built with Visual Studio 2012 or later.</span></span>
- <span data-ttu-id="5c62b-107">使用 Visual Studio 2010 或更早版本在安装了 .NET Framework 4.5 的系统上生成的应用程序。</span><span class="sxs-lookup"><span data-stu-id="5c62b-107">Applications built with Visual Studio 2010 or earlier on systems with the .NET Framework 4.5 present.</span></span>
<span data-ttu-id="5c62b-108">此外，如果安装了 .NET Framework 4.5 或更高版本，则 ClickOnce 清单也会采用 SHA-256 签名，因为 SHA-256 证书与编译所采用的 .NET Framework 版本无关。</span><span class="sxs-lookup"><span data-stu-id="5c62b-108">In addition, if the .NET Framework 4.5 or later is present, the ClickOnce manifest is also signed with SHA-256 for SHA-256 certificates regardless of the .NET Framework version against which it was compiled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5c62b-109">建议</span><span class="sxs-lookup"><span data-stu-id="5c62b-109">Suggestion</span></span>

<span data-ttu-id="5c62b-110">更改 ClickOnce 可执行文件的签名仅影响 Windows Server 2003 系统；它们需要安装 KB 938397。</span><span class="sxs-lookup"><span data-stu-id="5c62b-110">The change in signing the ClickOnce executable affects only Windows Server 2003 systems; they require that KB 938397 be installed.</span></span> <span data-ttu-id="5c62b-111">即使应用是面向 .NET Framework 4.0 或早期版本，对使用 SHA-256 签名的清单进行更改，将引入依赖 .NET Framework 4.5 或更高版本的运行时。</span><span class="sxs-lookup"><span data-stu-id="5c62b-111">The change in signing the manifest with SHA-256 even when an app targets the .NET Framework 4.0 or earlier versions introduces a runtime dependency on the .NET Framework 4.5 or a later version.</span></span>

| <span data-ttu-id="5c62b-112">“属性”</span><span class="sxs-lookup"><span data-stu-id="5c62b-112">Name</span></span>    | <span data-ttu-id="5c62b-113">“值”</span><span class="sxs-lookup"><span data-stu-id="5c62b-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5c62b-114">范围</span><span class="sxs-lookup"><span data-stu-id="5c62b-114">Scope</span></span>   | <span data-ttu-id="5c62b-115">边缘</span><span class="sxs-lookup"><span data-stu-id="5c62b-115">Edge</span></span>        |
| <span data-ttu-id="5c62b-116">Version</span><span class="sxs-lookup"><span data-stu-id="5c62b-116">Version</span></span> | <span data-ttu-id="5c62b-117">4.5</span><span class="sxs-lookup"><span data-stu-id="5c62b-117">4.5</span></span>         |
| <span data-ttu-id="5c62b-118">类型</span><span class="sxs-lookup"><span data-stu-id="5c62b-118">Type</span></span>    | <span data-ttu-id="5c62b-119">重定目标</span><span class="sxs-lookup"><span data-stu-id="5c62b-119">Retargeting</span></span> |
