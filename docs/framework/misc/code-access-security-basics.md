---
title: 代码访问安全性基础知识
description: 了解面向 CLR 的应用程序的代码访问安全性基础知识：类型安全代码、命令性语法、声明性语法、安全类库和透明代码。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
ms.openlocfilehash: 9f6049913a2e8cf3e3f220b0148598a236b60bef
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557066"
---
# <a name="code-access-security-basics"></a><span data-ttu-id="e7a2a-103">代码访问安全性基础知识</span><span class="sxs-lookup"><span data-stu-id="e7a2a-103">Code Access Security Basics</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="e7a2a-104">每个面向公共语言运行时的应用程序（即每个托管应用程序）必须与运行时的安全系统进行交互。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-104">Every application that targets the common language runtime (that is, every managed application) must interact with the runtime's security system.</span></span> <span data-ttu-id="e7a2a-105">加载托管应用程序时，其主机会自动授予它一组权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-105">When a managed application is loaded, its host automatically grants it a set of permissions.</span></span> <span data-ttu-id="e7a2a-106">这些权限由主机的本地安全设置或应用程序所在的沙盒决定。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-106">These permissions are determined by the host's local security settings or by the sandbox the application is in.</span></span> <span data-ttu-id="e7a2a-107">根据这些权限，应用程序会正确运行，或者生成安全异常。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-107">Depending on these permissions, the application either runs properly or generates a security exception.</span></span>

<span data-ttu-id="e7a2a-108">桌面应用程序的默认主机允许代码在完全信任环境中运行。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-108">The default host for desktop applications allows code to run in full trust.</span></span> <span data-ttu-id="e7a2a-109">因此，如果应用程序面向桌面，它就具有不受限制的权限集。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-109">Therefore, if your application targets the desktop, it has an unrestricted permission set.</span></span> <span data-ttu-id="e7a2a-110">其他主机或沙盒会为应用程序提供受限制的权限集。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-110">Other hosts or sandboxes provide a limited permission set for applications.</span></span> <span data-ttu-id="e7a2a-111">由于主机的权限集各不相同，所以必须将应用程序设计为仅使用目标主机允许的权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-111">Because the permission set can change from host to host, you must design your application to use only the permissions that your target host allows.</span></span>

<span data-ttu-id="e7a2a-112">你必须熟悉下列代码访问安全性概念才能编写面向公共语言运行时的有效应用程序：</span><span class="sxs-lookup"><span data-stu-id="e7a2a-112">You must be familiar with the following code access security concepts in order to write effective applications that target the common language runtime:</span></span>

- <span data-ttu-id="e7a2a-113">**类型安全代码**：类型安全代码是仅以定义完善的允许方法访问类型的代码。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-113">**Type-safe code**: Type-safe code is code that accesses types only in well-defined, allowable ways.</span></span> <span data-ttu-id="e7a2a-114">例如，给定有效的对象引用，类型安全代码能以与实际字段成员相应的固定偏移量访问内存。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-114">For example, given a valid object reference, type-safe code can access memory at fixed offsets that correspond to actual field members.</span></span> <span data-ttu-id="e7a2a-115">如果代码以超出内存（内存属于该对象的公共公开字段）范围的任意偏移量访问内存，则它不是类型安全的。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-115">If the code accesses memory at arbitrary offsets outside the range of memory that belongs to that object's publicly exposed fields, it is not type-safe.</span></span> <span data-ttu-id="e7a2a-116">若要使代码能够受益于代码访问安全性，必须使用生成可验证类型安全代码的编译器。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-116">To enable code to benefit from code access security, you must use a compiler that generates verifiably type-safe code.</span></span> <span data-ttu-id="e7a2a-117">有关详细信息，请参阅本主题后面的 [编写验证的类型安全代码](#typesafe_code) 部分。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-117">For more information, see the [Writing Verifiably Type-Safe Code](#typesafe_code) section later in this topic.</span></span>

- <span data-ttu-id="e7a2a-118">**命令性和声明性语法**：以公共语言运行时为目标的代码可以通过以下方法与安全系统进行交互：请求权限、要求调用方具有指定的权限，并覆盖 (给定足够权限) 的某些安全设置。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-118">**Imperative and declarative syntax**: Code that targets the common language runtime can interact with the security system by requesting permissions, demanding that callers have specified permissions, and overriding certain security settings (given enough privileges).</span></span> <span data-ttu-id="e7a2a-119">可使用两种形式的语法以编程方式与 .NET Framework 安全系统进行交互：声明性语法和命令性语法。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-119">You use two forms of syntax to programmatically interact with the .NET Framework security system: declarative syntax and imperative syntax.</span></span> <span data-ttu-id="e7a2a-120">声明性调用通过使用属性来执行；命令性调用通过使用代码中类的新实例来执行。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-120">Declarative calls are performed using attributes; imperative calls are performed using new instances of classes within your code.</span></span> <span data-ttu-id="e7a2a-121">一些调用只能以命令方式执行，其他调用仅能以声明方式执行，还有一些调用能以任一种方式执行。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-121">Some calls can be performed only imperatively, others can be performed only declaratively, and some calls can be performed in either manner.</span></span>

- <span data-ttu-id="e7a2a-122">**安全类库**：安全类库使用安全要求确保库的调用方有权访问库公开的资源。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-122">**Secure class libraries**: A secure class library uses security demands to ensure that the library's callers have permission to access the resources that the library exposes.</span></span> <span data-ttu-id="e7a2a-123">例如，安全类库可能具有一种方法，可用于创建一种文件，这种文件要求其调用方具有创建文件的权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-123">For example, a secure class library might have a method for creating files that would demand that its callers have permissions to create files.</span></span> <span data-ttu-id="e7a2a-124">.NET Framework 由安全类库组成。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-124">The .NET Framework consists of secure class libraries.</span></span> <span data-ttu-id="e7a2a-125">你应了解访问你的代码所使用的任何库所需的权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-125">You should be aware of the permissions required to access any library that your code uses.</span></span> <span data-ttu-id="e7a2a-126">有关详细信息，请参阅本主题后面的 [使用安全类库](#secure_library) 部分。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-126">For more information, see the [Using Secure Class Libraries](#secure_library) section later in this topic.</span></span>

- <span data-ttu-id="e7a2a-127">**透明代码**：除了标识特定权限以外，还必须确定代码是否应作为安全透明运行，从 .NET Framework 4 开始。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-127">**Transparent code**: Starting with the .NET Framework 4, in addition to identifying specific permissions, you must also determine whether your code should run as security-transparent.</span></span> <span data-ttu-id="e7a2a-128">安全透明代码不能调用标识为安全关键的类型或成员。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-128">Security-transparent code cannot call types or members that are identified as security-critical.</span></span> <span data-ttu-id="e7a2a-129">此规则适用于完全信任的应用程序以及部分受信任的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-129">This rule applies to full-trust applications as well as partially trusted applications.</span></span> <span data-ttu-id="e7a2a-130">有关详细信息，请参阅 [安全透明代码](security-transparent-code.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-130">For more information, see [Security-Transparent Code](security-transparent-code.md).</span></span>

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a><span data-ttu-id="e7a2a-131">编写可验证类型安全代码</span><span class="sxs-lookup"><span data-stu-id="e7a2a-131">Writing Verifiably Type-Safe Code</span></span>

<span data-ttu-id="e7a2a-132">实时 (JIT) 编译会执行一个验证过程以检查代码并尝试确定代码是否为类型安全的。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-132">Just-in-time (JIT) compilation performs a verification process that examines code and tries to determine whether the code is type-safe.</span></span> <span data-ttu-id="e7a2a-133">在验证过程中验证为类型安全的代码称为可 *验证的类型安全代码*。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-133">Code that is proven during verification to be type-safe is called *verifiably type-safe code*.</span></span> <span data-ttu-id="e7a2a-134">代码可以是类型安全的，但由于验证过程或编译器的限制，代码可能不是可验证类型安全的。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-134">Code can be type-safe, yet might not be verifiably type-safe because of the limitations of the verification process or of the compiler.</span></span> <span data-ttu-id="e7a2a-135">并非所有语言都是类型安全的，而且一些语言编译器（如 Microsoft Visual c + +）无法生成可验证类型安全托管代码。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-135">Not all languages are type-safe, and some language compilers, such as Microsoft Visual C++, cannot generate verifiably type-safe managed code.</span></span> <span data-ttu-id="e7a2a-136">若要确定你使用的语言编译器是否生成可验证类型安全代码，请参阅编译器的文档。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-136">To determine whether the language compiler you use generates verifiably type-safe code, consult the compiler's documentation.</span></span> <span data-ttu-id="e7a2a-137">如果你使用的语言编译器仅在你避免使用某些语言构造时才生成可验证的类型安全代码，则你可能需要使用 [peverify.exe 工具](../tools/peverify-exe-peverify-tool.md) 来确定你的代码是否可验证类型安全。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-137">If you use a language compiler that generates verifiably type-safe code only when you avoid certain language constructs, you might want to use the [PEVerify tool](../tools/peverify-exe-peverify-tool.md) to determine whether your code is verifiably type-safe.</span></span>

<span data-ttu-id="e7a2a-138">如果安全策略允许代码跳过验证，不是可验证类型安全的代码也可以尝试执行。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-138">Code that is not verifiably type-safe can attempt to execute if security policy allows the code to bypass verification.</span></span> <span data-ttu-id="e7a2a-139">但是，由于类型安全是运行时机制隔离程序集必不可少的组成部分，如果代码违反类型安全的规则，就不能可靠地强制实施安全性。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-139">However, because type safety is an essential part of the runtime's mechanism for isolating assemblies, security cannot be reliably enforced if code violates the rules of type safety.</span></span> <span data-ttu-id="e7a2a-140">默认情况下，仅当非类型安全的代码来自本地计算机时才允许它运行。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-140">By default, code that is not type-safe is allowed to run only if it originates from the local computer.</span></span> <span data-ttu-id="e7a2a-141">因此，移动代码应是类型安全的。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-141">Therefore, mobile code should be type-safe.</span></span>

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a><span data-ttu-id="e7a2a-142">使用安全类库</span><span class="sxs-lookup"><span data-stu-id="e7a2a-142">Using Secure Class Libraries</span></span>

<span data-ttu-id="e7a2a-143">如果你的代码进行请求并被授予类库所需的权限，将允许它访问该库，同时保护该库公开的资源不受未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-143">If your code requests and is granted the permissions required by the class library, it will be allowed to access the library and the resources that the library exposes will be protected from unauthorized access.</span></span> <span data-ttu-id="e7a2a-144">如果你的代码不具有适当的权限，将不允许它访问类库，恶意代码将无法使用你的代码间接访问受保护的资源。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-144">If your code does not have the appropriate permissions, it will not be allowed to access the class library, and malicious code will not be able to use your code to indirectly access protected resources.</span></span> <span data-ttu-id="e7a2a-145">其他调用你代码的代码也必须具有访问该库的权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-145">Other code that calls your code must also have permission to access the library.</span></span> <span data-ttu-id="e7a2a-146">如果它不具有权限，则你的代码也将被限制运行。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-146">If it does not, your code will be restricted from running as well.</span></span>

<span data-ttu-id="e7a2a-147">代码访问安全性不会消除编写代码时产生人为错误的可能性。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-147">Code access security does not eliminate the possibility of human error in writing code.</span></span> <span data-ttu-id="e7a2a-148">但是，如果你的应用程序使用安全类库访问受保护的资源，应用程序代码的安全风险会降低，因为类库会受到仔细审查以排除潜在的安全问题。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-148">However, if your application uses secure class libraries to access protected resources, the security risk for application code is decreased, because class libraries are closely scrutinized for potential security problems.</span></span>

## <a name="declarative-security"></a><span data-ttu-id="e7a2a-149">声明性安全</span><span class="sxs-lookup"><span data-stu-id="e7a2a-149">Declarative Security</span></span>

<span data-ttu-id="e7a2a-150">声明性安全语法使用 [特性](../../standard/attributes/index.md) 将安全信息放置到代码的 [元数据](../../standard/metadata-and-self-describing-components.md) 中。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-150">Declarative security syntax uses [attributes](../../standard/attributes/index.md) to place security information into the [metadata](../../standard/metadata-and-self-describing-components.md) of your code.</span></span> <span data-ttu-id="e7a2a-151">属性可以程序集、类或成员级别放置，以指示你要使用的请求、需求或重写的类型。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-151">Attributes can be placed at the assembly, class, or member level, to indicate the type of request, demand, or override you want to use.</span></span> <span data-ttu-id="e7a2a-152">请求用于面向公共语言运行时的应用程序，以通知运行时安全系统有关应用程序需要或不想要的权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-152">Requests are used in applications that target the common language runtime to inform the runtime security system about the permissions that your application needs or does not want.</span></span> <span data-ttu-id="e7a2a-153">在库中使用要求和重写以帮助保护调用方的资源或重写默认安全行为。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-153">Demands and overrides are used in libraries to help protect resources from callers or to override default security behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="e7a2a-154">在 .NET Framework 4 中，对 .NET Framework 安全模型和术语进行了重大更改。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-154">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="e7a2a-155">有关这些更改的详细信息，请参阅 [安全更改](/previous-versions/dotnet/framework/security/security-changes)。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-155">For more information about these changes, see [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>

<span data-ttu-id="e7a2a-156">为了使用声明性安全调用，必须初始化权限对象的状态数据，使其表示所需权限的特定形式。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-156">In order to use declarative security calls, you must initialize the state data of the permission object so that it represents the particular form of permission you need.</span></span> <span data-ttu-id="e7a2a-157">每个内置权限都具有一个属性，会向该属性传递 <xref:System.Security.Permissions.SecurityAction> 枚举来描述你要执行的安全操作的类型。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-157">Every built-in permission has an attribute that is passed a <xref:System.Security.Permissions.SecurityAction> enumeration to describe the type of security operation you want to perform.</span></span> <span data-ttu-id="e7a2a-158">但是，权限还接受自己独占的自己的参数。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-158">However, permissions also accept their own parameters that are exclusive to them.</span></span>

<span data-ttu-id="e7a2a-159">下列代码段显示一个声明性语法，用于要求代码调用方具有称为 `MyPermission` 的自定义权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-159">The following code fragment shows declarative syntax for requesting that your code's callers have a custom permission called `MyPermission`.</span></span> <span data-ttu-id="e7a2a-160">此权限是假设的自定义权限，在 .NET Framework 中并不存在。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-160">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="e7a2a-161">在此示例中，声明性调用直接放置在类定义之前，指定此权限应用于类级别。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-161">In this example, the declarative call is placed directly before the class definition, specifying that this permission be applied to the class level.</span></span> <span data-ttu-id="e7a2a-162">向属性传递 **SecurityAction** 结构，以指定调用方必须拥有此权限才能运行。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-162">The attribute is passed a **SecurityAction.Demand** structure to specify that callers must have this permission in order to run.</span></span>

```vb
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1

   Public Sub New()
      'The constructor is protected by the security call.
   End Sub

   Public Sub MyMethod()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'This method is protected by the security call.
   End Sub
End Class
```

```csharp
[MyPermission(SecurityAction.Demand, Unrestricted = true)]
public class MyClass
{
   public MyClass()
   {
      //The constructor is protected by the security call.
   }

   public void MyMethod()
   {
      //This method is protected by the security call.
   }

   public void YourMethod()
   {
      //This method is protected by the security call.
   }
}
```

## <a name="imperative-security"></a><span data-ttu-id="e7a2a-163">强制安全性</span><span class="sxs-lookup"><span data-stu-id="e7a2a-163">Imperative Security</span></span>

<span data-ttu-id="e7a2a-164">强制性安全语法通过创建你要调用的权限对象的新实例发出安全调用。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-164">Imperative security syntax issues a security call by creating a new instance of the permission object you want to invoke.</span></span> <span data-ttu-id="e7a2a-165">强制性语法可用于执行需求和重写，但不可用于执行请求。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-165">You can use imperative syntax to perform demands and overrides, but not requests.</span></span>

<span data-ttu-id="e7a2a-166">进行安全调用之前，必须初始化权限对象的状态数据，使其表示所需权限的特定形式。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-166">Before you make the security call, you must initialize the state data of the permission object so that it represents the particular form of the permission you need.</span></span> <span data-ttu-id="e7a2a-167">例如，在创建对象时 <xref:System.Security.Permissions.FileIOPermission> ，可以使用构造函数来初始化 **FileIOPermission** 对象，使其表示对所有文件的不受限制的访问权限，或者不能访问文件。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-167">For example, when creating a <xref:System.Security.Permissions.FileIOPermission> object, you can use the constructor to initialize the **FileIOPermission** object so that it represents either unrestricted access to all files or no access to files.</span></span> <span data-ttu-id="e7a2a-168">或者，你可以使用不同的 **FileIOPermission** 对象，传递指定你希望对象表示的访问类型的参数 (即读取、追加或写入) 以及希望对象保护的文件。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-168">Or, you can use a different **FileIOPermission** object, passing parameters that indicate the type of access you want the object to represent (that is, read, append, or write) and what files you want the object to protect.</span></span>

<span data-ttu-id="e7a2a-169">除了使用命令性安全语法来调用单个安全对象，你还可以使用它来初始化权限集中的一组权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-169">In addition to using imperative security syntax to invoke a single security object, you can use it to initialize a group of permissions in a permission set.</span></span> <span data-ttu-id="e7a2a-170">例如，这种方法是在一个方法中对多个权限可靠地执行 [assert](using-the-assert-method.md) 调用的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-170">For example, this technique is the only way to reliably perform [assert](using-the-assert-method.md) calls on multiple permissions in one method.</span></span> <span data-ttu-id="e7a2a-171">使用 <xref:System.Security.PermissionSet> 和 <xref:System.Security.NamedPermissionSet> 类来创建一组权限，然后调用合适的方法来调用所需的安全调用。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-171">Use the <xref:System.Security.PermissionSet> and <xref:System.Security.NamedPermissionSet> classes to create a group of permissions and then call the appropriate method to invoke the desired security call.</span></span>

<span data-ttu-id="e7a2a-172">强制性语法可用于执行需求和重写，但不可用于执行请求。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-172">You can use imperative syntax to perform demands and overrides, but not requests.</span></span> <span data-ttu-id="e7a2a-173">当初始化权限状态所需的信息仅在运行时变成已知时，你可能会为需求和重写使用命令性语法而不是声明性语法。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-173">You might use imperative syntax for demands and overrides instead of declarative syntax when information that you need in order to initialize the permission state becomes known only at run time.</span></span> <span data-ttu-id="e7a2a-174">例如，如果想确保调用方具有读取某个文件的权限，但直到运行时都不知道该文件的名称，在这种情况下，则使用命令性需求。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-174">For example, if you want to ensure that callers have permission to read a certain file, but you do not know the name of that file until run time, use an imperative demand.</span></span> <span data-ttu-id="e7a2a-175">当你需要在运行时确定是否存在一个条件以及根据测试结果是否发出安全要求时，也可以选择使用命令性检查而不是声明性检查。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-175">You might also choose to use imperative checks instead of declarative checks when you need to determine at run time whether a condition holds and, based on the result of the test, make a security demand (or not).</span></span>

<span data-ttu-id="e7a2a-176">下列代码段显示了声明性语法，用于要求代码调用方具有名为 `MyPermission` 的自定义权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-176">The following code fragment shows imperative syntax for requesting that your code's callers have a custom permission called `MyPermission`.</span></span> <span data-ttu-id="e7a2a-177">此权限是假设的自定义权限，在 .NET Framework 中并不存在。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-177">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="e7a2a-178">在 `MyMethod` 中创建了 `MyPermission` 的新实例，用于通过安全调用仅对此方法提供保护。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-178">A new instance of `MyPermission` is created in `MyMethod`, guarding only this method with the security call.</span></span>

```vb
Public Class MyClass1

   Public Sub New()

   End Sub

   Public Sub MyMethod()
      'MyPermission is demanded using imperative syntax.
      Dim Perm As New MyPermission()
      Perm.Demand()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'YourMethod 'This method is not protected by the security call.
   End Sub
End Class
```

```csharp
public class MyClass {
   public MyClass(){

   }

   public void MyMethod() {
       //MyPermission is demanded using imperative syntax.
       MyPermission Perm = new MyPermission();
       Perm.Demand();
       //This method is protected by the security call.
   }

   public void YourMethod() {
       //This method is not protected by the security call.
   }
}
```

## <a name="using-managed-wrapper-classes"></a><span data-ttu-id="e7a2a-179">使用托管包装类</span><span class="sxs-lookup"><span data-stu-id="e7a2a-179">Using Managed Wrapper Classes</span></span>

<span data-ttu-id="e7a2a-180">大多数应用程序和组件（安全库除外） 不应直接调用非托管代码。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-180">Most applications and components (except secure libraries) should not directly call unmanaged code.</span></span> <span data-ttu-id="e7a2a-181">其原因有若干：</span><span class="sxs-lookup"><span data-stu-id="e7a2a-181">There are several reasons for this.</span></span> <span data-ttu-id="e7a2a-182">如果代码直接调用非托管代码，在许多情况下将不允许该代码运行，因为必须授予代码调用本机代码所需的高级别信任。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-182">If code calls unmanaged code directly, it will not be allowed to run in many circumstances because code must be granted a high level of trust to call native code.</span></span> <span data-ttu-id="e7a2a-183">如果为允许此类应用程序运行而修改策略，则会大大削弱系统安全性，这样的话，应用程序能自由执行几乎所有操作。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-183">If policy is modified to allow such an application to run, it can significantly weaken the security of the system, leaving the application free to perform almost any operation.</span></span>

<span data-ttu-id="e7a2a-184">此外，有权访问非托管代码的代码很可能会通过调用非托管 API 来执行几乎任何操作。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-184">Additionally, code that has permission to access unmanaged code can probably perform almost any operation by calling into an unmanaged API.</span></span> <span data-ttu-id="e7a2a-185">例如，有权调用非托管代码的代码不需要 <xref:System.Security.Permissions.FileIOPermission> 访问文件; 它可以直接调用非托管 (Win32) 文件 api，绕过需要 **FileIOPermission**的托管文件 api。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-185">For example, code that has permission to call unmanaged code does not need <xref:System.Security.Permissions.FileIOPermission> to access a file; it can just call an unmanaged (Win32) file API directly, bypassing the managed file API that requires **FileIOPermission**.</span></span> <span data-ttu-id="e7a2a-186">如果托管代码有权调入非托管代码并直接调入非托管代码，安全系统将无法可靠地强制执行安全限制，因为运行时无法对非托管代码强制执行这类限制。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-186">If managed code has permission to call into unmanaged code and does call directly into unmanaged code, the security system will be unable to reliably enforce security restrictions, since the runtime cannot enforce such restrictions on unmanaged code.</span></span>

<span data-ttu-id="e7a2a-187">如果希望应用程序执行需要访问非托管代码的操作，则应该通过包装所需功能的受信任的托管类（如果存在这样的类）来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-187">If you want your application to perform an operation that requires accessing unmanaged code, it should do so through a trusted managed class that wraps the required functionality (if such a class exists).</span></span> <span data-ttu-id="e7a2a-188">如果安全类库中已存在包装类，请不要自己创建此类。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-188">Do not create a wrapper class yourself if one already exists in a secure class library.</span></span> <span data-ttu-id="e7a2a-189">必须向此包装类授予高级别的信任度，该包装类才能调入非托管代码，该包装类负责要求调入方具有合适权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-189">The wrapper class, which must be granted a high degree of trust to be allowed to make the call into unmanaged code, is responsible for demanding that its callers have the appropriate permissions.</span></span> <span data-ttu-id="e7a2a-190">如果使用包装类，你的代码只需请求并被授予包装类要求的权限。</span><span class="sxs-lookup"><span data-stu-id="e7a2a-190">If you use the wrapper class, your code only needs to request and be granted the permissions that the wrapper class demands.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7a2a-191">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7a2a-191">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="e7a2a-192">ActualRebinds</span><span class="sxs-lookup"><span data-stu-id="e7a2a-192">Assert</span></span>](using-the-assert-method.md)
- [<span data-ttu-id="e7a2a-193">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="e7a2a-193">Code Access Security</span></span>](code-access-security.md)
- [<span data-ttu-id="e7a2a-194">代码访问安全性基础知识</span><span class="sxs-lookup"><span data-stu-id="e7a2a-194">Code Access Security Basics</span></span>](code-access-security-basics.md)
- [<span data-ttu-id="e7a2a-195">特性</span><span class="sxs-lookup"><span data-stu-id="e7a2a-195">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="e7a2a-196">元数据和自描述组件</span><span class="sxs-lookup"><span data-stu-id="e7a2a-196">Metadata and Self-Describing Components</span></span>](../../standard/metadata-and-self-describing-components.md)
