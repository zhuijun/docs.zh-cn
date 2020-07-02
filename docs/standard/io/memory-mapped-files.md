---
title: 内存映射文件
description: 浏览 .NET 中的内存映射文件，这些文件包含虚拟内存中的文件内容，并允许应用程序直接写入内存来修改文件。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: db63c15357b0670c55b1174b91b02e2f49a0c4c1
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661974"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="eda88-103">内存映射文件</span><span class="sxs-lookup"><span data-stu-id="eda88-103">Memory-Mapped Files</span></span>
<span data-ttu-id="eda88-104">内存映射文件包含虚拟内存中文件的内容。</span><span class="sxs-lookup"><span data-stu-id="eda88-104">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="eda88-105">借助文件和内存空间之间的这种映射，应用（包括多个进程）可以直接对内存执行读取和写入操作，从而修改文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-105">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="eda88-106">从 .NET Framework 4 开始，可以使用托管代码访问内存映射文件，就像本机 Windows 函数访问内存映射文件（如[管理内存映射文件](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10))所述）一样。</span><span class="sxs-lookup"><span data-stu-id="eda88-106">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="eda88-107">内存映射文件分为两种类型：</span><span class="sxs-lookup"><span data-stu-id="eda88-107">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="eda88-108">持久化内存映射文件</span><span class="sxs-lookup"><span data-stu-id="eda88-108">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="eda88-109">持久化文件是与磁盘上的源文件相关联的内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-109">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="eda88-110">当最后一个进程处理完文件时，数据保存到磁盘上的源文件中。</span><span class="sxs-lookup"><span data-stu-id="eda88-110">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="eda88-111">此类内存映射文件适用于处理非常大的源文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-111">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="eda88-112">非持久化内存映射文件</span><span class="sxs-lookup"><span data-stu-id="eda88-112">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="eda88-113">非持久化文件是不与磁盘上的文件相关联的内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-113">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="eda88-114">当最后一个进程处理完文件时，数据会丢失，且文件被垃圾回收器回收。</span><span class="sxs-lookup"><span data-stu-id="eda88-114">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="eda88-115">此类文件适合创建共享内存，以进行进程内通信 (IPC)。</span><span class="sxs-lookup"><span data-stu-id="eda88-115">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="eda88-116">进程、视图和管理内存</span><span class="sxs-lookup"><span data-stu-id="eda88-116">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="eda88-117">可以跨多个进程共享内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-117">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="eda88-118">进程可以映射到相同的内存映射文件，只需使用文件创建进程分配的通用名称即可。</span><span class="sxs-lookup"><span data-stu-id="eda88-118">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="eda88-119">必须创建整个或部分内存映射文件的视图，才能使用内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-119">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="eda88-120">还可以为内存映射文件的同一部分创建多个视图，从而创建并发内存。</span><span class="sxs-lookup"><span data-stu-id="eda88-120">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="eda88-121">若要让两个视图一直处于并发状态，必须通过同一个内存映射文件创建它们。</span><span class="sxs-lookup"><span data-stu-id="eda88-121">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="eda88-122">如果文件大于可用于内存映射的应用逻辑内存空间（在 32 位计算机中为 2GB），可能也有必要使用多个视图。</span><span class="sxs-lookup"><span data-stu-id="eda88-122">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="eda88-123">视图分为以下两种类型：流访问视图和随机访问视图。</span><span class="sxs-lookup"><span data-stu-id="eda88-123">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="eda88-124">使用流访问视图，可以顺序访问文件；建议对非持久化文件和 IPC 使用这种类型。</span><span class="sxs-lookup"><span data-stu-id="eda88-124">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="eda88-125">随机访问视图是处理持久化文件的首选类型。</span><span class="sxs-lookup"><span data-stu-id="eda88-125">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="eda88-126">由于内存映射文件是通过操作系统的内存管理程序进行访问，因此文件会被自动分区到很多页面，并根据需要进行访问。</span><span class="sxs-lookup"><span data-stu-id="eda88-126">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="eda88-127">无需自行处理内存管理。</span><span class="sxs-lookup"><span data-stu-id="eda88-127">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="eda88-128">下图展示了多个进程如何同时对同一个内存映射文件有多个重叠视图。</span><span class="sxs-lookup"><span data-stu-id="eda88-128">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="eda88-129">下图显示了内存映射文件的多个重叠视图：</span><span class="sxs-lookup"><span data-stu-id="eda88-129">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![显示内存映射文件的视图的屏幕截图。](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="eda88-131">使用内存映射文件编程</span><span class="sxs-lookup"><span data-stu-id="eda88-131">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="eda88-132">下表列出了与使用内存映射文件对象及其成员相关的指南。</span><span class="sxs-lookup"><span data-stu-id="eda88-132">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="eda88-133">任务</span><span class="sxs-lookup"><span data-stu-id="eda88-133">Task</span></span>|<span data-ttu-id="eda88-134">要使用的方法或属性</span><span class="sxs-lookup"><span data-stu-id="eda88-134">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="eda88-135">从磁盘上的文件获取表示持久化内存映射文件的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 对象。</span><span class="sxs-lookup"><span data-stu-id="eda88-135">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="eda88-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="eda88-137">获取表示非持久化内存映射文件的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 对象（未与磁盘上的文件关联）。</span><span class="sxs-lookup"><span data-stu-id="eda88-137">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="eda88-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="eda88-139">- 或 -</span><span class="sxs-lookup"><span data-stu-id="eda88-139">- or -</span></span><br /><br /> <span data-ttu-id="eda88-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="eda88-141">获取现有内存映射文件（持久化或非持久化）的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 对象。</span><span class="sxs-lookup"><span data-stu-id="eda88-141">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="eda88-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="eda88-143">获取内存映射文件的顺序访问视图的 <xref:System.IO.UnmanagedMemoryStream> 对象。</span><span class="sxs-lookup"><span data-stu-id="eda88-143">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="eda88-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="eda88-145">获取内存映射文件的随机访问视图的 <xref:System.IO.UnmanagedMemoryAccessor> 对象。</span><span class="sxs-lookup"><span data-stu-id="eda88-145">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="eda88-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="eda88-147">获取要与非托管代码结合使用的 <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> 对象。</span><span class="sxs-lookup"><span data-stu-id="eda88-147">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="eda88-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="eda88-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="eda88-149">- 或 -</span><span class="sxs-lookup"><span data-stu-id="eda88-149">- or -</span></span><br /><br /> <span data-ttu-id="eda88-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="eda88-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="eda88-151">- 或 -</span><span class="sxs-lookup"><span data-stu-id="eda88-151">- or -</span></span><br /><br /> <span data-ttu-id="eda88-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="eda88-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="eda88-153">将内存分配一直延迟到视图创建完成（仅限非持久化文件）。</span><span class="sxs-lookup"><span data-stu-id="eda88-153">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="eda88-154">（若要确定当前系统页面大小，请使用 <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> 属性。）</span><span class="sxs-lookup"><span data-stu-id="eda88-154">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="eda88-155">值为 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> 的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-155"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="eda88-156">- 或 -</span><span class="sxs-lookup"><span data-stu-id="eda88-156">- or -</span></span><br /><br /> <span data-ttu-id="eda88-157">将 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> 枚举用作参数的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-157"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="eda88-158">安全性</span><span class="sxs-lookup"><span data-stu-id="eda88-158">Security</span></span>  
 <span data-ttu-id="eda88-159">可以在创建内存映射文件时应用访问权限，具体操作是运行以下需要将 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> 枚举用作参数的方法：</span><span class="sxs-lookup"><span data-stu-id="eda88-159">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="eda88-160">若要指定打开现有内存映射文件所需的访问权限，可以运行需要将 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> 用作参数的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-160">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="eda88-161">另外，还可以添加包含预定义访问规则的 <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> 对象。</span><span class="sxs-lookup"><span data-stu-id="eda88-161">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="eda88-162">若要将新的或更改后的访问规则应用于内存映射文件，请使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-162">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="eda88-163">若要从现有文件检索访问或审核规则，请使用 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="eda88-163">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="eda88-164">示例</span><span class="sxs-lookup"><span data-stu-id="eda88-164">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="eda88-165">持久化内存映射文件</span><span class="sxs-lookup"><span data-stu-id="eda88-165">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="eda88-166"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> 方法通过磁盘上的现有文件创建内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-166">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="eda88-167">下面的示例为极大文件的一部分创建内存映射视图，并控制其中一部分。</span><span class="sxs-lookup"><span data-stu-id="eda88-167">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="eda88-168">下面的示例为另一个进程打开相同的内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-168">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="eda88-169">非持久化内存映射文件</span><span class="sxs-lookup"><span data-stu-id="eda88-169">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="eda88-170"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> 和 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> 方法创建未映射到磁盘上现有文件的内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-170">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="eda88-171">下面的示例包含三个独立进程（控制台应用），以将布尔值写入内存映射文件。</span><span class="sxs-lookup"><span data-stu-id="eda88-171">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="eda88-172">各操作按下面的顺序发生：</span><span class="sxs-lookup"><span data-stu-id="eda88-172">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="eda88-173">`Process A` 创建内存映射文件，并向其中写入值。</span><span class="sxs-lookup"><span data-stu-id="eda88-173">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="eda88-174">`Process B` 打开内存映射文件，并向其中写入值。</span><span class="sxs-lookup"><span data-stu-id="eda88-174">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="eda88-175">`Process C` 打开内存映射文件，并向其中写入值。</span><span class="sxs-lookup"><span data-stu-id="eda88-175">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="eda88-176">`Process A` 读取并显示内存映射文件中的值。</span><span class="sxs-lookup"><span data-stu-id="eda88-176">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="eda88-177">在 `Process A` 处理完内存映射文件后，此文件立即被垃圾回收器回收。</span><span class="sxs-lookup"><span data-stu-id="eda88-177">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="eda88-178">若要运行此示例，请按照以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="eda88-178">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="eda88-179">编译应用并打开三个命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="eda88-179">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="eda88-180">在第一个命令提示符窗口中，运行 `Process A`。</span><span class="sxs-lookup"><span data-stu-id="eda88-180">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="eda88-181">在第二个命令提示符窗口中，运行 `Process B`。</span><span class="sxs-lookup"><span data-stu-id="eda88-181">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="eda88-182">返回到 `Process A`，再按 Enter。</span><span class="sxs-lookup"><span data-stu-id="eda88-182">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="eda88-183">在第三个命令提示符窗口中，运行 `Process C`。</span><span class="sxs-lookup"><span data-stu-id="eda88-183">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="eda88-184">返回到 `Process A`，再按 Enter。</span><span class="sxs-lookup"><span data-stu-id="eda88-184">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="eda88-185">`Process A` 的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="eda88-185">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="eda88-186">**Process A**</span><span class="sxs-lookup"><span data-stu-id="eda88-186">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="eda88-187">**Process B**</span><span class="sxs-lookup"><span data-stu-id="eda88-187">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="eda88-188">**Process C**</span><span class="sxs-lookup"><span data-stu-id="eda88-188">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="eda88-189">请参阅</span><span class="sxs-lookup"><span data-stu-id="eda88-189">See also</span></span>

- [<span data-ttu-id="eda88-190">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="eda88-190">File and Stream I/O</span></span>](index.md)
