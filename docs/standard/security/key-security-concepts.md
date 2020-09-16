---
title: 安全性的基础概念
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET]
- security [.NET], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
ms.openlocfilehash: 5dedf6df8e6cf2cf886e68cc132a44abfb201c49
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554392"
---
# <a name="key-security-concepts"></a><span data-ttu-id="fb101-102">安全性的基础概念</span><span class="sxs-lookup"><span data-stu-id="fb101-102">Key Security Concepts</span></span>

> [!NOTE]
> <span data-ttu-id="fb101-103">本文适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="fb101-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="fb101-104">有关 ASP.NET Core 的信息，请参阅 [ASP.NET Core 安全性概述](/aspnet/core/security/)。</span><span class="sxs-lookup"><span data-stu-id="fb101-104">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="fb101-105">.NET 提供基于角色的安全性，以帮助解决有关移动代码的安全性问题，并提供支持，使组件能够确定用户有权执行的操作。</span><span class="sxs-lookup"><span data-stu-id="fb101-105">.NET offers role-based security to help address security concerns about mobile code and to provide support that enables components to determine what users are authorized to do.</span></span>  
  
## <a name="type-safety-and-security"></a><span data-ttu-id="fb101-106">类型安全和安全性</span><span class="sxs-lookup"><span data-stu-id="fb101-106">Type safety and security</span></span>  

<span data-ttu-id="fb101-107">类型安全代码只访问其有权访问的内存位置。</span><span class="sxs-lookup"><span data-stu-id="fb101-107">Type-safe code accesses only the memory locations it is authorized to access.</span></span> <span data-ttu-id="fb101-108"> (此讨论，类型安全专门指内存类型安全，不应与更广泛的类型安全混淆。 ) 例如，类型安全代码无法从另一个对象的私有字段读取值。</span><span class="sxs-lookup"><span data-stu-id="fb101-108">(For this discussion, type safety specifically refers to memory type safety and should not be confused with type safety in a broader respect.) For example, type-safe code cannot read values from another object's private fields.</span></span> <span data-ttu-id="fb101-109">它仅以明确定义且经允许的方式访问类型。</span><span class="sxs-lookup"><span data-stu-id="fb101-109">It accesses types only in well-defined, allowable ways.</span></span>  
  
<span data-ttu-id="fb101-110">在实时 (JIT) 编译期间，一个可选的验证过程将检查方法（该方法将被实时编译为本机代码）的元数据和 Microsoft 中间语言 (MSIL)，以验证它们是否类型安全。</span><span class="sxs-lookup"><span data-stu-id="fb101-110">During just-in-time (JIT) compilation, an optional verification process examines the metadata and Microsoft intermediate language (MSIL) of a method to be JIT-compiled into native machine code to verify that they are type safe.</span></span> <span data-ttu-id="fb101-111">如果代码有权绕过验证，则将跳过此过程。</span><span class="sxs-lookup"><span data-stu-id="fb101-111">This process is skipped if the code has permission to bypass verification.</span></span> <span data-ttu-id="fb101-112">有关验证的详细信息，请参阅[托管执行过程](../managed-execution-process.md)。</span><span class="sxs-lookup"><span data-stu-id="fb101-112">For more information about verification, see [Managed Execution Process](../managed-execution-process.md).</span></span>  
  
<span data-ttu-id="fb101-113">虽然类型安全验证并不强制性要求运行托管代码，但类型安全在程序集隔离和安全性强制中扮演着重要角色。</span><span class="sxs-lookup"><span data-stu-id="fb101-113">Although verification of type safety is not mandatory to run managed code, type safety plays a crucial role in assembly isolation and security enforcement.</span></span> <span data-ttu-id="fb101-114">代码类型安全时，公共语言运行时可以将程序集彼此完全隔离。</span><span class="sxs-lookup"><span data-stu-id="fb101-114">When code is type safe, the common language runtime can completely isolate assemblies from each other.</span></span> <span data-ttu-id="fb101-115">这种隔离可帮助确保程序集不能对彼此产生负面影响，同时可增加应用程序的可靠性。</span><span class="sxs-lookup"><span data-stu-id="fb101-115">This isolation helps ensure that assemblies cannot adversely affect each other and it increases application reliability.</span></span> <span data-ttu-id="fb101-116">类型安全组件可在相同进程中安全地执行，即使它们的信任级别不同。</span><span class="sxs-lookup"><span data-stu-id="fb101-116">Type-safe components can execute safely in the same process even if they are trusted at different levels.</span></span> <span data-ttu-id="fb101-117">代码不是类型安全的代码时，可能会产生意外的副作用。</span><span class="sxs-lookup"><span data-stu-id="fb101-117">When code is not type safe, unwanted side effects can occur.</span></span> <span data-ttu-id="fb101-118">例如，运行时无法阻止托管代码调用到本机（非托管）代码中和执行恶意操作。</span><span class="sxs-lookup"><span data-stu-id="fb101-118">For example, the runtime cannot prevent managed code from calling into native (unmanaged) code and performing malicious operations.</span></span> <span data-ttu-id="fb101-119">代码是类型安全的代码时，运行时的安全强制机制可确保它不会访问本机代码，除非它有权这么做。</span><span class="sxs-lookup"><span data-stu-id="fb101-119">When code is type safe, the runtime's security enforcement mechanism ensures that it does not access native code unless it has permission to do so.</span></span> <span data-ttu-id="fb101-120">非类型安全的所有代码都必须被授予 <xref:System.Security.Permissions.SecurityPermission> 和传递的枚举成员 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>才能运行。</span><span class="sxs-lookup"><span data-stu-id="fb101-120">All code that is not type safe must have been granted <xref:System.Security.Permissions.SecurityPermission> with the passed enum member <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> to run.</span></span>  
  
<span data-ttu-id="fb101-121">有关详细信息，请参阅 [Code Access Security Basics](../../framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="fb101-121">For more information, see [Code Access Security Basics](../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="principal"></a><span data-ttu-id="fb101-122">主体</span><span class="sxs-lookup"><span data-stu-id="fb101-122">Principal</span></span>  

<span data-ttu-id="fb101-123">主体表示用户的标识和角色，并代表用户进行操作。</span><span class="sxs-lookup"><span data-stu-id="fb101-123">A principal represents the identity and role of a user and acts on the user's behalf.</span></span> <span data-ttu-id="fb101-124">.NET 中基于角色的安全性支持三种主体：</span><span class="sxs-lookup"><span data-stu-id="fb101-124">Role-based security in .NET supports three kinds of principals:</span></span>  
  
- <span data-ttu-id="fb101-125">泛型主体表示独立于 Windows 用户和角色存在的用户和角色。</span><span class="sxs-lookup"><span data-stu-id="fb101-125">Generic principals represent users and roles that exist independent of Windows users and roles.</span></span>  
  
- <span data-ttu-id="fb101-126">Windows 主体表示 Windows 用户及其角色（或其 Windows 组）。</span><span class="sxs-lookup"><span data-stu-id="fb101-126">Windows principals represent Windows users and their roles (or their Windows groups).</span></span> <span data-ttu-id="fb101-127">Windows 主体可以模拟其他用户，这意味着当代表属于一个用户的标识时，主体可代表该用户访问资源。</span><span class="sxs-lookup"><span data-stu-id="fb101-127">A Windows principal can impersonate another user, which means that the principal can access a resource on a user's behalf while presenting the identity that belongs to that user.</span></span>  
  
- <span data-ttu-id="fb101-128">应用程序可以用任何所需的方式自定义主体。</span><span class="sxs-lookup"><span data-stu-id="fb101-128">Custom principals can be defined by an application in any way that is needed for that particular application.</span></span> <span data-ttu-id="fb101-129">它们可以扩展该主体的标识和角色的基本概念。</span><span class="sxs-lookup"><span data-stu-id="fb101-129">They can extend the basic notion of the principal's identity and roles.</span></span>  
  
<span data-ttu-id="fb101-130">有关详细信息，请参阅[主体和标识对象](principal-and-identity-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="fb101-130">For more information, see [Principal and Identity Objects](principal-and-identity-objects.md).</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="fb101-131">身份验证</span><span class="sxs-lookup"><span data-stu-id="fb101-131">Authentication</span></span>  
<span data-ttu-id="fb101-132">身份验证是通过检查用户凭据和针对某些颁发机构对这些凭据进行验证来发现和验证主体的标识的过程。</span><span class="sxs-lookup"><span data-stu-id="fb101-132">Authentication is the process of discovering and verifying the identity of a principal by examining the user's credentials and validating those credentials against some authority.</span></span> <span data-ttu-id="fb101-133">身份验证期间获取的信息可直接为你的代码所用。</span><span class="sxs-lookup"><span data-stu-id="fb101-133">The information obtained during authentication is directly usable by your code.</span></span> <span data-ttu-id="fb101-134">还可以使用基于 .NET 角色的安全性对当前用户进行身份验证并确定是否允许该主体访问代码。</span><span class="sxs-lookup"><span data-stu-id="fb101-134">You can also use .NET role-based security to authenticate the current user and to determine whether to allow that principal to access your code.</span></span> <span data-ttu-id="fb101-135">请参阅 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> 方法的重载，了解有关如何对特定角色的主体进行身份验证的示例。</span><span class="sxs-lookup"><span data-stu-id="fb101-135">See the overloads of the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> method for examples of how to authenticate the principal for specific roles.</span></span> <span data-ttu-id="fb101-136">例如，可以使用 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> 重载确定当前用户是否是“Administrators”组的成员。</span><span class="sxs-lookup"><span data-stu-id="fb101-136">For example, you can use the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> overload to determine if the current user is a member of the Administrators group.</span></span>  
  
<span data-ttu-id="fb101-137">目前使用多种身份验证机制，其中的许多机制可用于基于 .NET 角色的安全性。</span><span class="sxs-lookup"><span data-stu-id="fb101-137">A variety of authentication mechanisms are used today, many of which can be used with .NET role-based security.</span></span> <span data-ttu-id="fb101-138">最常用的一些机制包括 basic、digest、Passport、操作系统（例如，NTLM 或 Kerberos）或应用程序定义的机制。</span><span class="sxs-lookup"><span data-stu-id="fb101-138">Some of the most commonly used mechanisms are basic, digest, Passport, operating system (such as NTLM or Kerberos), or application-defined mechanisms.</span></span>  
  
### <a name="example"></a><span data-ttu-id="fb101-139">示例</span><span class="sxs-lookup"><span data-stu-id="fb101-139">Example</span></span>  

<span data-ttu-id="fb101-140">下面的示例要求活动主体是管理员。</span><span class="sxs-lookup"><span data-stu-id="fb101-140">The following example requires that the active principal be an administrator.</span></span> <span data-ttu-id="fb101-141">`name` 参数为 `null`，这使任何身份为管理员的用户均满足该要求。</span><span class="sxs-lookup"><span data-stu-id="fb101-141">The `name` parameter is `null`, which allows any user who is an administrator to pass the demand.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb101-142">在 Windows Vista 中，用户帐户控制 (UAC) 决定用户的特权。</span><span class="sxs-lookup"><span data-stu-id="fb101-142">In Windows Vista, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="fb101-143">如果您是内置的 Administrators 组的成员，将为您分配两个运行时访问令牌：一个标准用户访问令牌和一个管理员访问令牌。</span><span class="sxs-lookup"><span data-stu-id="fb101-143">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="fb101-144">默认情况下，您拥有标准用户角色。</span><span class="sxs-lookup"><span data-stu-id="fb101-144">By default, you are in the standard user role.</span></span> <span data-ttu-id="fb101-145">要执行需要管理员身份的代码，必须首先将你的特权从标准用户提升至管理员。</span><span class="sxs-lookup"><span data-stu-id="fb101-145">To execute the code that requires you to be an administrator, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="fb101-146">你可以通过以下方式执行此操作：右键单击应用程序图标并指示需以管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="fb101-146">You can do this when you start an application by right-clicking the application icon and indicating that you want to run as an administrator.</span></span>  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 <span data-ttu-id="fb101-147">下面的示例演示如何确定主体的标识和该主体可用的角色。</span><span class="sxs-lookup"><span data-stu-id="fb101-147">The following example demonstrates how to determine the identity of the principal and the roles available to the principal.</span></span> <span data-ttu-id="fb101-148">该示例的应用可能是：确认当前用户为你允许使用你的应用程序的角色。</span><span class="sxs-lookup"><span data-stu-id="fb101-148">An application of this example might be to confirm that the current user is in a role you allow for using your application.</span></span>  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a><span data-ttu-id="fb101-149">授权</span><span class="sxs-lookup"><span data-stu-id="fb101-149">Authorization</span></span>  

<span data-ttu-id="fb101-150">授权是确定是否同意主体执行所请求的操作的过程。</span><span class="sxs-lookup"><span data-stu-id="fb101-150">Authorization is the process of determining whether a principal is allowed to perform a requested action.</span></span> <span data-ttu-id="fb101-151">授权发生在身份验证之后，并使用有关主体的标识和角色的信息来确定主体可以访问的资源。</span><span class="sxs-lookup"><span data-stu-id="fb101-151">Authorization occurs after authentication and uses information about the principal's identity and roles to determine what resources the principal can access.</span></span> <span data-ttu-id="fb101-152">您可以使用基于 .NET 角色的安全性实现授权。</span><span class="sxs-lookup"><span data-stu-id="fb101-152">You can use .NET role-based security to implement authorization.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb101-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="fb101-153">See also</span></span>

- [<span data-ttu-id="fb101-154">ASP.NET Core 安全性</span><span class="sxs-lookup"><span data-stu-id="fb101-154">ASP.NET Core Security</span></span>](/aspnet/core/security/)
