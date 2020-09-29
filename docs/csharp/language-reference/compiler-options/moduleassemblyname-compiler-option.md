---
description: -moduleassemblyname（C# 编译器选项）
title: -moduleassemblyname（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9131db17d767c76fe6a57f5d5353474153e0c269
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194084"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="6eb65-103">-moduleassemblyname（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="6eb65-103">-moduleassemblyname (C# Compiler Option)</span></span>

<span data-ttu-id="6eb65-104">指定一个程序集，.netmodule 可以访问其非公共类型。</span><span class="sxs-lookup"><span data-stu-id="6eb65-104">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb65-105">语法</span><span class="sxs-lookup"><span data-stu-id="6eb65-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="6eb65-106">自变量</span><span class="sxs-lookup"><span data-stu-id="6eb65-106">Arguments</span></span>  

 `assembly_name`  
 <span data-ttu-id="6eb65-107">.netmodule 可以访问其非公共类型的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="6eb65-107">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb65-108">备注</span><span class="sxs-lookup"><span data-stu-id="6eb65-108">Remarks</span></span>  

 <span data-ttu-id="6eb65-109">生成 .netmodule 时，应使用 -moduleassemblyname 并满足以下条件\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="6eb65-109">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="6eb65-110">.netmodule 需要具有访问现有程序集中非公共类型的权限。</span><span class="sxs-lookup"><span data-stu-id="6eb65-110">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="6eb65-111">知道生成后的 .netmodule 所在程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="6eb65-111">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="6eb65-112">现有程序集已经获得有元程序集访问权限，可访问生成后的 .netmodule 所在的程序集。</span><span class="sxs-lookup"><span data-stu-id="6eb65-112">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="6eb65-113">有关生成 .netmodule 的详细信息，请参阅 [-target: module（C# 编译器选项）](./target-module-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb65-113">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="6eb65-114">有关友元程序集的详细信息，请参阅[友元程序集](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb65-114">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="6eb65-115">此选项不适用于开发环境内，仅当从命令行编译时可用。</span><span class="sxs-lookup"><span data-stu-id="6eb65-115">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="6eb65-116">此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。</span><span class="sxs-lookup"><span data-stu-id="6eb65-116">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eb65-117">示例</span><span class="sxs-lookup"><span data-stu-id="6eb65-117">Example</span></span>  

 <span data-ttu-id="6eb65-118">此示例将生成包含私有类型的程序集，并且授予名为 csman_an_assembly 的程序集友元程序集访问权限。</span><span class="sxs-lookup"><span data-stu-id="6eb65-118">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class
{  
    public void Test()
    {
        Console.WriteLine("An_Internal_Class.Test called");
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="6eb65-119">示例</span><span class="sxs-lookup"><span data-stu-id="6eb65-119">Example</span></span>  

 <span data-ttu-id="6eb65-120">该例生成一个可访问程序集 moduleassemblyname_1.dll 中非公共类型的 .netmodule。</span><span class="sxs-lookup"><span data-stu-id="6eb65-120">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="6eb65-121">通过了解此 .netmodule 在生成后所在的程序集（名为 csman_an_assembly），可以指定 -moduleassemblyname，以便 .netmodule 在已经获得 csman_an_assembly 的友元程序集访问权限的程序集中访问非公共类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6eb65-121">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="6eb65-122">示例</span><span class="sxs-lookup"><span data-stu-id="6eb65-122">Example</span></span>  

 <span data-ttu-id="6eb65-123">此代码示例通过引用之前生成的程序集和 .netmodule 来生成程序集 csman_an_assembly。</span><span class="sxs-lookup"><span data-stu-id="6eb65-123">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="6eb65-124">已调用 An_Internal_Class.Test\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6eb65-124">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="6eb65-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6eb65-125">See also</span></span>

- [<span data-ttu-id="6eb65-126">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="6eb65-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6eb65-127">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="6eb65-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
