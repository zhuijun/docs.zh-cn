---
title: virtualCERCall MDA
description: 查看 virtualCERCall 托管调试助手（MDA），如果 CER 包含对无法自动准备的虚方法的调用，则会调用此方法。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: fab0686b1c7d2fbb1485f6e4b82d008495a553cd
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803555"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="6597d-103">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="6597d-103">virtualCERCall MDA</span></span>
<span data-ttu-id="6597d-104">`virtualCERCall` 托管调试助手 (MDA) 作为警告被激活，指示某个受约束的执行区域 (CER) 调用关系图中的调用站点引用了虚拟目标，即对非最终虚拟方法的虚拟调用或使用接口的调用。</span><span class="sxs-lookup"><span data-stu-id="6597d-104">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="6597d-105">公共语言运行时 (CLR) 无法只凭中间语言和元数据分析预测这些调用的目标方法。</span><span class="sxs-lookup"><span data-stu-id="6597d-105">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="6597d-106">因此无法将调用树准备为 CER 关系图的一部分，且无法阻止该子树中的线程中止。</span><span class="sxs-lookup"><span data-stu-id="6597d-106">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="6597d-107">此 MDA 警告以下情况：一旦计算调用目标所需的附加信息在运行时已知，则可能需要使用对 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> 方法的显式调用来扩展 CER。</span><span class="sxs-lookup"><span data-stu-id="6597d-107">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6597d-108">症状</span><span class="sxs-lookup"><span data-stu-id="6597d-108">Symptoms</span></span>  
 <span data-ttu-id="6597d-109">线程中止或应用程序域卸载时 CER 不运行。</span><span class="sxs-lookup"><span data-stu-id="6597d-109">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6597d-110">原因</span><span class="sxs-lookup"><span data-stu-id="6597d-110">Cause</span></span>  
 <span data-ttu-id="6597d-111">CER 包含对无法自动准备的虚拟方法的调用。</span><span class="sxs-lookup"><span data-stu-id="6597d-111">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6597d-112">解决方法</span><span class="sxs-lookup"><span data-stu-id="6597d-112">Resolution</span></span>  
 <span data-ttu-id="6597d-113">为该虚拟方法调用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>。</span><span class="sxs-lookup"><span data-stu-id="6597d-113">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6597d-114">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="6597d-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="6597d-115">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="6597d-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6597d-116">Output</span><span class="sxs-lookup"><span data-stu-id="6597d-116">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="6597d-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="6597d-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6597d-118">示例</span><span class="sxs-lookup"><span data-stu-id="6597d-118">Example</span></span>  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6597d-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="6597d-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6597d-120">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="6597d-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6597d-121">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="6597d-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
