---
title: 封送 MDA
description: 查看封送托管调试助手（MDA），如果 CLR 为方法参数或结构字段设置封送处理信息，则会调用此方法。
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: 77811c526d1770b91b14aa1199dfc7b3177e6c59
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051150"
---
# <a name="marshaling-mda"></a><span data-ttu-id="fe4ed-103">封送 MDA</span><span class="sxs-lookup"><span data-stu-id="fe4ed-103">marshaling MDA</span></span>
<span data-ttu-id="fe4ed-104">当 CLR 为方法参数或结构的字段设置封送处理信息时，将激活 `marshaling` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="fe4ed-104">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="fe4ed-105">此 MDA 不适合 JIT 编译的程序集。</span><span class="sxs-lookup"><span data-stu-id="fe4ed-105">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fe4ed-106">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="fe4ed-106">Effect on the Runtime</span></span>  
 <span data-ttu-id="fe4ed-107">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="fe4ed-107">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fe4ed-108">输出</span><span class="sxs-lookup"><span data-stu-id="fe4ed-108">Output</span></span>  
 <span data-ttu-id="fe4ed-109">此 MDA 显示托管和非托管上下文中参数或字段的类型，以及包含此类型的结构或方法。</span><span class="sxs-lookup"><span data-stu-id="fe4ed-109">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="fe4ed-110">以下是字段输出的示例：</span><span class="sxs-lookup"><span data-stu-id="fe4ed-110">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="fe4ed-111">配置</span><span class="sxs-lookup"><span data-stu-id="fe4ed-111">Configuration</span></span>  
 <span data-ttu-id="fe4ed-112">MDA 配置允许你基于所涉及的字段或方法名称，筛选报告的封送处理信息。</span><span class="sxs-lookup"><span data-stu-id="fe4ed-112">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="fe4ed-113">以下示例演示如何使用 `methodFilter``fieldFilter` 和 `match` 元素指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="fe4ed-113">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="fe4ed-114">`name`将属性设置为星号（ \* ）可匹配所有内容。</span><span class="sxs-lookup"><span data-stu-id="fe4ed-114">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe4ed-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="fe4ed-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="fe4ed-116">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="fe4ed-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="fe4ed-117">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="fe4ed-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
