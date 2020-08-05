---
title: 安全性和进行中的代码生成
description: 对于以较高信任级别运行的代码，以较高信任级别运行代码，这是一个安全问题，尤其是当调用方可以影响代码生成时。
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: a3fc51c346feffa85537d95ccdbd23d943827edf
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555690"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="de9e5-103">安全性和进行中的代码生成</span><span class="sxs-lookup"><span data-stu-id="de9e5-103">Security and On-the-Fly Code Generation</span></span>

<span data-ttu-id="de9e5-104">某些库的操作方式是通过生成代码并运行它执行调用方的某项操作。</span><span class="sxs-lookup"><span data-stu-id="de9e5-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="de9e5-105">基本问题是代表信任级别较低的代码生成代码，并在更高的信任级别运行它。</span><span class="sxs-lookup"><span data-stu-id="de9e5-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="de9e5-106">当调用方可影响代码生成时，问题更为恶化，因此必须确保仅生成认为安全的代码。</span><span class="sxs-lookup"><span data-stu-id="de9e5-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
<span data-ttu-id="de9e5-107">需要随时了解正在生成的具体代码。</span><span class="sxs-lookup"><span data-stu-id="de9e5-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="de9e5-108">这意味着必须严格控制从用户获取的任何值，无论它们是带引号的字符串（应转义以便不包含意外代码元素）、标识符（应检查以验证是否为有效标识符）或任何其他内容。</span><span class="sxs-lookup"><span data-stu-id="de9e5-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="de9e5-109">标识符可能很危险，因为可能修改已编译的程序集，使其标识符包含可能损程序集的奇怪字符（尽管此类安全漏洞很少见）。</span><span class="sxs-lookup"><span data-stu-id="de9e5-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
<span data-ttu-id="de9e5-110">建议用反射发出生成代码，这通常有助于避免很多此类问题。</span><span class="sxs-lookup"><span data-stu-id="de9e5-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
<span data-ttu-id="de9e5-111">编译代码时，请注意恶意程序是否可以某种方式修改它。</span><span class="sxs-lookup"><span data-stu-id="de9e5-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="de9e5-112">在编译器读取磁盘上的源代码或代码加载 .dll 文件之前，是否存在一小段时间窗口使恶意代码可在此期间修改此源代码？</span><span class="sxs-lookup"><span data-stu-id="de9e5-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="de9e5-113">若如此，必须适当使用文件系统中的访问控制列表保护包含这些文件的目录。</span><span class="sxs-lookup"><span data-stu-id="de9e5-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9e5-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="de9e5-114">See also</span></span>

- [<span data-ttu-id="de9e5-115">代码安全维护指南</span><span class="sxs-lookup"><span data-stu-id="de9e5-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="de9e5-116">ASP.NET Core 安全性</span><span class="sxs-lookup"><span data-stu-id="de9e5-116">ASP.NET Core Security</span></span>](/aspnet/core/security/)
