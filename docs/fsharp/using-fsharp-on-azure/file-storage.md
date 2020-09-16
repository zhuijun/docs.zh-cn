---
title: 通过 F# 实现 Azure 文件存储入门
description: 使用 Azure 文件存储在云中存储文件数据和从 Azure 虚拟机 (VM) 或从运行 Windows 的本地应用程序装载云文件共享。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 04bee82fd9d3c652cd99b9c951880f6ba89610ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548457"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="16915-103">使用 F 开始使用 Azure 文件存储\#</span><span class="sxs-lookup"><span data-stu-id="16915-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="16915-104">Azure 文件存储是一种服务，它使用标准 [服务器消息块 (SMB) 协议](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)在云中提供文件共享。</span><span class="sxs-lookup"><span data-stu-id="16915-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview).</span></span> <span data-ttu-id="16915-105">支持 SMB 2.1 和 SMB 3.0。</span><span class="sxs-lookup"><span data-stu-id="16915-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="16915-106">通过 Azure 文件存储，可以将依赖文件共享的旧版应用程序快速迁移到 Azure 且无成本高昂的重写。</span><span class="sxs-lookup"><span data-stu-id="16915-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="16915-107">在 Azure 虚拟机或云服务中或者从本地客户端运行的应用程序可以在云中装载文件共享，就像桌面应用程序装载典型的 SMB 共享一样。</span><span class="sxs-lookup"><span data-stu-id="16915-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="16915-108">之后，任意数量的应用程序组件可以装载并同时访问文件存储共享。</span><span class="sxs-lookup"><span data-stu-id="16915-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="16915-109">有关文件存储的概念性概述，请参阅 [适用于文件存储的 .net 指南](/azure/storage/storage-dotnet-how-to-use-files)。</span><span class="sxs-lookup"><span data-stu-id="16915-109">For a conceptual overview of file storage, see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16915-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="16915-110">Prerequisites</span></span>

<span data-ttu-id="16915-111">若要使用本指南，必须先 [创建 Azure 存储帐户](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="16915-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="16915-112">还需要此帐户的存储访问密钥。</span><span class="sxs-lookup"><span data-stu-id="16915-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="16915-113">创建 F # 脚本并开始 F# 交互窗口</span><span class="sxs-lookup"><span data-stu-id="16915-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="16915-114">本文中的示例可用于 F # 应用程序或 F # 脚本。</span><span class="sxs-lookup"><span data-stu-id="16915-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="16915-115">若要创建 F # 脚本，请创建 `.fsx` 扩展名为的文件，例如 `files.fsx` f # 开发环境中的文件。</span><span class="sxs-lookup"><span data-stu-id="16915-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="16915-116">接下来，使用 [包管理器](package-management.md) （如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ） `WindowsAzure.Storage` `WindowsAzure.Storage.dll` 通过指令在脚本中安装包和引用 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="16915-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="16915-117">添加命名空间声明</span><span class="sxs-lookup"><span data-stu-id="16915-117">Add namespace declarations</span></span>

<span data-ttu-id="16915-118">将下列 `open` 语句添加到 `files.fsx` 文件顶部：</span><span class="sxs-lookup"><span data-stu-id="16915-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="16915-119">获取连接字符串</span><span class="sxs-lookup"><span data-stu-id="16915-119">Get your connection string</span></span>

<span data-ttu-id="16915-120">本教程需要 Azure 存储连接字符串。</span><span class="sxs-lookup"><span data-stu-id="16915-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="16915-121">有关连接字符串的详细信息，请参阅 [配置存储连接字符串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="16915-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="16915-122">对于本教程，您将在脚本中输入连接字符串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="16915-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="16915-123">但对于实际项目， **不建议这样做** 。</span><span class="sxs-lookup"><span data-stu-id="16915-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="16915-124">存储帐户密钥类似于存储帐户的根密码。</span><span class="sxs-lookup"><span data-stu-id="16915-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="16915-125">始终要小心保护存储帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="16915-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="16915-126">避免将其分发给其他用户、对其进行硬编码或将其保存在其他人可以访问的纯文本文件中。</span><span class="sxs-lookup"><span data-stu-id="16915-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="16915-127">如果你认为密钥可能已泄漏，你可以使用 Azure 门户重新生成密钥。</span><span class="sxs-lookup"><span data-stu-id="16915-127">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="16915-128">对于实际应用程序，维护存储连接字符串的最佳方式是在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="16915-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="16915-129">若要从配置文件中提取连接字符串，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="16915-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="16915-130">不一定要使用 Azure Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="16915-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="16915-131">你还可以使用 API，例如 .NET Framework 的 `ConfigurationManager` 类型。</span><span class="sxs-lookup"><span data-stu-id="16915-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="16915-132">解析连接字符串</span><span class="sxs-lookup"><span data-stu-id="16915-132">Parse the connection string</span></span>

<span data-ttu-id="16915-133">若要分析连接字符串，请使用：</span><span class="sxs-lookup"><span data-stu-id="16915-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="16915-134">这将返回 `CloudStorageAccount` 。</span><span class="sxs-lookup"><span data-stu-id="16915-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="16915-135">创建文件服务客户端</span><span class="sxs-lookup"><span data-stu-id="16915-135">Create the File service client</span></span>

<span data-ttu-id="16915-136">`CloudFileClient`类型允许以编程方式使用存储在文件存储中的文件。</span><span class="sxs-lookup"><span data-stu-id="16915-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="16915-137">下面是创建服务客户端的一种方法：</span><span class="sxs-lookup"><span data-stu-id="16915-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="16915-138">现在，你已准备好编写从文件存储读取数据并将数据写入文件存储的代码。</span><span class="sxs-lookup"><span data-stu-id="16915-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="16915-139">创建文件共享</span><span class="sxs-lookup"><span data-stu-id="16915-139">Create a file share</span></span>

<span data-ttu-id="16915-140">此示例演示如何创建不存在的文件共享：</span><span class="sxs-lookup"><span data-stu-id="16915-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="16915-141">创建根目录和子目录</span><span class="sxs-lookup"><span data-stu-id="16915-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="16915-142">在这里，你将获取根目录并获取根目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="16915-142">Here, you get the root directory and get a subdirectory of the root.</span></span> <span data-ttu-id="16915-143">如果它们尚不存在，则创建它们。</span><span class="sxs-lookup"><span data-stu-id="16915-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="16915-144">以文件形式上传文本</span><span class="sxs-lookup"><span data-stu-id="16915-144">Upload text as a file</span></span>

<span data-ttu-id="16915-145">此示例演示如何将文本作为文件上传。</span><span class="sxs-lookup"><span data-stu-id="16915-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="16915-146">将文件下载到文件的本地副本</span><span class="sxs-lookup"><span data-stu-id="16915-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="16915-147">此处下载刚刚创建的文件，并将内容追加到本地文件。</span><span class="sxs-lookup"><span data-stu-id="16915-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="16915-148">设置文件共享的最大大小</span><span class="sxs-lookup"><span data-stu-id="16915-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="16915-149">下面的示例演示如何检查共享的当前使用情况，以及如何设置共享的配额。</span><span class="sxs-lookup"><span data-stu-id="16915-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="16915-150">`FetchAttributes` 必须调用以填充共享的 `Properties` ，并 `SetProperties` 将本地更改传播到 Azure 文件存储。</span><span class="sxs-lookup"><span data-stu-id="16915-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="16915-151">为文件或文件共享生成共享访问签名</span><span class="sxs-lookup"><span data-stu-id="16915-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="16915-152">可以为文件共享或单个文件生成共享访问签名 (SAS)。</span><span class="sxs-lookup"><span data-stu-id="16915-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="16915-153">还可以在文件共享上创建一个共享访问策略以管理共享访问签名。</span><span class="sxs-lookup"><span data-stu-id="16915-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="16915-154">建议创建共享访问策略，因为它提供了一种在受到威胁时撤消 SAS 的方式。</span><span class="sxs-lookup"><span data-stu-id="16915-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="16915-155">此处，在共享上创建共享访问策略，然后使用该策略为共享中的文件提供 SAS 约束。</span><span class="sxs-lookup"><span data-stu-id="16915-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="16915-156">有关创建和使用共享访问签名的更多信息，请参阅[使用共享访问签名 (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) 和[创建 SAS 并将其与 Blob 存储结合使用](/azure/storage/storage-dotnet-shared-access-signature-part-2)。</span><span class="sxs-lookup"><span data-stu-id="16915-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="16915-157">复制文件</span><span class="sxs-lookup"><span data-stu-id="16915-157">Copy files</span></span>

<span data-ttu-id="16915-158">可以将文件复制到另一个文件，或复制到一个 blob，或将一个 blob 复制到一个文件中。</span><span class="sxs-lookup"><span data-stu-id="16915-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="16915-159">如果要将一个 blob 复制到一个文件，或将一个文件复制到一个 blob，则 *必须* 使用共享访问签名 (SAS) 对源对象进行身份验证，即使你在同一存储帐户内进行复制也是如此。</span><span class="sxs-lookup"><span data-stu-id="16915-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="16915-160">将一个文件复制到另一个文件</span><span class="sxs-lookup"><span data-stu-id="16915-160">Copy a file to another file</span></span>

<span data-ttu-id="16915-161">此处，将文件复制到同一共享中的另一个文件。</span><span class="sxs-lookup"><span data-stu-id="16915-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="16915-162">因为此操作在同一存储帐户中的文件之间进行复制，可以使用共享密钥身份验证来进行复制。</span><span class="sxs-lookup"><span data-stu-id="16915-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="16915-163">将文件复制到 Blob</span><span class="sxs-lookup"><span data-stu-id="16915-163">Copy a file to a blob</span></span>

<span data-ttu-id="16915-164">在这里，你将创建一个文件并将其复制到同一存储帐户中的 blob。</span><span class="sxs-lookup"><span data-stu-id="16915-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="16915-165">为源文件创建一个 SAS，服务在复制操作期间使用该 SAS 验证对源文件的访问。</span><span class="sxs-lookup"><span data-stu-id="16915-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="16915-166">可以用相同的方式将一个 Blob 复制到一个文件。</span><span class="sxs-lookup"><span data-stu-id="16915-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="16915-167">如果源对象是一个 Blob，则创建一个 SAS 以复制操作期间验证对该 Blob 的访问。</span><span class="sxs-lookup"><span data-stu-id="16915-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="16915-168">使用指标对文件存储进行故障排除</span><span class="sxs-lookup"><span data-stu-id="16915-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="16915-169">Azure 存储分析支持用于文件存储的指标。</span><span class="sxs-lookup"><span data-stu-id="16915-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="16915-170">使用指标数据，可以跟踪请求和诊断问题。</span><span class="sxs-lookup"><span data-stu-id="16915-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="16915-171">可以从 [Azure 门户](https://portal.azure.com)中为文件存储启用指标，也可以从 F # 中执行此操作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="16915-171">You can enable metrics for File storage from the [Azure portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="16915-172">后续步骤</span><span class="sxs-lookup"><span data-stu-id="16915-172">Next steps</span></span>

<span data-ttu-id="16915-173">有关 Azure 文件存储的详细信息，请参阅以下链接。</span><span class="sxs-lookup"><span data-stu-id="16915-173">For more information about Azure File storage, see these links.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="16915-174">概念性文章和视频</span><span class="sxs-lookup"><span data-stu-id="16915-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="16915-175">Azure 文件存储：适用于 Windows 和 Linux 的顺畅的云 SMB 文件系统</span><span class="sxs-lookup"><span data-stu-id="16915-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="16915-176">如何通过 Linux 使用 Azure 文件存储</span><span class="sxs-lookup"><span data-stu-id="16915-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="16915-177">文件存储的工具支持</span><span class="sxs-lookup"><span data-stu-id="16915-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="16915-178">对 Azure 存储使用 Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="16915-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="16915-179">如何对 Microsoft Azure 存储使用 AzCopy</span><span class="sxs-lookup"><span data-stu-id="16915-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="16915-180">使用 Azure CLI 创建、下载和列出 blob</span><span class="sxs-lookup"><span data-stu-id="16915-180">Create, download, and list blobs with Azure CLI</span></span>](/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="16915-181">参考</span><span class="sxs-lookup"><span data-stu-id="16915-181">Reference</span></span>

- [<span data-ttu-id="16915-182">.NET 存储客户端库参考</span><span class="sxs-lookup"><span data-stu-id="16915-182">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="16915-183">文件服务 REST API 参考</span><span class="sxs-lookup"><span data-stu-id="16915-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="16915-184">博客文章</span><span class="sxs-lookup"><span data-stu-id="16915-184">Blog posts</span></span>

- [<span data-ttu-id="16915-185">Azure 文件存储现已正式发布</span><span class="sxs-lookup"><span data-stu-id="16915-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="16915-186">Azure 文件存储内部</span><span class="sxs-lookup"><span data-stu-id="16915-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [<span data-ttu-id="16915-187">Microsoft Azure 文件服务简介</span><span class="sxs-lookup"><span data-stu-id="16915-187">Introducing Microsoft Azure File Service</span></span>](/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [<span data-ttu-id="16915-188">将连接保存到 Microsoft Azure 文件中</span><span class="sxs-lookup"><span data-stu-id="16915-188">Persisting connections to Microsoft Azure Files</span></span>](/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
