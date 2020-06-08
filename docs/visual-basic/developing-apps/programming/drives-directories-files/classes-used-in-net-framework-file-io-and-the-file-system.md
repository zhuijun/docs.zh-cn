---
title: 在 .NET Framework 文件 I/O 和文件系统中使用的类
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: 2c696d5b8c83ae55caf61e4710630ad1e34c088d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401766"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="98225-102">在 .NET Framework 文件 I/O 和文件系统中使用的类 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98225-102">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>

<span data-ttu-id="98225-103">下列各表列出了常用于 .NET Framework 文件 I/O 的类，将这些类分为文件 I/O 类、用于创建流的类和用于读取和写入流的类。</span><span class="sxs-lookup"><span data-stu-id="98225-103">The following tables list the classes commonly used for .NET Framework file I/O, categorized into file I/O classes, classes used for creating streams, and classes used to read and write to streams.</span></span>  
  
<span data-ttu-id="98225-104">要获取更完整的列表，请参阅[类库概述](../../../../standard/class-library-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="98225-104">For a more comprehensive listing, see [Class Library Overview](../../../../standard/class-library-overview.md).</span></span>  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a><span data-ttu-id="98225-105">用于文件、驱动器和目录的基本 I/O 类</span><span class="sxs-lookup"><span data-stu-id="98225-105">Basic I/O Classes for Files, Drives, and Directories</span></span>  

 <span data-ttu-id="98225-106">下表列出并说明了用于文件 I/O 的主类。</span><span class="sxs-lookup"><span data-stu-id="98225-106">The following table lists and describes the main classes used for file I/O.</span></span>  
  
|<span data-ttu-id="98225-107">类</span><span class="sxs-lookup"><span data-stu-id="98225-107">Class</span></span>|<span data-ttu-id="98225-108">说明</span><span class="sxs-lookup"><span data-stu-id="98225-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|<span data-ttu-id="98225-109">提供用于创建、移动和枚举目录和子目录的静态方法。</span><span class="sxs-lookup"><span data-stu-id="98225-109">Provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|<span data-ttu-id="98225-110">提供用于创建、移动和枚举目录和子目录的实例方法。</span><span class="sxs-lookup"><span data-stu-id="98225-110">Provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|<span data-ttu-id="98225-111">提供通过驱动器用于创建、移动和枚举的实例方法。</span><span class="sxs-lookup"><span data-stu-id="98225-111">Provides instance methods for creating, moving, and enumerating through drives.</span></span>|  
|<xref:System.IO.File?displayProperty=nameWithType>|<span data-ttu-id="98225-112">提供用于创建、复制、删除、移动和打开文件的静态方法，并可帮助创建 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="98225-112">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|<span data-ttu-id="98225-113">定义文件的读取、写入或读/写访问权限的常量。</span><span class="sxs-lookup"><span data-stu-id="98225-113">Defines constants for read, write, or read/write access to a file.</span></span>|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|<span data-ttu-id="98225-114">提供文件和目录的属性，例如 `Archive`、`Hidden` 和 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="98225-114">Provides attributes for files and directories such as `Archive`, `Hidden`, and `ReadOnly`.</span></span>|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|<span data-ttu-id="98225-115">提供用于创建、复制、删除、移动和打开文件的静态方法，并可帮助创建 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="98225-115">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|<span data-ttu-id="98225-116">控制打开文件的方式。</span><span class="sxs-lookup"><span data-stu-id="98225-116">Controls how a file is opened.</span></span> <span data-ttu-id="98225-117">在多个 `FileStream` 和 `IsolatedStorageFileStream` 的构造函数中指定此参数，此参数用于 <xref:System.IO.File> 和 <xref:System.IO.FileInfo> 的 `Open` 方法。</span><span class="sxs-lookup"><span data-stu-id="98225-117">This parameter is specified in many of the constructors for `FileStream` and `IsolatedStorageFileStream`, and for the `Open` methods of <xref:System.IO.File> and <xref:System.IO.FileInfo>.</span></span>|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|<span data-ttu-id="98225-118">定义用于控制其他文件流可以对同一文件进行何种类型的访问的常量。</span><span class="sxs-lookup"><span data-stu-id="98225-118">Defines constants for controlling the type of access other file streams can have to the same file.</span></span>|  
|<xref:System.IO.Path?displayProperty=nameWithType>|<span data-ttu-id="98225-119">提供用于处理目录字符串的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="98225-119">Provides methods and properties for processing directory strings.</span></span>|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|<span data-ttu-id="98225-120">通过定义 <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> 和 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> 权限来控制对文件和文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="98225-120">Controls the access of files and folders by defining <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> and <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> permissions.</span></span>|  
  
## <a name="classes-used-to-create-streams"></a><span data-ttu-id="98225-121">用于创建流的类</span><span class="sxs-lookup"><span data-stu-id="98225-121">Classes Used to Create Streams</span></span>  

 <span data-ttu-id="98225-122">下表列出并说明了用于创建流的主类。</span><span class="sxs-lookup"><span data-stu-id="98225-122">The following table lists and describes the main classes used to create streams.</span></span>  
  
|<span data-ttu-id="98225-123">类</span><span class="sxs-lookup"><span data-stu-id="98225-123">Class</span></span>|<span data-ttu-id="98225-124">说明</span><span class="sxs-lookup"><span data-stu-id="98225-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|<span data-ttu-id="98225-125">将缓冲层添加到另一个流上的读取和写入操作。</span><span class="sxs-lookup"><span data-stu-id="98225-125">Adds a buffering layer to read and write operations on another stream.</span></span>|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<span data-ttu-id="98225-126">支持通过文件的 <xref:System.IO.FileStream.Seek%2A> 方法对其进行随机访问。</span><span class="sxs-lookup"><span data-stu-id="98225-126">Supports random access to files through its <xref:System.IO.FileStream.Seek%2A> method.</span></span> <span data-ttu-id="98225-127">默认情况下 <xref:System.IO.FileStream> 同步打开文件，但也支持异步操作。</span><span class="sxs-lookup"><span data-stu-id="98225-127"><xref:System.IO.FileStream> opens files synchronously by default but also supports asynchronous operation.</span></span>|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|<span data-ttu-id="98225-128">创建一个流，其后备存储为内存而非文件。</span><span class="sxs-lookup"><span data-stu-id="98225-128">Creates a stream whose backing store is memory, rather than a file.</span></span>|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|<span data-ttu-id="98225-129">为网络访问提供数据的基础流。</span><span class="sxs-lookup"><span data-stu-id="98225-129">Provides the underlying stream of data for network access.</span></span>|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|<span data-ttu-id="98225-130">定义将数据流链接到加密转换的流。</span><span class="sxs-lookup"><span data-stu-id="98225-130">Defines a stream that links data streams to cryptographic transformations.</span></span>|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a><span data-ttu-id="98225-131">用于读取和写入到流的类</span><span class="sxs-lookup"><span data-stu-id="98225-131">Classes Used to Read from and Write to Streams</span></span>  

 <span data-ttu-id="98225-132">下表显示使用流读取和写入到文件的特定类。</span><span class="sxs-lookup"><span data-stu-id="98225-132">The following table shows the specific classes used for reading from and writing to files with streams.</span></span>  
  
|<span data-ttu-id="98225-133">**类**</span><span class="sxs-lookup"><span data-stu-id="98225-133">**Class**</span></span>|<span data-ttu-id="98225-134">**说明**</span><span class="sxs-lookup"><span data-stu-id="98225-134">**Description**</span></span>|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|<span data-ttu-id="98225-135">从 <xref:System.IO.FileStream> 读取编码字符串和基元数据类型。</span><span class="sxs-lookup"><span data-stu-id="98225-135">Reads encoded strings and primitive data types from a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|<span data-ttu-id="98225-136">将编码字符串和基元数据类型写入 <xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="98225-136">Writes encoded strings and primitive data types to a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|<span data-ttu-id="98225-137">从 <xref:System.IO.FileStream> 读取字符，使用 <xref:System.IO.StreamReader.CurrentEncoding%2A> 将字符转换为字节，或将字节转换为字符。</span><span class="sxs-lookup"><span data-stu-id="98225-137">Reads characters from a <xref:System.IO.FileStream>, using <xref:System.IO.StreamReader.CurrentEncoding%2A> to convert characters to and from bytes.</span></span> <span data-ttu-id="98225-138">对于给定的流，<xref:System.IO.StreamReader> 的构造函数基于特定 <xref:System.IO.StreamReader.CurrentEncoding%2A> 报头的状态，尝试确定正确的 <xref:System.IO.StreamReader.CurrentEncoding%2A>，如字节顺序标记。</span><span class="sxs-lookup"><span data-stu-id="98225-138"><xref:System.IO.StreamReader> has a constructor that attempts to ascertain the correct <xref:System.IO.StreamReader.CurrentEncoding%2A> for a given stream, based on the presence of a <xref:System.IO.StreamReader.CurrentEncoding%2A>-specific preamble, such as a byte order mark.</span></span>|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|<span data-ttu-id="98225-139">将字符写入 `FileStream`，使用 <xref:System.IO.StreamWriter.Encoding%2A> 将字符转换为字节。</span><span class="sxs-lookup"><span data-stu-id="98225-139">Writes characters to a `FileStream`, using <xref:System.IO.StreamWriter.Encoding%2A> to convert characters to bytes.</span></span>|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|<span data-ttu-id="98225-140">从 `String` 读取字符。</span><span class="sxs-lookup"><span data-stu-id="98225-140">Reads characters from a `String`.</span></span> <span data-ttu-id="98225-141">输出可以是任意编码中的流或 `String`。</span><span class="sxs-lookup"><span data-stu-id="98225-141">Output can be either a stream in any encoding or a `String`.</span></span>|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|<span data-ttu-id="98225-142">将字符写入 `String`。</span><span class="sxs-lookup"><span data-stu-id="98225-142">Writes characters to a `String`.</span></span> <span data-ttu-id="98225-143">输出可以是任意编码中的流或 `String`。</span><span class="sxs-lookup"><span data-stu-id="98225-143">Output can be either a stream in any encoding or a `String`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98225-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98225-144">See also</span></span>

- [<span data-ttu-id="98225-145">撰写流</span><span class="sxs-lookup"><span data-stu-id="98225-145">Composing Streams</span></span>](../../../../standard/io/composing-streams.md)
- [<span data-ttu-id="98225-146">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="98225-146">File and Stream I/O</span></span>](../../../../standard/io/index.md)
- [<span data-ttu-id="98225-147">异步文件 I/O</span><span class="sxs-lookup"><span data-stu-id="98225-147">Asynchronous File I/O</span></span>](../../../../standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="98225-148">.NET Framework 文件 I/O 和文件系统基础知识 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98225-148">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](basics-of-net-framework-file-io-and-the-file-system.md)
