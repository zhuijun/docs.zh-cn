---
title: 如何：创建 GenericPrincipal 和 GenericIdentity 对象
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: 57ffe3fd2d446b4a7364aa531e785bfb79520a0a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558207"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="df220-102">如何：创建 GenericPrincipal 和 GenericIdentity 对象</span><span class="sxs-lookup"><span data-stu-id="df220-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

> [!NOTE]
> <span data-ttu-id="df220-103">本文适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="df220-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="df220-104">有关 ASP.NET Core 的信息，请参阅 [ASP.NET Core 安全性概述](/aspnet/core/security/)。</span><span class="sxs-lookup"><span data-stu-id="df220-104">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="df220-105">你可以将 <xref:System.Security.Principal.GenericIdentity> 类与类结合使用 <xref:System.Security.Principal.GenericPrincipal> ，以创建独立于 Windows 域的授权方案。</span><span class="sxs-lookup"><span data-stu-id="df220-105">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="df220-106">创建 GenericPrincipal 对象</span><span class="sxs-lookup"><span data-stu-id="df220-106">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="df220-107">创建标识类的一个新实例，并用希望它持有的名称对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="df220-107">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="df220-108">以下代码创建一个新的 **GenericIdentity** 对象，并用名称 `MyUser` 对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="df220-108">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="df220-109">创建 **GenericPrincipal** 类的一个新实例，并用先前创建的 **GenericIdentity** 对象和表示希望与此主体关联的角色的字符串数组对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="df220-109">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="df220-110">下面的代码示例指定表示一个管理员角色和一个用户角色的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="df220-110">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="df220-111">然后用前面的 **GenericIdentity** 和该字符串数组对 **GenericPrincipal** 进行初始化。</span><span class="sxs-lookup"><span data-stu-id="df220-111">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="df220-112">使用以下代码将主体附加到当前线程中。</span><span class="sxs-lookup"><span data-stu-id="df220-112">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="df220-113">这在以下情况下很有用：必须多次验证主体，必须由应用程序中运行的其他代码验证，或者必须由 <xref:System.Security.Permissions.PrincipalPermission> 对象验证。</span><span class="sxs-lookup"><span data-stu-id="df220-113">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="df220-114">不将主体附加到线程中，仍可对主体对象执行基于角色的验证。</span><span class="sxs-lookup"><span data-stu-id="df220-114">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="df220-115">有关详细信息，请参阅[替换主体对象](replacing-a-principal-object.md)。</span><span class="sxs-lookup"><span data-stu-id="df220-115">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="df220-116">示例</span><span class="sxs-lookup"><span data-stu-id="df220-116">Example</span></span>

<span data-ttu-id="df220-117">下面的代码示例说明如何创建 **GenericPrincipal** 和 **GenericIdentity** 的实例。</span><span class="sxs-lookup"><span data-stu-id="df220-117">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="df220-118">此代码将这些对象的值显示到控制台中。</span><span class="sxs-lookup"><span data-stu-id="df220-118">This code displays the values of these objects to the console.</span></span>

```vb
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

<span data-ttu-id="df220-119">执行时，应用程序显示类似于下面这样的输出。</span><span class="sxs-lookup"><span data-stu-id="df220-119">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="df220-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="df220-120">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="df220-121">替换 Principal 对象</span><span class="sxs-lookup"><span data-stu-id="df220-121">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="df220-122">主体和标识对象</span><span class="sxs-lookup"><span data-stu-id="df220-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
