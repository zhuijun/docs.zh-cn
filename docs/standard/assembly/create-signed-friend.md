---
title: 如何：创建已签名的友元程序集
description: 本文演示如何将友元程序集和具有强名称的程序集一起使用。 其中包含有关 .NET 安全性的信息。
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: b6176afed44e32911a37a0d753cea2bae7d8554e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378546"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="fcaf9-104">如何：创建已签名的友元程序集</span><span class="sxs-lookup"><span data-stu-id="fcaf9-104">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="fcaf9-105">本示例演示如何将友元程序集和具有强名称的程序集一起使用。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-105">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="fcaf9-106">这两种程序集必须都使用强名称。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-106">Both assemblies must be strong named.</span></span> <span data-ttu-id="fcaf9-107">尽管本示例中的两种程序集使用相同的密钥，但可以对这两种程序集使用不同的密钥。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-107">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="fcaf9-108">创建已签名的程序集和友元程序集</span><span class="sxs-lookup"><span data-stu-id="fcaf9-108">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="fcaf9-109">打开命令提示。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="fcaf9-110">使用强名称工具，通过以下命令序列生成 keyfile 并显示其公钥。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-110">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="fcaf9-111">有关详细信息，请参阅 [Sn.exe（强名称工具）](../../framework/tools/sn-exe-strong-name-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-111">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="fcaf9-112">生成此示例的强名称密钥，并将其存储在 FriendAssemblies.snk 文件中：</span><span class="sxs-lookup"><span data-stu-id="fcaf9-112">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="fcaf9-113">从 FriendAssemblies.snk 文件中提取公钥，将其放入 FriendAssemblies.publickey 中 ：</span><span class="sxs-lookup"><span data-stu-id="fcaf9-113">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="fcaf9-114">显示存储在 FriendAssemblies.publickey 文件中的公钥：</span><span class="sxs-lookup"><span data-stu-id="fcaf9-114">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="fcaf9-115">创建名为 friend_signed_A 的 C# 或 Visual Basic 文件，其中包含以下代码。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-115">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="fcaf9-116">该代码使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性将 friend_signed_B 声明为友元程序集。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-116">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="fcaf9-117">强名称工具在每次运行时生成新的公钥。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-117">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="fcaf9-118">因此，必须将以下代码中的公钥替换为刚生成的公钥，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-118">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="fcaf9-119">使用以下命令编译 friend_signed_A 并为其签名。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-119">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="fcaf9-120">创建名为 friend_signed_B 的 C# 或 Visual Basic 文件，其中包含以下代码。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-120">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="fcaf9-121">由于 friend_signed_A 将 friend_signed_B 指定为友元程序集，因此 friend_signed_B 中的代码可以访问 friend_signed_A 中的 `internal` (C#) 或 `Friend` (Visual Basic) 类型和成员   。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-121">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="fcaf9-122">文件包含以下代码。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-122">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="fcaf9-123">使用以下命令编译 friend_signed_B 并为其签名。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-123">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="fcaf9-124">编译器生成的程序集的名称必须与传递给 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性的友元程序集的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-124">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="fcaf9-125">必须使用 `-out` 编译器选项显式指定输出程序集（.exe 或 .dll）的名称 。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-125">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="fcaf9-126">有关详细信息，请参阅 [-out（C# 编译器选项）](../../csharp/language-reference/compiler-options/out-compiler-option.md)或 [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-126">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="fcaf9-127">运行 friend_signed_B.exe 文件。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-127">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="fcaf9-128">程序将输出字符串“Class1.Test”。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-128">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="fcaf9-129">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="fcaf9-129">.NET security</span></span>  
 <span data-ttu-id="fcaf9-130"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 类之间具有相似之处。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-130">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="fcaf9-131">主要区别是，<xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全权限来运行一段特定代码，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性控制 `internal` (C#) 和 `Friend` (Visual Basic) 类型和成员的可见性。</span><span class="sxs-lookup"><span data-stu-id="fcaf9-131">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcaf9-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="fcaf9-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="fcaf9-133">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="fcaf9-133">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="fcaf9-134">友元程序集</span><span class="sxs-lookup"><span data-stu-id="fcaf9-134">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="fcaf9-135">如何：创建未签名的友元程序集</span><span class="sxs-lookup"><span data-stu-id="fcaf9-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="fcaf9-136">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="fcaf9-136">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="fcaf9-137">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcaf9-137">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="fcaf9-138">Sn.exe（强名称工具）</span><span class="sxs-lookup"><span data-stu-id="fcaf9-138">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="fcaf9-139">创建和使用具有强名称的程序集</span><span class="sxs-lookup"><span data-stu-id="fcaf9-139">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="fcaf9-140">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="fcaf9-140">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fcaf9-141">编程概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcaf9-141">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
