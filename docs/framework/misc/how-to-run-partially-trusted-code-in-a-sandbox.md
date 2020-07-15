---
title: 如何：运行沙盒中部分受信任的代码
description: 了解如何在 .NET 中的沙盒中运行部分受信任的代码。 AppDomain 类是一种对托管应用程序进行沙盒处理的有效方法。
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: e02b5d679fb1f5947373399ac1226732623ef96d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309230"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="71cfc-104">如何：运行沙盒中部分受信任的代码</span><span class="sxs-lookup"><span data-stu-id="71cfc-104">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="71cfc-105">沙盒处理是在受限制的安全环境中运行代码的做法，从而限制授予代码的访问权限。</span><span class="sxs-lookup"><span data-stu-id="71cfc-105">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="71cfc-106">例如，如果你有来自不完全信任的源的托管库，则不应将其作为完全受信任运行。</span><span class="sxs-lookup"><span data-stu-id="71cfc-106">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="71cfc-107">相反，应将代码放在将权限限制为预计需要的权限（例如 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 权限）的沙盒中。</span><span class="sxs-lookup"><span data-stu-id="71cfc-107">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="71cfc-108">沙盒处理还可用于测试将在部分受信任环境中运行的分发的代码。</span><span class="sxs-lookup"><span data-stu-id="71cfc-108">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="71cfc-109"><xref:System.AppDomain> 是为托管应用程序提供沙盒的有效途径。</span><span class="sxs-lookup"><span data-stu-id="71cfc-109">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="71cfc-110">用于运行部分受信任的代码的应用程序域具有定义受保护资源的权限，这些资源在于 <xref:System.AppDomain> 内运行时可用。</span><span class="sxs-lookup"><span data-stu-id="71cfc-110">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="71cfc-111">在 <xref:System.AppDomain> 内运行的代码由与 <xref:System.AppDomain> 关联的权限约束并且仅能访问指定的资源。</span><span class="sxs-lookup"><span data-stu-id="71cfc-111">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="71cfc-112"><xref:System.AppDomain> 还包括用于标识程序集（作为完全受信任的程序集加载）的 <xref:System.Security.Policy.StrongName> 数组。</span><span class="sxs-lookup"><span data-stu-id="71cfc-112">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="71cfc-113">这使 <xref:System.AppDomain> 的创建者能启动新沙盒域，该域允许特定的帮助程序程序集为完全受信任的程序集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-113">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="71cfc-114">将程序集加载为完全受信任的程序集的另一种方法是：将其放在全局程序集缓存中；但是，这会在该计算机上创建的所有应用程序域中将程序集加载为完全受信任的程序集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-114">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="71cfc-115">强名称列表支持提供更多限制性决定的每个 <xref:System.AppDomain> 的决策。</span><span class="sxs-lookup"><span data-stu-id="71cfc-115">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="71cfc-116">可以使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 方法重载为在沙盒中运行的应用程序指定权限集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-116">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="71cfc-117">此重载使你能够指定所需代码访问安全性的确切级别。</span><span class="sxs-lookup"><span data-stu-id="71cfc-117">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="71cfc-118">使用此重载加载到 <xref:System.AppDomain> 中的程序集可以仅具有指定的授予集，也可以是完全受信任的程序集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-118">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="71cfc-119">如果程序集位于全局程序集缓存中或在 `fullTrustAssemblies`（<xref:System.Security.Policy.StrongName>）数组参数中列出，则该程序集被授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="71cfc-119">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="71cfc-120">只应将已知完全受信任的程序集添加到 `fullTrustAssemblies` 列表中。</span><span class="sxs-lookup"><span data-stu-id="71cfc-120">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="71cfc-121">重载具有以下签名：</span><span class="sxs-lookup"><span data-stu-id="71cfc-121">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="71cfc-122"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 方法重载的参数指定 <xref:System.AppDomain> 的名称、<xref:System.AppDomain> 的证据、标识沙盒的应用程序基的 <xref:System.AppDomainSetup> 对象、要使用的权限集和完全受信任的程序集的强名称。</span><span class="sxs-lookup"><span data-stu-id="71cfc-122">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="71cfc-123">出于安全原因，在 `info` 参数中指定的应用程序基不应为主机应用程序的应用程序基。</span><span class="sxs-lookup"><span data-stu-id="71cfc-123">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="71cfc-124">对于 `grantSet` 参数，可以指定已显式创建的权限集或由 <xref:System.Security.SecurityManager.GetStandardSandbox%2A> 方法创建的标准权限集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-124">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="71cfc-125">与大多数 <xref:System.AppDomain> 加载不同，<xref:System.AppDomain> 的证据（由 `securityInfo` 参数提供）不用于确定部分受信任的程序集的授予集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-125">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="71cfc-126">相反，它由 `grantSet` 参数单独指定。</span><span class="sxs-lookup"><span data-stu-id="71cfc-126">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="71cfc-127">但证据可以用于其它目的，例如确定独立存储范围。</span><span class="sxs-lookup"><span data-stu-id="71cfc-127">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="71cfc-128">在沙盒中运行应用程序</span><span class="sxs-lookup"><span data-stu-id="71cfc-128">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="71cfc-129">创建要授予给不受信任的应用程序的权限集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-129">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="71cfc-130">可以授予的最小权限是 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 权限。</span><span class="sxs-lookup"><span data-stu-id="71cfc-130">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="71cfc-131">还可以授予其它你认为可能对不受信任的代码安全的权限；例如，<xref:System.Security.Permissions.IsolatedStorageFilePermission>。</span><span class="sxs-lookup"><span data-stu-id="71cfc-131">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="71cfc-132">下面的代码创建仅具有 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 权限的新权限集。</span><span class="sxs-lookup"><span data-stu-id="71cfc-132">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="71cfc-133">或者，可以使用现有的已命名权限集，如 Internet。</span><span class="sxs-lookup"><span data-stu-id="71cfc-133">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="71cfc-134"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> 方法返回 `Internet` 权限集或 `LocalIntranet` 权限集，具体取决于证据中的区域。</span><span class="sxs-lookup"><span data-stu-id="71cfc-134">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="71cfc-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> 还为一些作为引用传递的证据对象构造标识权限。</span><span class="sxs-lookup"><span data-stu-id="71cfc-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="71cfc-136">为包含调用不受信任的代码的宿主类（在此示例中，命名为 `Sandboxer`）的程序集签名。</span><span class="sxs-lookup"><span data-stu-id="71cfc-136">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="71cfc-137">将用于对程序集签名的 <xref:System.Security.Policy.StrongName> 添加到 <xref:System.AppDomain.CreateDomain%2A> 调用的 `fullTrustAssemblies` 参数的 <xref:System.Security.Policy.StrongName> 数组中。</span><span class="sxs-lookup"><span data-stu-id="71cfc-137">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="71cfc-138">主机类必须作为完全受信任的类运行，以启用部分信任代码的执行或为部分信任应用程序提供服务。</span><span class="sxs-lookup"><span data-stu-id="71cfc-138">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="71cfc-139">这就是读取程序集的 <xref:System.Security.Policy.StrongName> 的方式：</span><span class="sxs-lookup"><span data-stu-id="71cfc-139">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="71cfc-140">不需要将 .NET framework 程序集（如 mscorlib 和 System.dll）添加到完全信任列表中，因为它们是作为完全受信任的程序集从全局程序集缓存中加载的。</span><span class="sxs-lookup"><span data-stu-id="71cfc-140">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="71cfc-141">初始化 <xref:System.AppDomain.CreateDomain%2A> 方法的 <xref:System.AppDomainSetup> 参数。</span><span class="sxs-lookup"><span data-stu-id="71cfc-141">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="71cfc-142">使用此参数，可以控制新的 <xref:System.AppDomain> 的许多设置。</span><span class="sxs-lookup"><span data-stu-id="71cfc-142">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="71cfc-143"><xref:System.AppDomainSetup.ApplicationBase%2A> 属性是一个重要设置，并且应不同于宿主应用程序的 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="71cfc-143">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="71cfc-144">如果 <xref:System.AppDomainSetup.ApplicationBase%2A> 设置相同，则部分信任应用程序可以获取主机应用程序以加载（作为完全受信任的应用程序）它定义的异常，从而攻击它。</span><span class="sxs-lookup"><span data-stu-id="71cfc-144">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="71cfc-145">这是为什么不建议使用 catch（异常）的另一个原因。</span><span class="sxs-lookup"><span data-stu-id="71cfc-145">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="71cfc-146">将主机的应用程序基设置为与沙盒应用程序的应用程序基不同，这可降低攻击风险。</span><span class="sxs-lookup"><span data-stu-id="71cfc-146">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="71cfc-147">使用已指定的参数调用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 方法重载来创建应用程序域。</span><span class="sxs-lookup"><span data-stu-id="71cfc-147">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="71cfc-148">此方法的签名是：</span><span class="sxs-lookup"><span data-stu-id="71cfc-148">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="71cfc-149">其他信息：</span><span class="sxs-lookup"><span data-stu-id="71cfc-149">Additional information:</span></span>  
  
    - <span data-ttu-id="71cfc-150">这是唯一将 <xref:System.Security.PermissionSet> 作为参数的 <xref:System.AppDomain.CreateDomain%2A> 方法的重载，因而它是唯一允许以部分信任设置加载应用程序的重载。</span><span class="sxs-lookup"><span data-stu-id="71cfc-150">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="71cfc-151">`evidence` 参数不用于计算权限集；它由 .NET Framework 的其它功能用于标识。</span><span class="sxs-lookup"><span data-stu-id="71cfc-151">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="71cfc-152">此重载必须设置`info` 参数的 <xref:System.AppDomainSetup.ApplicationBase%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="71cfc-152">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="71cfc-153">`fullTrustAssemblies` 参数具有 `params` 关键字，这意味着不需要创建 <xref:System.Security.Policy.StrongName> 数组。</span><span class="sxs-lookup"><span data-stu-id="71cfc-153">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="71cfc-154">允许将 0、1 或更多强名称作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="71cfc-154">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="71cfc-155">要用于创建应用程序域的代码是：</span><span class="sxs-lookup"><span data-stu-id="71cfc-155">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="71cfc-156">将代码加载到已创建的沙盒 <xref:System.AppDomain> 中。</span><span class="sxs-lookup"><span data-stu-id="71cfc-156">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="71cfc-157">可以通过两种方法实现此目的：</span><span class="sxs-lookup"><span data-stu-id="71cfc-157">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="71cfc-158">调用程序集的 <xref:System.AppDomain.ExecuteAssembly%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="71cfc-158">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="71cfc-159">使用 <xref:System.Activator.CreateInstanceFrom%2A> 方法来创建派生自新的 <xref:System.AppDomain> 中的 <xref:System.MarshalByRefObject> 的类的实例。</span><span class="sxs-lookup"><span data-stu-id="71cfc-159">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="71cfc-160">第二种方法非常可取，因为这样可以更轻松地将参数传递给新的 <xref:System.AppDomain> 实例。</span><span class="sxs-lookup"><span data-stu-id="71cfc-160">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="71cfc-161"><xref:System.Activator.CreateInstanceFrom%2A> 方法提供两大重要功能：</span><span class="sxs-lookup"><span data-stu-id="71cfc-161">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="71cfc-162">可以使用指向不包含你的程序集的位置的基本代码。</span><span class="sxs-lookup"><span data-stu-id="71cfc-162">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="71cfc-163">可以在完全信任 (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>) 的 <xref:System.Security.CodeAccessPermission.Assert%2A> 下进行创建，这样就可以创建关键类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="71cfc-163">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="71cfc-164">（只要程序集没有透明标记，并加载为完全受信任，就会发生这种情况。）因此，你必须小心地仅创建与此函数信任的代码，我们建议你仅在新应用程序域中创建完全受信任的类的实例。</span><span class="sxs-lookup"><span data-stu-id="71cfc-164">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="71cfc-165">若要在新域中创建类的实例，该类必须扩展 <xref:System.MarshalByRefObject> 类。</span><span class="sxs-lookup"><span data-stu-id="71cfc-165">To create an instance of a class in a new domain, the class must extend the <xref:System.MarshalByRefObject> class.</span></span>
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="71cfc-166">将新的域实例解包到此域中的引用中。</span><span class="sxs-lookup"><span data-stu-id="71cfc-166">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="71cfc-167">此引用用于执行不受信任的代码。</span><span class="sxs-lookup"><span data-stu-id="71cfc-167">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="71cfc-168">调用你刚刚创建的 `Sandboxer` 类的实例中的 `ExecuteUntrustedCode` 方法。</span><span class="sxs-lookup"><span data-stu-id="71cfc-168">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="71cfc-169">此调用在具有受限权限的沙盒应用程序域中执行。</span><span class="sxs-lookup"><span data-stu-id="71cfc-169">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="71cfc-170"><xref:System.Reflection> 用于获取部分受信任的程序集中的方法的句柄。</span><span class="sxs-lookup"><span data-stu-id="71cfc-170"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="71cfc-171">该句柄可以用于以安全的方式、使用最小权限来执行代码。</span><span class="sxs-lookup"><span data-stu-id="71cfc-171">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="71cfc-172">在前面的代码中，请在打印 <xref:System.Security.SecurityException> 之前备注完全信任权限的 <xref:System.Security.PermissionSet.Assert%2A>。</span><span class="sxs-lookup"><span data-stu-id="71cfc-172">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="71cfc-173">完全信任断言用于从 <xref:System.Security.SecurityException> 中获取扩展信息。</span><span class="sxs-lookup"><span data-stu-id="71cfc-173">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="71cfc-174">没有 <xref:System.Security.PermissionSet.Assert%2A>，则 <xref:System.Security.SecurityException> 的 <xref:System.Security.SecurityException.ToString%2A> 方法将发现堆栈上有部分受信任的代码，并将限制返回的信息。</span><span class="sxs-lookup"><span data-stu-id="71cfc-174">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="71cfc-175">如果部分信任代码可以读取该信息，可能会导致安全问题，但可以通过不授予 <xref:System.Security.Permissions.UIPermission> 来缓解此风险。</span><span class="sxs-lookup"><span data-stu-id="71cfc-175">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="71cfc-176">完全信任断言应慎用，且仅在确定不允许部分信任代码提升为完全信任代码时使用。</span><span class="sxs-lookup"><span data-stu-id="71cfc-176">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="71cfc-177">一般来说，不要调用同一函数中不信任的代码，也不要在调用完全信任断言后调用代码。</span><span class="sxs-lookup"><span data-stu-id="71cfc-177">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="71cfc-178">始终在完成使用断言后还原断言，这是个好做法。</span><span class="sxs-lookup"><span data-stu-id="71cfc-178">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71cfc-179">示例</span><span class="sxs-lookup"><span data-stu-id="71cfc-179">Example</span></span>  
 <span data-ttu-id="71cfc-180">下面的示例实现前一部分中的过程。</span><span class="sxs-lookup"><span data-stu-id="71cfc-180">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="71cfc-181">在此示例中，Visual Studio 解决方案中一个名为 `Sandboxer` 的项目还包含一个名为 `UntrustedCode` 的项目（该项目实现类 `UntrustedClass`）。</span><span class="sxs-lookup"><span data-stu-id="71cfc-181">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="71cfc-182">此方案假定你已下载库程序集，该程序集包含应该返回 `true` 或 `false` 的方法，以指示你提供的数字是否为斐波纳契数。</span><span class="sxs-lookup"><span data-stu-id="71cfc-182">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="71cfc-183">相反，该方法会尝试从你的计算机中读取文件。</span><span class="sxs-lookup"><span data-stu-id="71cfc-183">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="71cfc-184">下面的示例演示不受信任的代码。</span><span class="sxs-lookup"><span data-stu-id="71cfc-184">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="71cfc-185">下面的示例演示执行不受信任的代码的 `Sandboxer` 应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="71cfc-185">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="71cfc-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71cfc-186">See also</span></span>

- [<span data-ttu-id="71cfc-187">代码安全维护指南</span><span class="sxs-lookup"><span data-stu-id="71cfc-187">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
