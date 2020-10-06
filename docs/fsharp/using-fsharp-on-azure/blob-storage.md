---
title: 通过 F# 实现 Azure Blob 入门
description: 通过 Azure Blob 存储将非结构化数据存储在云中。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 91aec8fc2b57c71ce4ba47d62619912af6c71e59
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756242"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="608ef-103">使用 F 开始使用 Azure Blob 存储\#</span><span class="sxs-lookup"><span data-stu-id="608ef-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="608ef-104">Azure Blob 存储是一种将非结构化数据作为对象/Blob 存储在云中的服务。</span><span class="sxs-lookup"><span data-stu-id="608ef-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="608ef-105">Blob 存储可以存储任何类型的文本或二进制数据，例如文档、媒体文件或应用程序安装程序。</span><span class="sxs-lookup"><span data-stu-id="608ef-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="608ef-106">Blob 存储也称为对象存储。</span><span class="sxs-lookup"><span data-stu-id="608ef-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="608ef-107">本文介绍如何使用 Blob 存储执行常见任务。</span><span class="sxs-lookup"><span data-stu-id="608ef-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="608ef-108">使用用于 .NET 的 Azure 存储客户端库的 F # 编写示例。</span><span class="sxs-lookup"><span data-stu-id="608ef-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="608ef-109">涉及的任务包括如何上传、列出、下载和删除 blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="608ef-110">有关 blob 存储的概念性概述，请参阅 [blob 存储的 .net 指南](/azure/storage/blobs/storage-quickstart-blobs-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="608ef-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="608ef-111">必备知识</span><span class="sxs-lookup"><span data-stu-id="608ef-111">Prerequisites</span></span>

<span data-ttu-id="608ef-112">若要使用本指南，必须先 [创建 Azure 存储帐户](/azure/storage/common/storage-account-create)。</span><span class="sxs-lookup"><span data-stu-id="608ef-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="608ef-113">还需要此帐户的存储访问密钥。</span><span class="sxs-lookup"><span data-stu-id="608ef-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="608ef-114">创建 F # 脚本并开始 F# 交互窗口</span><span class="sxs-lookup"><span data-stu-id="608ef-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="608ef-115">本文中的示例可用于 F # 应用程序或 F # 脚本。</span><span class="sxs-lookup"><span data-stu-id="608ef-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="608ef-116">若要创建 F # 脚本，请创建 `.fsx` 扩展名为的文件，例如 `blobs.fsx` f # 开发环境中的文件。</span><span class="sxs-lookup"><span data-stu-id="608ef-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="608ef-117">接下来，使用 [包管理器](package-management.md) （如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ）在 `WindowsAzure.Storage` 你的 `Microsoft.WindowsAzure.ConfigurationManager` `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` 脚本中使用指令安装和包和引用 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="608ef-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="608ef-118">添加命名空间声明</span><span class="sxs-lookup"><span data-stu-id="608ef-118">Add namespace declarations</span></span>

<span data-ttu-id="608ef-119">将下列 `open` 语句添加到 `blobs.fsx` 文件顶部：</span><span class="sxs-lookup"><span data-stu-id="608ef-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="608ef-120">获取连接字符串</span><span class="sxs-lookup"><span data-stu-id="608ef-120">Get your connection string</span></span>

<span data-ttu-id="608ef-121">对于本教程，你需要一个 Azure 存储连接字符串。</span><span class="sxs-lookup"><span data-stu-id="608ef-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="608ef-122">有关连接字符串的详细信息，请参阅 [配置存储连接字符串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="608ef-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="608ef-123">对于本教程，请在脚本中输入连接字符串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="608ef-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="608ef-124">但对于实际项目， **不建议这样做** 。</span><span class="sxs-lookup"><span data-stu-id="608ef-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="608ef-125">存储帐户密钥类似于存储帐户的根密码。</span><span class="sxs-lookup"><span data-stu-id="608ef-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="608ef-126">始终要小心保护存储帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="608ef-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="608ef-127">避免将其分发给其他用户、对其进行硬编码或将其保存在其他人可以访问的纯文本文件中。</span><span class="sxs-lookup"><span data-stu-id="608ef-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="608ef-128">如果你认为密钥可能已泄漏，你可以使用 Azure 门户重新生成密钥。</span><span class="sxs-lookup"><span data-stu-id="608ef-128">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="608ef-129">对于实际应用程序，维护存储连接字符串的最佳方式是在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="608ef-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="608ef-130">若要从配置文件中提取连接字符串，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="608ef-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="608ef-131">不一定要使用 Azure Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="608ef-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="608ef-132">你还可以使用 API，例如 .NET Framework 的 `ConfigurationManager` 类型。</span><span class="sxs-lookup"><span data-stu-id="608ef-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="608ef-133">解析连接字符串</span><span class="sxs-lookup"><span data-stu-id="608ef-133">Parse the connection string</span></span>

<span data-ttu-id="608ef-134">若要分析连接字符串，请使用：</span><span class="sxs-lookup"><span data-stu-id="608ef-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="608ef-135">这会返回一个 `CloudStorageAccount` 。</span><span class="sxs-lookup"><span data-stu-id="608ef-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="608ef-136">创建一些本地虚拟数据</span><span class="sxs-lookup"><span data-stu-id="608ef-136">Create some local dummy data</span></span>

<span data-ttu-id="608ef-137">在开始之前，请在脚本的目录中创建一些虚拟本地数据。</span><span class="sxs-lookup"><span data-stu-id="608ef-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="608ef-138">稍后上载此数据。</span><span class="sxs-lookup"><span data-stu-id="608ef-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="608ef-139">创建 Blob 服务客户端</span><span class="sxs-lookup"><span data-stu-id="608ef-139">Create the Blob service client</span></span>

<span data-ttu-id="608ef-140">`CloudBlobClient`类型使你能够检索存储在 Blob 存储中的容器和 blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="608ef-141">下面是创建服务客户端的一种方法：</span><span class="sxs-lookup"><span data-stu-id="608ef-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="608ef-142">现在，已准备好编写从 Blob 存储读取数据并将数据写入 Blob 存储的代码。</span><span class="sxs-lookup"><span data-stu-id="608ef-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="608ef-143">创建容器</span><span class="sxs-lookup"><span data-stu-id="608ef-143">Create a container</span></span>

<span data-ttu-id="608ef-144">此示例演示如何创建一个容器（如果该容器不存在）：</span><span class="sxs-lookup"><span data-stu-id="608ef-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="608ef-145">默认情况下，新容器是专用容器，意思是必须指定存储访问密钥才能从该容器下载 blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="608ef-146">如果要让容器中的文件可供所有人使用，则可以使用以下代码将容器设置为公共容器：</span><span class="sxs-lookup"><span data-stu-id="608ef-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="608ef-147">Internet 中的所有人都可以查看公共容器中的 blob，但是，仅在具有相应的帐户访问密钥或共享的访问签名时，才能修改或删除它们。</span><span class="sxs-lookup"><span data-stu-id="608ef-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="608ef-148">将 Blob 上传到容器中</span><span class="sxs-lookup"><span data-stu-id="608ef-148">Upload a blob into a container</span></span>

<span data-ttu-id="608ef-149">Azure Blob 存储支持块 Blob 和页 Blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="608ef-150">在大多数情况下，建议使用块 blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="608ef-151">要将文件上传到块 Blob，请获取容器引用，并使用它获取块 Blob 引用。</span><span class="sxs-lookup"><span data-stu-id="608ef-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="608ef-152">拥有 blob 引用后，可以通过调用方法，将任何数据流上载到该 blob `UploadFromFile` 。</span><span class="sxs-lookup"><span data-stu-id="608ef-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="608ef-153">此操作将创建 blob （如果该 blob 不存在），或者覆盖它（如果该 blob 存在）。</span><span class="sxs-lookup"><span data-stu-id="608ef-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="608ef-154">列出容器中的 blob</span><span class="sxs-lookup"><span data-stu-id="608ef-154">List the blobs in a container</span></span>

<span data-ttu-id="608ef-155">若要列出容器中的 Blob，首先需要获取容器引用。</span><span class="sxs-lookup"><span data-stu-id="608ef-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="608ef-156">然后，可以使用容器的 `ListBlobs` 方法检索其中的 blob 和/或目录。</span><span class="sxs-lookup"><span data-stu-id="608ef-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="608ef-157">若要访问返回的的丰富属性和方法集 `IListBlobItem` ，必须将其强制转换为 `CloudBlockBlob` 、 `CloudPageBlob` 或 `CloudBlobDirectory` 对象。</span><span class="sxs-lookup"><span data-stu-id="608ef-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="608ef-158">如果类型未知，可以使用类型检查来确定要将其转换为哪种类型。</span><span class="sxs-lookup"><span data-stu-id="608ef-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="608ef-159">以下代码演示了如何检索和输出 `mydata` 容器中每一项的 URI：</span><span class="sxs-lookup"><span data-stu-id="608ef-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="608ef-160">还可以在名称中命名包含路径信息的 blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="608ef-161">这会创建一个虚拟目录结构，可以像传统文件系统一样组织和遍历。</span><span class="sxs-lookup"><span data-stu-id="608ef-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="608ef-162">目录结构只是虚拟的-Blob 存储中唯一可用的资源是容器和 blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-162">The directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="608ef-163">但是，存储客户端库提供了一个 `CloudBlobDirectory` 对象来引用虚拟目录，并简化了以这种方式组织的 blob 的使用过程。</span><span class="sxs-lookup"><span data-stu-id="608ef-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="608ef-164">例如，考虑名为 `photos`的容器中包含的下面一组块 Blob：</span><span class="sxs-lookup"><span data-stu-id="608ef-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="608ef-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="608ef-165">*photo1.jpg*</span></span>\
<span data-ttu-id="608ef-166">*2015/体系结构/description.txt*</span><span class="sxs-lookup"><span data-stu-id="608ef-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="608ef-167">*2015/体系结构/photo3.jpg*</span><span class="sxs-lookup"><span data-stu-id="608ef-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="608ef-168">*2015/体系结构/photo4.jpg*</span><span class="sxs-lookup"><span data-stu-id="608ef-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="608ef-169">*2016/体系结构/photo5.jpg*</span><span class="sxs-lookup"><span data-stu-id="608ef-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="608ef-170">*2016/体系结构/photo6.jpg*</span><span class="sxs-lookup"><span data-stu-id="608ef-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="608ef-171">*2016/体系结构/description.txt*</span><span class="sxs-lookup"><span data-stu-id="608ef-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="608ef-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="608ef-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="608ef-173">当你在 `ListBlobs` 容器上调用时 (如以上示例) 中所示，将返回一个层次结构列表。</span><span class="sxs-lookup"><span data-stu-id="608ef-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="608ef-174">如果它包含 `CloudBlobDirectory` 和 `CloudBlockBlob` 对象，分别表示容器中的目录和 blob，则生成的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="608ef-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="608ef-175">还可以选择将方法的 `UseFlatBlobListing` 参数设置 `ListBlobs` 为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="608ef-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="608ef-176">在这种情况下，容器中的每个 blob 都作为 `CloudBlockBlob` 对象返回。</span><span class="sxs-lookup"><span data-stu-id="608ef-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="608ef-177">对的调用 `ListBlobs` 将返回一个平面列表，如下所示：</span><span class="sxs-lookup"><span data-stu-id="608ef-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="608ef-178">而且，根据容器的当前内容，结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="608ef-178">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="608ef-179">下载 Blob</span><span class="sxs-lookup"><span data-stu-id="608ef-179">Download blobs</span></span>

<span data-ttu-id="608ef-180">若要下载 blob，请首先检索 blob 引用，然后调用 `DownloadToStream` 方法。</span><span class="sxs-lookup"><span data-stu-id="608ef-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="608ef-181">下面的示例使用 `DownloadToStream` 方法将 blob 内容传输到一个流对象，然后你可以将该对象保存到本地文件。</span><span class="sxs-lookup"><span data-stu-id="608ef-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="608ef-182">你还可以使用 `DownloadToStream` 方法以文本字符串形式下载 blob 的内容。</span><span class="sxs-lookup"><span data-stu-id="608ef-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="608ef-183">删除 Blob</span><span class="sxs-lookup"><span data-stu-id="608ef-183">Delete blobs</span></span>

<span data-ttu-id="608ef-184">若要删除 blob，首先要获取 blob 引用，然后对 `Delete` 其调用方法。</span><span class="sxs-lookup"><span data-stu-id="608ef-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="608ef-185">以异步方式列出页中的 Blob</span><span class="sxs-lookup"><span data-stu-id="608ef-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="608ef-186">如果要列出大量 Blob，或需要控制一个列表操作中返回的结果数，则可以结果页的方式列出 Blob。</span><span class="sxs-lookup"><span data-stu-id="608ef-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="608ef-187">此示例显示如何以页面形式异步返回结果，这样就不会在等待返回大型结果集时阻止操作的执行。</span><span class="sxs-lookup"><span data-stu-id="608ef-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="608ef-188">此示例演示平面 blob 列表，但你也可以通过将 `useFlatBlobListing` 方法的参数设置为来执行层次结构列表 `ListBlobsSegmentedAsync` `false` 。</span><span class="sxs-lookup"><span data-stu-id="608ef-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="608ef-189">该示例使用块定义了一个异步方法 `async` 。</span><span class="sxs-lookup"><span data-stu-id="608ef-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="608ef-190">``let!``关键字将挂起示例方法的执行，直至列表任务完成。</span><span class="sxs-lookup"><span data-stu-id="608ef-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="608ef-191">现在，我们可以按如下所示使用此异步例程。</span><span class="sxs-lookup"><span data-stu-id="608ef-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="608ef-192">首先，使用在本教程) 之前创建的本地文件上传一些虚拟数据 (。</span><span class="sxs-lookup"><span data-stu-id="608ef-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="608ef-193">现在，调用例程。</span><span class="sxs-lookup"><span data-stu-id="608ef-193">Now, call the routine.</span></span> <span data-ttu-id="608ef-194">使用 `Async.RunSynchronously` 强制执行异步操作。</span><span class="sxs-lookup"><span data-stu-id="608ef-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="608ef-195">写入追加 Blob</span><span class="sxs-lookup"><span data-stu-id="608ef-195">Writing to an append blob</span></span>

<span data-ttu-id="608ef-196">追加 Blob 针对追加操作（例如日志记录）进行了优化。</span><span class="sxs-lookup"><span data-stu-id="608ef-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="608ef-197">与块 blob 一样，追加 blob 由块组成，但是当你将新块添加到追加 blob 时，它始终追加到 blob 的末尾。</span><span class="sxs-lookup"><span data-stu-id="608ef-197">Like a block blob, an append blob is composed of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="608ef-198">不能更新或删除追加 Blob 中现有的块。</span><span class="sxs-lookup"><span data-stu-id="608ef-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="608ef-199">追加 Blob 的块 ID 不公开，因为它们是用于一个块 Blob 的。</span><span class="sxs-lookup"><span data-stu-id="608ef-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="608ef-200">追加 Blob 中的每个块可以有不同的大小，最大为 4 MB，并且追加 Blob 最多可包含 50000 个块。</span><span class="sxs-lookup"><span data-stu-id="608ef-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="608ef-201">因此，追加 Blob 的最大大小稍微大于 195 GB（4 MB X 50000 块）。</span><span class="sxs-lookup"><span data-stu-id="608ef-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="608ef-202">下面的示例创建一个新的追加 blob 并向其追加一些数据，模拟一个简单的日志记录操作。</span><span class="sxs-lookup"><span data-stu-id="608ef-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="608ef-203">请参阅 [了解块 Blob、页 Blob 和追加 Blob](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) ，就有关三种 Blob 之间的差异了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="608ef-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="608ef-204">并发访问</span><span class="sxs-lookup"><span data-stu-id="608ef-204">Concurrent access</span></span>

<span data-ttu-id="608ef-205">若要允许从多个客户端或多个进程实例并发访问某个 Blob，可以使用 **ETag** 或**租约**。</span><span class="sxs-lookup"><span data-stu-id="608ef-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="608ef-206">**Etag** - 用于检测 Blob 或容器是否已被其他进程修改</span><span class="sxs-lookup"><span data-stu-id="608ef-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="608ef-207">**租约** -提供一种在一段时间内获取对 blob 的独占、可续订、写入或删除访问的方法</span><span class="sxs-lookup"><span data-stu-id="608ef-207">**Lease** - provides a way to obtain exclusive, renewable, write, or delete access to a blob for a period of time</span></span>

<span data-ttu-id="608ef-208">有关详细信息，请参阅 [Microsoft Azure 存储中的 "管理并发](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)"。</span><span class="sxs-lookup"><span data-stu-id="608ef-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="608ef-209">命名容器</span><span class="sxs-lookup"><span data-stu-id="608ef-209">Naming containers</span></span>

<span data-ttu-id="608ef-210">Azure 存储中的每个 Blob 必须驻留在一个容器中。</span><span class="sxs-lookup"><span data-stu-id="608ef-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="608ef-211">该容器构成 Blob 名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="608ef-211">The container forms part of the blob name.</span></span> <span data-ttu-id="608ef-212">例如，在这些示例 Blob URI 中， `mydata` 是容器的名称：</span><span class="sxs-lookup"><span data-stu-id="608ef-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="608ef-213">容器名称必须是有效的 DNS 名称，并符合以下命名规则：</span><span class="sxs-lookup"><span data-stu-id="608ef-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="608ef-214">容器名称必须以字母或数字开头，并且只能包含字母、数字和短划线 (-) 字符。</span><span class="sxs-lookup"><span data-stu-id="608ef-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="608ef-215">每个短划线 (-) 字符的前面和后面都必须是一个字母或数字；在容器名称中不允许连续的短划线 (-)。</span><span class="sxs-lookup"><span data-stu-id="608ef-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="608ef-216">容器名称中的所有字母都必须为小写。</span><span class="sxs-lookup"><span data-stu-id="608ef-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="608ef-217">容器名称必须介于 3 到 63 个字符。</span><span class="sxs-lookup"><span data-stu-id="608ef-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="608ef-218">容器的名称必须始终为小写。</span><span class="sxs-lookup"><span data-stu-id="608ef-218">The name of a container must always be lowercase.</span></span> <span data-ttu-id="608ef-219">如果在容器名称中包括大写字母或以其他方式违反了容器命名规则，则可能会收到 400 错误（错误请求）。</span><span class="sxs-lookup"><span data-stu-id="608ef-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="608ef-220">管理 Blob 安全性</span><span class="sxs-lookup"><span data-stu-id="608ef-220">Managing security for blobs</span></span>

<span data-ttu-id="608ef-221">默认情况下，Azure 存储会限制拥有帐户访问密钥的帐户所有者的访问权限来保持数据安全。</span><span class="sxs-lookup"><span data-stu-id="608ef-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="608ef-222">当需要共享存储帐户中的 Blob 数据时，请注意不可危及帐户访问密钥的安全性。</span><span class="sxs-lookup"><span data-stu-id="608ef-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="608ef-223">此外，可以加密 Blob 数据，以确保其在网络中传输时以及在 Azure 存储中时的安全性。</span><span class="sxs-lookup"><span data-stu-id="608ef-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="608ef-224">控制对 Blob 数据的访问</span><span class="sxs-lookup"><span data-stu-id="608ef-224">Controlling access to blob data</span></span>

<span data-ttu-id="608ef-225">默认情况下，存储帐户中的 Blob 数据仅供存储帐户所有者访问。</span><span class="sxs-lookup"><span data-stu-id="608ef-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="608ef-226">默认情况下，验证对 Blob 存储的请求需要帐户访问密钥。</span><span class="sxs-lookup"><span data-stu-id="608ef-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="608ef-227">但是，你可能希望使某些 blob 数据可供其他用户使用。</span><span class="sxs-lookup"><span data-stu-id="608ef-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="608ef-228">加密 Blob 数据</span><span class="sxs-lookup"><span data-stu-id="608ef-228">Encrypting blob data</span></span>

<span data-ttu-id="608ef-229">Azure 存储支持在客户端和服务器上加密 blob 数据。</span><span class="sxs-lookup"><span data-stu-id="608ef-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="608ef-230">后续步骤</span><span class="sxs-lookup"><span data-stu-id="608ef-230">Next steps</span></span>

<span data-ttu-id="608ef-231">现在，已了解 Blob 存储的基础知识，可单击下面的链接了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="608ef-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="608ef-232">工具</span><span class="sxs-lookup"><span data-stu-id="608ef-232">Tools</span></span>

- <span data-ttu-id="608ef-233">[F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="608ef-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="608ef-234">F # 类型提供程序，可用于浏览 Blob、表和队列的 Azure 存储资产，并可以轻松地对其应用 CRUD 操作。</span><span class="sxs-lookup"><span data-stu-id="608ef-234">An F# Type Provider that can be used to explore Blob, Table, and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="608ef-235">[Fsharp.core](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="608ef-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="608ef-236">使用 Microsoft Azure 表存储服务的 F # API</span><span class="sxs-lookup"><span data-stu-id="608ef-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="608ef-237">[Microsoft Azure 存储资源管理器 (MASE) ](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="608ef-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="608ef-238">Microsoft 提供的免费独立应用，可用于在 Windows、OS X 和 Linux 上以可视方式处理 Azure 存储数据。</span><span class="sxs-lookup"><span data-stu-id="608ef-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="608ef-239">Blob 存储参考</span><span class="sxs-lookup"><span data-stu-id="608ef-239">Blob storage reference</span></span>

- [<span data-ttu-id="608ef-240">用于 .NET 的 Azure 存储 API</span><span class="sxs-lookup"><span data-stu-id="608ef-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="608ef-241">Azure 存储服务 REST API 参考</span><span class="sxs-lookup"><span data-stu-id="608ef-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="608ef-242">相关指南</span><span class="sxs-lookup"><span data-stu-id="608ef-242">Related guides</span></span>

- [<span data-ttu-id="608ef-243">适用于 .NET 的 Azure Blob 存储示例</span><span class="sxs-lookup"><span data-stu-id="608ef-243">Azure Blob Storage Samples for .NET</span></span>](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="608ef-244">AzCopy 入门</span><span class="sxs-lookup"><span data-stu-id="608ef-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- <span data-ttu-id="608ef-245">[Configure Azure Storage connection strings](/azure/storage/common/storage-configure-connection-string)（配置 Azure 存储连接字符串）</span><span class="sxs-lookup"><span data-stu-id="608ef-245">[Configure Azure Storage connection strings](/azure/storage/common/storage-configure-connection-string)</span></span>
- [<span data-ttu-id="608ef-246">Azure 存储团队博客</span><span class="sxs-lookup"><span data-stu-id="608ef-246">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="608ef-247">快速入门：使用 .NET 在对象存储中创建 blob</span><span class="sxs-lookup"><span data-stu-id="608ef-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
