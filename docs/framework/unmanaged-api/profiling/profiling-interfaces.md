---
title: 分析接口
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: f073794b4fdf89f289b70fed9967ee37b5f4e133
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494028"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="f833b-102">分析接口</span><span class="sxs-lookup"><span data-stu-id="f833b-102">Profiling Interfaces</span></span>
<span data-ttu-id="f833b-103">本节描述允许对公共语言运行时 (CLR) 正在执行的程序进行分析的非托管接口。</span><span class="sxs-lookup"><span data-stu-id="f833b-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f833b-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="f833b-104">In This Section</span></span>  
 [<span data-ttu-id="f833b-105">ICLRProfiling 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-105">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="f833b-106">提供[AttachProfiler](iclrprofiling-attachprofiler-method.md)方法，该方法可使探查器附加到正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="f833b-106">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="f833b-107">ICorProfilerAssemblyReferenceProvider 方法</span><span class="sxs-lookup"><span data-stu-id="f833b-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="f833b-108">启用探查器以通知程序集引用的 CLR，探查器将在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回调中添加这些引用。</span><span class="sxs-lookup"><span data-stu-id="f833b-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="f833b-109">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-109">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="f833b-110">提供 CLR 在代码探查器订阅的事件发生时用来通知该探查器的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="f833b-111">ICorProfilerCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-111">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="f833b-112">使用 NET Framework 2.0 及更高版本支持的回调扩展 `ICorProfilerCallback` 接口。</span><span class="sxs-lookup"><span data-stu-id="f833b-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="f833b-113">ICorProfilerCallback3 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-113">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="f833b-114">提供 CLR 用于将附加和分离状态信息传递给探查器的回调方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="f833b-115">ICorProfilerCallback4 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-115">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="f833b-116">提供 CLR 用于将信息传递给探查器的回调方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="f833b-117">ICorProfilerCallback5 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-117">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="f833b-118">提供用于标识由垃圾回收根引用的对象的传递闭包的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="f833b-119">ICorProfilerCallback6 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-119">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="f833b-120">提供 CLR 用于通知探查器正在加载程序集的回调方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="f833b-121">ICorProfilerCallback7 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-121">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="f833b-122">提供一个回调方法，公共语言运行时使用该方法通知探查器已更新与内存中模块关联的符号流。</span><span class="sxs-lookup"><span data-stu-id="f833b-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="f833b-123">ICorProfilerCallback8 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="f833b-124">提供回调方法，公共语言运行时使用该方法通知探查器已开始和完成动态方法的 JIT 编译。</span><span class="sxs-lookup"><span data-stu-id="f833b-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="f833b-125">ICorProfilerCallback9 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-125">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="f833b-126">提供一个回调方法，公共语言运行时使用该方法通知探查器动态方法是经过垃圾回收并随后卸载。</span><span class="sxs-lookup"><span data-stu-id="f833b-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="f833b-127">ICorProfilerFunctionControl 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-127">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="f833b-128">提供允许代码探查器与 CLR 进行通信的方法，从而在重新编译特定方法时控制 JIT 探查器应生成代码的方式。</span><span class="sxs-lookup"><span data-stu-id="f833b-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="f833b-129">ICorProfilerFunctionEnum 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-129">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="f833b-130">提供按顺序循环访问 CLR 中函数集合的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="f833b-131">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="f833b-132">提供代码探查器用于与 CLR 通信以控制事件监视及请求信息的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="f833b-133">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-133">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="f833b-134">使用 NET Framework 2.0 及更高版本支持的方法扩展 `ICorProfilerInfo` 接口。</span><span class="sxs-lookup"><span data-stu-id="f833b-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="f833b-135">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-135">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="f833b-136">`ICorProfilerInfo2`用 .NET Framework 4 及更高版本中支持的方法扩展接口。</span><span class="sxs-lookup"><span data-stu-id="f833b-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="f833b-137">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-137">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="f833b-138">提供一些方法，代码探查器可以使用这些方法与 CLR 通信，从而控制事件监视并请求信息。</span><span class="sxs-lookup"><span data-stu-id="f833b-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="f833b-139">ICorProfilerInfo5 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="f833b-140">提供代码探查器用于与 CLR 通信以控制事件监视的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="f833b-141">ICorProfilerInfo6 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-141">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="f833b-142">为属于给定的 NGen 模块并在给定方法的主体中内联的所有方法提供一个枚举器。</span><span class="sxs-lookup"><span data-stu-id="f833b-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="f833b-143">ICorProfilerInfo7 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-143">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="f833b-144">提供了一种方法，用于将新定义的元数据应用于模块，并提供对内存中符号流的访问。</span><span class="sxs-lookup"><span data-stu-id="f833b-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="f833b-145">ICorProfilerModuleEnum 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-145">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="f833b-146">提供用于按顺序循环访问应用程序或探查器加载的模块集合的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="f833b-147">ICorProfilerObjectEnum 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-147">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="f833b-148">提供按顺序循环访问[ngen.exe （本机映像生成器）](../../tools/ngen-exe-native-image-generator.md)生成的冻结对象的集合的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="f833b-149">ICorProfilerThreadEnum 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-149">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="f833b-150">提供按顺序循环访问 CLR 中线程集合的方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="f833b-151">IMethodMalloc 接口</span><span class="sxs-lookup"><span data-stu-id="f833b-151">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="f833b-152">为新的 Microsoft 中间语言（MSIL）函数体提供分配内存的[分配](imethodmalloc-alloc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f833b-152">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f833b-153">相关章节</span><span class="sxs-lookup"><span data-stu-id="f833b-153">Related Sections</span></span>  
 [<span data-ttu-id="f833b-154">分析概述</span><span class="sxs-lookup"><span data-stu-id="f833b-154">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="f833b-155">分析全局静态函数</span><span class="sxs-lookup"><span data-stu-id="f833b-155">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="f833b-156">分析枚举</span><span class="sxs-lookup"><span data-stu-id="f833b-156">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="f833b-157">分析结构</span><span class="sxs-lookup"><span data-stu-id="f833b-157">Profiling Structures</span></span>](profiling-structures.md)
