---
title: 如何：从类型库生成互操作程序集
description: 从类型库生成互操作程序集。 使用类型库导入程序 (Tlbimp.exe) 将组件类和接口从 COM 类型库转换为元数据。
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 6f54875d6aadb1da18cf25a1bec0a0e451f4a24c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619554"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="de3d0-104">如何：从类型库生成互操作程序集</span><span class="sxs-lookup"><span data-stu-id="de3d0-104">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="de3d0-105">[类型库导入程序 (Tlbexp.exe)](../tools/tlbimp-exe-type-library-importer.md) 是一个命令行工具，可将 COM 类型库中包含的组件类和接口转换为元数据。</span><span class="sxs-lookup"><span data-stu-id="de3d0-105">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="de3d0-106">此工具会自动为类型信息创建互操作程序集和命名空间。</span><span class="sxs-lookup"><span data-stu-id="de3d0-106">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="de3d0-107">类的元数据可用之后，托管客户端可创建 COM 类型的实例并调用其方法，就像它是 .NET 实例一样。</span><span class="sxs-lookup"><span data-stu-id="de3d0-107">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="de3d0-108">Tlbimp.exe 同时将整个类型库转换为元数据，而且无法生成类型库中定义的类型子集的类型信息。</span><span class="sxs-lookup"><span data-stu-id="de3d0-108">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="de3d0-109">从类型库生成的互操作程序集</span><span class="sxs-lookup"><span data-stu-id="de3d0-109">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="de3d0-110">使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="de3d0-110">Use the following command:</span></span>  
  
     <span data-ttu-id="de3d0-111">tlbimp \<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="de3d0-111">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="de3d0-112">添加 /out: 开关会生成具有已更改名称的互操作程序集，如 LOANLib.dll。</span><span class="sxs-lookup"><span data-stu-id="de3d0-112">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="de3d0-113">更改互操作程序集名称有助于将它与原始 COM DLL 区分开来，并防止因为具有重复名称而可能发生的问题。</span><span class="sxs-lookup"><span data-stu-id="de3d0-113">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de3d0-114">示例</span><span class="sxs-lookup"><span data-stu-id="de3d0-114">Example</span></span>  
 <span data-ttu-id="de3d0-115">以下命令在 `Loanlib` 命名空间中生成 Loanlib.dll 程序集。</span><span class="sxs-lookup"><span data-stu-id="de3d0-115">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="de3d0-116">以下命令生成具有已更改名称的互操作程序集 (LOANLib.dll)。</span><span class="sxs-lookup"><span data-stu-id="de3d0-116">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="de3d0-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="de3d0-117">See also</span></span>

- [<span data-ttu-id="de3d0-118">将类型库作为程序集导入</span><span class="sxs-lookup"><span data-stu-id="de3d0-118">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="de3d0-119">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="de3d0-119">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
