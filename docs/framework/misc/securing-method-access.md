---
title: 保护方法访问
description: 了解如何对不打算公开使用但仍需要公共的方法进行方法访问。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
ms.openlocfilehash: f9b9bc00058aefc8f58facff43509e717967c2a7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555713"
---
# <a name="securing-method-access"></a><span data-ttu-id="a62e9-103">保护方法访问</span><span class="sxs-lookup"><span data-stu-id="a62e9-103">Securing Method Access</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="a62e9-104">某些方法可能不适用于允许任意不受信任的代码进行调用。</span><span class="sxs-lookup"><span data-stu-id="a62e9-104">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="a62e9-105">此类方法会带来几种风险：方法可能会提供一些受限制的信息；它可能信任传递给它的任何信息；它可能不会对参数执行错误检查；如果使用错误的参数，它还可能出现故障或执行某些有害操作。</span><span class="sxs-lookup"><span data-stu-id="a62e9-105">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="a62e9-106">应该注意这些情况，并采取措施以帮助保护这类方法。</span><span class="sxs-lookup"><span data-stu-id="a62e9-106">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="a62e9-107">在某些情况下，可能需要限制并不打算用于公共用途但仍须为公共方法的方法。</span><span class="sxs-lookup"><span data-stu-id="a62e9-107">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="a62e9-108">例如，可能有一个需在你自己的 DLL 间调用（从而必须为公共接口）的接口，但你不希望将其以公共方式公开，以防止客户使用它，或防止恶意代码利用入口点进入组件中。</span><span class="sxs-lookup"><span data-stu-id="a62e9-108">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="a62e9-109">限制不用于公共使用的方法的另一个常见原因是 (但必须是公共的) ，以避免必须记录和支持可能是内部接口的内容。</span><span class="sxs-lookup"><span data-stu-id="a62e9-109">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be an internal interface.</span></span>  
  
 <span data-ttu-id="a62e9-110">托管代码提供几种方法来限制方法访问：</span><span class="sxs-lookup"><span data-stu-id="a62e9-110">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="a62e9-111">如果可以信任类、程序集或派生类，则限制它们的可访问性的范围。</span><span class="sxs-lookup"><span data-stu-id="a62e9-111">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="a62e9-112">这是限制方法访问的最简单的方法。</span><span class="sxs-lookup"><span data-stu-id="a62e9-112">This is the simplest way to limit method access.</span></span> <span data-ttu-id="a62e9-113">通常，派生类的可信度可能低于它们派生自的类，但在某些情况下，它们共享父类的标识。</span><span class="sxs-lookup"><span data-stu-id="a62e9-113">In general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="a62e9-114">特别是，不要从关键字推断信任 `protected` ，这并不一定在安全上下文中使用。</span><span class="sxs-lookup"><span data-stu-id="a62e9-114">In particular, do not infer trust from the keyword `protected`, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="a62e9-115">限制对指定标识的调用方的方法访问-实质上，任何特定 [证据](/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)) (强名称、发布服务器、区域等) 你选择。</span><span class="sxs-lookup"><span data-stu-id="a62e9-115">Limit the method access to callers of a specified identity--essentially, any particular [evidence](/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="a62e9-116">限制对具有你选择的任何权限的调用方的方法访问。</span><span class="sxs-lookup"><span data-stu-id="a62e9-116">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="a62e9-117">同样，声明性安全使你可以控制类的继承。</span><span class="sxs-lookup"><span data-stu-id="a62e9-117">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="a62e9-118">您可以使用 **InheritanceDemand** 来执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a62e9-118">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="a62e9-119">要求派生类具有指定的标识或权限。</span><span class="sxs-lookup"><span data-stu-id="a62e9-119">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="a62e9-120">要求重写特定方法的派生类具有指定的标识或权限。</span><span class="sxs-lookup"><span data-stu-id="a62e9-120">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="a62e9-121">下面的示例演示如何通过要求使用特定强名称对调用方进行签名来帮助保护具有有限访问权限的公共类。</span><span class="sxs-lookup"><span data-stu-id="a62e9-121">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="a62e9-122">此示例使用 <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> 带有强名称 **需求** 的。</span><span class="sxs-lookup"><span data-stu-id="a62e9-122">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="a62e9-123">有关如何使用强名称为程序集签名的信息，请参阅 [创建和使用具有强名称的程序集](../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="a62e9-123">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="a62e9-124">防止不受信任的代码使用类和成员</span><span class="sxs-lookup"><span data-stu-id="a62e9-124">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="a62e9-125">使用本节中所示的声明来防止部分受信任的代码使用特定的类、方法以及属性和事件。</span><span class="sxs-lookup"><span data-stu-id="a62e9-125">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="a62e9-126">通过将这些声明应用于类，可以将保护应用于其所有方法、属性和事件。</span><span class="sxs-lookup"><span data-stu-id="a62e9-126">By applying these declarations to a class, you apply the protection to all its methods, properties, and events.</span></span> <span data-ttu-id="a62e9-127">但是，字段访问不受声明性安全的影响。</span><span class="sxs-lookup"><span data-stu-id="a62e9-127">However, field access is not affected by declarative security.</span></span> <span data-ttu-id="a62e9-128">也请注意，链接要求仅帮助不受直接调用方的攻击，可能仍会受到引诱攻击。</span><span class="sxs-lookup"><span data-stu-id="a62e9-128">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a62e9-129">.NET Framework 4 中引入了一个新的透明度模型。</span><span class="sxs-lookup"><span data-stu-id="a62e9-129">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="a62e9-130">[安全透明的代码，级别 2](security-transparent-code-level-2.md)模型用属性标识安全代码 <xref:System.Security.SecurityCriticalAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="a62e9-130">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="a62e9-131">安全关键代码需要调用方和继承者均完全受信任。</span><span class="sxs-lookup"><span data-stu-id="a62e9-131">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="a62e9-132">在早期 .NET Framework 版本中的代码访问安全性规则下运行的程序集可以调用级别 2 程序集。</span><span class="sxs-lookup"><span data-stu-id="a62e9-132">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="a62e9-133">在这种情况下，安全关键属性将被视为完全信任的链接要求。</span><span class="sxs-lookup"><span data-stu-id="a62e9-133">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="a62e9-134">在强名称程序集中， [LinkDemand](link-demands.md) 应用于所有可公开访问的方法、属性和事件，以将其使用限制为完全受信任的调用方。</span><span class="sxs-lookup"><span data-stu-id="a62e9-134">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="a62e9-135">若要禁用此功能，必须应用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="a62e9-135">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="a62e9-136">因此，仅未签名的程序集或具有此特性的程序集需要显式标记类以排除不受信任调用方；可以使用这些声明来标记其中并不打算用于不受信任的调用方的类型子集。</span><span class="sxs-lookup"><span data-stu-id="a62e9-136">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="a62e9-137">下面的示例说明如何防止不受信任的代码使用类和成员。</span><span class="sxs-lookup"><span data-stu-id="a62e9-137">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="a62e9-138">对于公共非密封类：</span><span class="sxs-lookup"><span data-stu-id="a62e9-138">For public nonsealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="a62e9-139">对于公共密封类：</span><span class="sxs-lookup"><span data-stu-id="a62e9-139">For public sealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="a62e9-140">对于公共抽象类：</span><span class="sxs-lookup"><span data-stu-id="a62e9-140">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 <span data-ttu-id="a62e9-141">对于公共虚拟函数：</span><span class="sxs-lookup"><span data-stu-id="a62e9-141">For public virtual functions:</span></span>  
  
```vb  
Class Base1
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 <span data-ttu-id="a62e9-142">对于公共抽象函数：</span><span class="sxs-lookup"><span data-stu-id="a62e9-142">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="a62e9-143">对于基类不要求完全信任的公共重写函数：</span><span class="sxs-lookup"><span data-stu-id="a62e9-143">For public override functions where the base class does not demand full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="a62e9-144">对于基类要求完全信任的公共重写函数：</span><span class="sxs-lookup"><span data-stu-id="a62e9-144">For public override functions where the base class demands full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="a62e9-145">对于公共接口：</span><span class="sxs-lookup"><span data-stu-id="a62e9-145">For public interfaces:</span></span>  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="a62e9-146">Virtual Internal 重写或 Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="a62e9-146">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a62e9-147">本部分对在 `virtual` `internal` `Overloads` `Overridable` `Friend` Visual Basic) 中将方法声明为和 (时的安全问题进行了警告。</span><span class="sxs-lookup"><span data-stu-id="a62e9-147">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="a62e9-148">此警告仅适用于 .NET Framework 版本1.0 和1.1，不适用于更高版本。</span><span class="sxs-lookup"><span data-stu-id="a62e9-148">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="a62e9-149">在 .NET Framework 版本1.0 和1.1 中，你必须了解类型系统可访问性在确认你的代码对其他程序集不可用时的细微差别。</span><span class="sxs-lookup"><span data-stu-id="a62e9-149">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="a62e9-150">在 Visual Basic) 可以重写父类项的情况中，声明为 **虚拟** 和 **内部** (重载可重写 **Friend** 的方法，并且只能在同一程序集中使用该方法，因为它是内部的。</span><span class="sxs-lookup"><span data-stu-id="a62e9-150">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="a62e9-151">但是，重写的可访问性由 **virtual** 关键字确定，只要代码有权访问类本身，就可以从其他程序集进行重写。</span><span class="sxs-lookup"><span data-stu-id="a62e9-151">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="a62e9-152">如果重写的可能性导致了问题，请使用声明性安全修复此问题，如果不是绝对必需的，则删除 **虚拟** 关键字。</span><span class="sxs-lookup"><span data-stu-id="a62e9-152">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="a62e9-153">即使语言编译器阻止这些重写的编译错误，使用其他编译器编写的代码也可能会重写。</span><span class="sxs-lookup"><span data-stu-id="a62e9-153">Even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62e9-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="a62e9-154">See also</span></span>

- [<span data-ttu-id="a62e9-155">安全编码准则</span><span class="sxs-lookup"><span data-stu-id="a62e9-155">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
