---
title: 如何：从 COM 引用 .NET 类型
description: 从 COM 引用 .NET 类型。 VB 客户端可以在对象浏览器中查看 .NET 对象，但 C++ 客户端必须使用 \#import 指令引用 TLB 文件。
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: f8d052c7b9bac9c4bab61ab1950e9e89a7c73912
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618956"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="fc68b-104">如何：从 COM 引用 .NET 类型</span><span class="sxs-lookup"><span data-stu-id="fc68b-104">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="fc68b-105">从客户端和服务器代码的角度看，COM 和 .NET Framework 之间的区别在很大程度上是不可见的。</span><span class="sxs-lookup"><span data-stu-id="fc68b-105">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="fc68b-106">Microsoft Visual Basic 客户端可在对象浏览器中查看 .NET 对象，这将公开对象方法和语法、属性和字段，正如任何其他 COM 对象那样。</span><span class="sxs-lookup"><span data-stu-id="fc68b-106">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="fc68b-107">尽管使用相同的工具将元数据导出到 COM 类型库，导入类型库的过程对于 C++ 客户端来说稍微复杂一些。</span><span class="sxs-lookup"><span data-stu-id="fc68b-107">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="fc68b-108">要从非托管 C++ 客户端引用 .NET 对象成员，通过“#import”指令引用 TLB 文件（使用 Tlbexp.exe 生成）。</span><span class="sxs-lookup"><span data-stu-id="fc68b-108">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="fc68b-109">从 C++ 引用类型库时，必须指定“raw_interfaces_only”选项或在基类库 Mscorlib.tlb 中导入定义。</span><span class="sxs-lookup"><span data-stu-id="fc68b-109">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="fc68b-110">导入库</span><span class="sxs-lookup"><span data-stu-id="fc68b-110">To import a library</span></span>  
  
- <span data-ttu-id="fc68b-111">在“#import”指令中指定“raw_interfaces_only”选项。</span><span class="sxs-lookup"><span data-stu-id="fc68b-111">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="fc68b-112">例如：</span><span class="sxs-lookup"><span data-stu-id="fc68b-112">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="fc68b-113">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="fc68b-113">-or-</span></span>  
  
- <span data-ttu-id="fc68b-114">包括用于 Mscorlib.tlb 的 #import 指令。</span><span class="sxs-lookup"><span data-stu-id="fc68b-114">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="fc68b-115">例如：</span><span class="sxs-lookup"><span data-stu-id="fc68b-115">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fc68b-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="fc68b-116">See also</span></span>

- [<span data-ttu-id="fc68b-117">向 COM 公开 .NET Framework 组件</span><span class="sxs-lookup"><span data-stu-id="fc68b-117">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="fc68b-118">向 COM 注册程序集</span><span class="sxs-lookup"><span data-stu-id="fc68b-118">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="fc68b-119">[调用 .NET 对象](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fc68b-119">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="fc68b-120">[为 COM 访问部署应用程序](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fc68b-120">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
