---
title: 诊断符号存储区接口
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 34eee8c05e1c356d4c431245c6837bd2b3a89b32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504467"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="e72c1-102">诊断符号存储区接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="e72c1-103">本主题介绍了一些非托管接口，这些接口允许编译器生成符号信息以供调试器使用。</span><span class="sxs-lookup"><span data-stu-id="e72c1-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e72c1-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="e72c1-104">In This Section</span></span>  
 [<span data-ttu-id="e72c1-105">IBindingDisplay 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="e72c1-106">提供显示有关正在运行的应用程序的当前绑定信息的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="e72c1-107">IDebugAutoAttach 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="e72c1-108">定义服务器调用的调试器自动附加的接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="e72c1-109">INotifyConnection2 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="e72c1-110">声明用于注册和注销连接通知源的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="e72c1-111">INotifySink2 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="e72c1-112">声明接收器通知的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="e72c1-113">INotifySource2 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="e72c1-114">声明用于设置通知筛选器的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="e72c1-115">ISymENCUnmanagedMethod 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="e72c1-116">提供 "编辑并继续" 功能的信息。</span><span class="sxs-lookup"><span data-stu-id="e72c1-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="e72c1-117">ISymUnmanagedAsyncMethod 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="e72c1-118">此接口是[ISymUnmanagedAsyncMethodPropertiesWriter 接口](isymunmanagedasyncmethodpropertieswriter-interface.md)的读取补充。</span><span class="sxs-lookup"><span data-stu-id="e72c1-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="e72c1-119">ISymUnmanagedAsyncMethodPropertiesWriter 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="e72c1-120">允许为每个方法符号定义可选的异步方法信息。</span><span class="sxs-lookup"><span data-stu-id="e72c1-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="e72c1-121">必须使用与已打开的方法（即，在对[OpenMethod 方法](isymunmanagedwriter-openmethod-method.md)和[CloseMethod 方法](isymunmanagedwriter-closemethod-method.md)的调用之间）。</span><span class="sxs-lookup"><span data-stu-id="e72c1-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="e72c1-122">ISymUnmanagedBinder 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="e72c1-123">表示非托管代码的符号联编程序。</span><span class="sxs-lookup"><span data-stu-id="e72c1-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="e72c1-124">ISymUnmanagedBinder2 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="e72c1-125">表示非托管代码的符号联编程序，并扩展 `ISymUnmanagedBinder` 接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="e72c1-126">ISymUnmanagedBinder3 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="e72c1-127">表示非托管代码的符号联编程序，并扩展 `ISymUnmanagedBinder` 接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="e72c1-128">ISymUnmanagedConstant 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="e72c1-129">提供对非托管常数的访问。</span><span class="sxs-lookup"><span data-stu-id="e72c1-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="e72c1-130">ISymUnmanagedDispose 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="e72c1-131">释放非托管资源。</span><span class="sxs-lookup"><span data-stu-id="e72c1-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="e72c1-132">ISymUnmanagedDocument 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="e72c1-133">表示由符号存储引用的文档。</span><span class="sxs-lookup"><span data-stu-id="e72c1-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="e72c1-134">ISymUnmanagedDocumentWriter 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="e72c1-135">提供用于写入到符号存储区引用的文档的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="e72c1-136">ISymUnmanagedENCUpdate 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="e72c1-137">提供 "编辑并继续" 功能的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="e72c1-138">ISymUnmanagedMethod 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="e72c1-139">表示符号存储区中的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="e72c1-140">ISymUnmanagedNamespace 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="e72c1-141">表示命名空间。</span><span class="sxs-lookup"><span data-stu-id="e72c1-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="e72c1-142">ISymUnmanagedReader 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="e72c1-143">表示一个符号读取器，该读取器提供对符号存储区中的文档、方法和变量的访问。</span><span class="sxs-lookup"><span data-stu-id="e72c1-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="e72c1-144">ISymUnmanagedReader2 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="e72c1-145">给定方法标记和编辑和复制版本号，获取符号读取器方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="e72c1-146">ISymUnmanagedReaderSymbolSearchInfo 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="e72c1-147">提供用于获取符号搜索信息的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="e72c1-148">ISymUnmanagedScope 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="e72c1-149">表示方法中的词法范围。</span><span class="sxs-lookup"><span data-stu-id="e72c1-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="e72c1-150">ISymUnmanagedScope2 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="e72c1-151">表示方法内的词法范围，并 `ISymUnmanagedScope` 使用获取有关范围中定义的常量的信息的方法扩展接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="e72c1-152">ISymUnmanagedSourceServerModule 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="e72c1-153">提供模块的源服务器数据。</span><span class="sxs-lookup"><span data-stu-id="e72c1-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="e72c1-154">ISymUnmanagedSymbolSearchInfo 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="e72c1-155">提供获取有关搜索路径的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="e72c1-156">ISymUnmanagedVariable 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="e72c1-157">表示变量，如参数、局部变量或字段。</span><span class="sxs-lookup"><span data-stu-id="e72c1-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="e72c1-158">ISymUnmanagedWriter 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="e72c1-159">表示符号编写器，并提供定义文档、序列点、词法范围和变量的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="e72c1-160">ISymUnmanagedWriter2 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="e72c1-161">表示符号编写器，并提供定义文档、序列点、词法范围和变量的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="e72c1-162">扩展 `ISymUnmanagedWriter` 接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="e72c1-163">ISymUnmanagedWriter3 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="e72c1-164">表示符号编写器，并提供定义文档、序列点、词法范围和变量的方法。</span><span class="sxs-lookup"><span data-stu-id="e72c1-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="e72c1-165">扩展 `ISymUnmanagedWriter` 接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="e72c1-166">ISymUnmanagedWriter4 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="e72c1-167">ISymUnmanagedWriter4 接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="e72c1-168">ISymUnmanagedWriter5 接口</span><span class="sxs-lookup"><span data-stu-id="e72c1-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="e72c1-169">ISymUnmanagedWriter5 接口。</span><span class="sxs-lookup"><span data-stu-id="e72c1-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e72c1-170">相关章节</span><span class="sxs-lookup"><span data-stu-id="e72c1-170">Related Sections</span></span>  
 [<span data-ttu-id="e72c1-171">诊断符号存储区枚举</span><span class="sxs-lookup"><span data-stu-id="e72c1-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="e72c1-172">诊断符号存储区结构</span><span class="sxs-lookup"><span data-stu-id="e72c1-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="e72c1-173">调试</span><span class="sxs-lookup"><span data-stu-id="e72c1-173">Debugging</span></span>](../debugging/index.md)
