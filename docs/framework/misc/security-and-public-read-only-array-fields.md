---
title: 安全和公共只读数组字段
description: 请阅读为什么应避免使用公共只读数组字段来定义应用程序的边界行为或安全性。
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 5e499f8052306cd1ad063c9f44a2a0f1d0b365ef
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855733"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="339b3-103">安全和公共只读数组字段</span><span class="sxs-lookup"><span data-stu-id="339b3-103">Security and Public Read-only Array Fields</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="339b3-104">永远不要使用托管库中的只读公共数组字段来定义应用程序的边界行为或安全性，因为可以修改只读公共数组字段。</span><span class="sxs-lookup"><span data-stu-id="339b3-104">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="339b3-105">备注</span><span class="sxs-lookup"><span data-stu-id="339b3-105">Remarks</span></span>  

<span data-ttu-id="339b3-106">某些 .NET 类包含包含特定于平台的边界参数的只读公共字段。</span><span class="sxs-lookup"><span data-stu-id="339b3-106">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="339b3-107">例如， <xref:System.IO.Path.InvalidPathChars> 字段是描述文件路径字符串中不允许使用的字符的数组。</span><span class="sxs-lookup"><span data-stu-id="339b3-107">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="339b3-108">许多类似的字段在 .NET 中都存在。</span><span class="sxs-lookup"><span data-stu-id="339b3-108">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="339b3-109">类似公共只读字段的值 <xref:System.IO.Path.InvalidPathChars> 可以通过代码或共享代码应用程序域的代码进行修改。</span><span class="sxs-lookup"><span data-stu-id="339b3-109">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="339b3-110">不应使用类似于这样的只读公共数组字段来定义应用程序的边界行为。</span><span class="sxs-lookup"><span data-stu-id="339b3-110">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="339b3-111">如果这样做，恶意代码可以更改边界定义，并以意外的方式使用您的代码。</span><span class="sxs-lookup"><span data-stu-id="339b3-111">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="339b3-112">在 .NET Framework 版本2.0 及更高版本中，应使用返回新数组的方法，而不是使用公共数组字段。</span><span class="sxs-lookup"><span data-stu-id="339b3-112">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="339b3-113">例如，应使用方法，而不是使用 <xref:System.IO.Path.InvalidPathChars> 字段 <xref:System.IO.Path.GetInvalidPathChars%2A> 。</span><span class="sxs-lookup"><span data-stu-id="339b3-113">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="339b3-114">请注意，.NET Framework 类型不使用公共字段在内部定义边界类型。</span><span class="sxs-lookup"><span data-stu-id="339b3-114">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="339b3-115">相反，.NET Framework 使用单独的私有字段。</span><span class="sxs-lookup"><span data-stu-id="339b3-115">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="339b3-116">更改这些公共字段的值不会改变 .NET Framework 类型的行为。</span><span class="sxs-lookup"><span data-stu-id="339b3-116">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339b3-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="339b3-117">See also</span></span>

- [<span data-ttu-id="339b3-118">安全编码准则</span><span class="sxs-lookup"><span data-stu-id="339b3-118">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
