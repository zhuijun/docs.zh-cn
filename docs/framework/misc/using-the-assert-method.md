---
title: 使用 Assert 方法
description: 了解如何使用 Assert 方法来使你的代码（和下游调用方的代码）可以执行你的代码对你的代码具有权限（而不是其调用方）。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
ms.openlocfilehash: 096e0375a94c92a835cccb4d1b3297783b4120e9
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309802"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="1c1e6-103">使用 Assert 方法</span><span class="sxs-lookup"><span data-stu-id="1c1e6-103">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="1c1e6-104"><xref:System.Security.CodeAccessPermission.Assert%2A> 是一种可在代码访问权限类和 <xref:System.Security.PermissionSet> 类上调用的方法。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-104"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="1c1e6-105">您可以使用**Assert**来实现您的代码（和下游调用方）执行您的代码有权执行的操作，但其调用方可能无权执行此操作。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-105">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="1c1e6-106">安全断言会更改在安全检查期间运行时所执行的正常过程。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-106">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="1c1e6-107">断言权限时，它会通知安全系统不检查断言权限的代码的调用方。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-107">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1c1e6-108">请谨慎使用断言，因为它们会打开安全漏洞并破坏运行时强制执行安全限制的机制。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-108">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="1c1e6-109">当库调用非托管代码或所执行的调用需要与库的预期用途不明显关联的权限时，断言非常有用。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-109">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="1c1e6-110">例如，调用到非托管代码的所有托管代码都必须具有指定了**UnmanagedCode**标志的**SecurityPermission** 。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-110">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="1c1e6-111">默认情况下，如果代码不是来自本地计算机（如从本地 intranet 下载的代码），则不会对其授予此权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-111">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="1c1e6-112">因此，为了使从本地 intranet 下载的代码能调用使用非托管代码的库，它必须具有由该库断言的权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-112">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="1c1e6-113">此外，某些库可能会执行对调用方不可见且需要特殊权限的调用。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-113">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="1c1e6-114">在代码以对调用方完全不可见的方式访问资源时，也可使用断言。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-114">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="1c1e6-115">例如，假设你的库从数据库获取信息，但在此过程中还会从计算机注册表读取信息。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-115">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="1c1e6-116">由于使用您的库的开发人员不能访问您的源，因此他们无法知道其代码需要**system.security.permissions.registrypermission>** 才能使用您的代码。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-116">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="1c1e6-117">在此情况下，如果你决定要求代码调用方有权访问注册表是不合理或不必要的，你可以断言权限以读取注册表。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-117">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="1c1e6-118">在这种情况下，适合库断言权限，使没有**system.security.permissions.registrypermission>** 的调用方可以使用库。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-118">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="1c1e6-119">仅当断言权限和下游调用方所需的权限属于同一类型且要求的权限是断言权限的子集时，断言才会影响堆栈审核。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-119">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="1c1e6-120">例如，如果你将**FileIOPermission**声明为读取 C 驱动器上的所有文件，并且**FileIOPermission**读取 C：\Temp 中的文件，则断言可能会影响堆栈审核;但是，如果要求**FileIOPermission**写入 C 驱动器，则断言不起作用。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-120">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="1c1e6-121">若要执行断言，必须向你的代码授予正在断言的权限以及表示有权执行断言的 <xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-121">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="1c1e6-122">虽然你可以断言尚未授予代码的权限，但此断言毫无意义，因为安全检查在断言使其成功之前就会失败。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-122">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="1c1e6-123">下图显示了使用**Assert**时会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-123">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="1c1e6-124">假设以下语句针对程序集 A、B、C、E 和 F 以及 P1 和 P1A 两个权限为 true：</span><span class="sxs-lookup"><span data-stu-id="1c1e6-124">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="1c1e6-125">P1A 表示读取 C 驱动器上的 .txt 文件的权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-125">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="1c1e6-126">P1 表示读取 C 驱动器上所有文件的权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-126">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="1c1e6-127">P1A 和 P1 均为**FileIOPermission**类型，而 P1A 是 P1 的子集。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-127">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="1c1e6-128">已向程序集 E 和 F 授予了 P1A 权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-128">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="1c1e6-129">已向程序集 C 授予了 P1 权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-129">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="1c1e6-130">尚未向程序集 A 和 B 授予 P1 或 P1A 权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-130">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="1c1e6-131">方法 A 包含在程序集 A 中，方法 B 包含在程序集 B 中，依次类推。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-131">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![显示断言方法程序集的关系图。](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="1c1e6-133">在此方案中，方法 A 调用 B，B 调用 C，C 调用 E，E 调用 F。方法 C 断言权限以读取 C 驱动器上的文件（权限 P1），而方法 E 要求权限读取 C 驱动器上的 .txt 文件（权限 P1A）。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="1c1e6-134">当在运行时遇到 F 中的请求时，将执行堆栈遍历来检查 F 的所有调用方的权限，从 E. E 获得 P1A 权限，因此堆栈审核会继续检查 C 的权限，其中发现 C 的断言。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="1c1e6-135">因为要求的权限 (P1A) 是断言的权限 (P1) 的子集，所以堆栈审核将停止且安全检查会自动成功。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="1c1e6-136">未向程序集 A 和 B 授予权限 P1A 并不重要。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="1c1e6-137">通过断言 P1，方法 C 确保其调用方可以访问受 P1 保护的资源，即使尚未授予调用方访问该资源的权限也是如此。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="1c1e6-138">如果你设计一个类库且某个类访问受保护的资源，则在大多数情况下，你应该提出安全要求，要求此类的调用方拥有适当的权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="1c1e6-139">如果类随后执行你知道其大多数调用方不具有权限的操作，并且你愿意承担让这些调用方调用你的代码的责任，则可以通过对表示代码正在执行的操作的权限对象调用**assert**方法来断言权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="1c1e6-140">以这种方式使用**断言**可以使通常不能调用你的代码的调用方。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="1c1e6-141">因此，如果你断言了一个权限，应确保预先执行了适当的安全检查，以防止你的组件被误用。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="1c1e6-142">例如，假设你的高度受信任的库类具有删除文件的方法。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="1c1e6-143">它通过调用非托管的 Win32 函数来访问文件。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="1c1e6-144">调用方调用你的代码的**Delete**方法，并传入要删除的文件的名称，C:\Test.txt。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="1c1e6-145">在**Delete**方法中，你的代码将创建一个对象，该 <xref:System.Security.Permissions.FileIOPermission> 对象表示对 C:\Test.txt 的写访问。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="1c1e6-146">（删除文件需要写访问权限。）然后，你的代码通过调用**FileIOPermission**对象的**要求**方法来调用命令性安全检查。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="1c1e6-147">如果调用堆栈中的某个调用方不具有此权限，则会引发 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="1c1e6-148">如果未引发任何异常，你会知道所有调用方都有权限访问 C:\Test.txt。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="1c1e6-149">由于你认为大多数调用方不具有访问非托管代码的权限，因此你的代码会创建一个 <xref:System.Security.Permissions.SecurityPermission> 对象，该对象表示调用非托管代码和调用该对象的**断言**方法的权限。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="1c1e6-150">最后，它会调用非托管的 Win32 函数来删除 C:\Text.txt，并将控件返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1c1e6-151">你必须确保你的代码在以下情况下不使用断言：其他代码可使用你的代码来访问由你正在断言的权限所保护的资源。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="1c1e6-152">例如，在写入文件（其名称由调用方指定为参数）的代码中，你将不会断言**FileIOPermission**来写入文件，因为你的代码将被第三方滥用。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="1c1e6-153">使用命令性安全语法时，对同一方法中的多个权限调用**Assert**方法会引发安全异常。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="1c1e6-154">相反，应创建**PermissionSet**对象，向其传递要调用的单个权限，然后调用**PermissionSet**对象上的**Assert**方法。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="1c1e6-155">使用声明性安全语法时，可以多次调用**断言**方法。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="1c1e6-156">下面的示例演示了使用**Assert**方法重写安全检查的声明性语法。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="1c1e6-157">请注意，**来**语法采用两个值：一个 <xref:System.Security.Permissions.SecurityAction> 枚举，以及要向其授予权限的文件或目录的位置。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="1c1e6-158">**Assert** `C:\Log.txt` 即使不检查调用方是否有权访问该文件，调用断言也会导致访问权限成功。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}
```  
  
 <span data-ttu-id="1c1e6-159">下面的代码片段演示了使用**Assert**方法重写安全检查的命令性语法。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="1c1e6-160">在此示例中，声明了**FileIOPermission**对象的实例。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="1c1e6-161">其构造函数被传递**FileIOPermissionAccess**以定义允许的访问类型，后跟描述文件位置的字符串。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="1c1e6-162">定义**FileIOPermission**对象后，只需调用其**Assert**方法来重写安全检查。</span><span class="sxs-lookup"><span data-stu-id="1c1e6-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c1e6-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="1c1e6-163">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="1c1e6-164">特性</span><span class="sxs-lookup"><span data-stu-id="1c1e6-164">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="1c1e6-165">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="1c1e6-165">Code Access Security</span></span>](code-access-security.md)
