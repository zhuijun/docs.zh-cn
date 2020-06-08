---
title: 如何：预见独立存储中的空间不足条件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
ms.openlocfilehash: bdc2cee343e9d9be44230e84ff45d6fa54901f48
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288584"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="542f4-102">如何：预见独立存储中的空间不足条件</span><span class="sxs-lookup"><span data-stu-id="542f4-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="542f4-103">使用独立存储的代码受[配额](isolated-storage.md#quotas)限制，配额指定了独立存储文件和目录所在数据隔离舱的大小上限。</span><span class="sxs-lookup"><span data-stu-id="542f4-103">Code that uses isolated storage is constrained by a [quota](isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="542f4-104">该配额由安全策略定义，管理员可以对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="542f4-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="542f4-105">如果尝试写入数据时超过了所允许的最大大小，将引发 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 异常并使操作失败。</span><span class="sxs-lookup"><span data-stu-id="542f4-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="542f4-106">这有助于防止恶意的拒绝服务攻击，此类攻击可能会导致应用因为数据存储已满而拒绝请求。</span><span class="sxs-lookup"><span data-stu-id="542f4-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="542f4-107">为有助于确定给定写入尝试是否有可能由于此原因而失败，<xref:System.IO.IsolatedStorage.IsolatedStorage> 类提供了下列三个只读属性：<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>。</span><span class="sxs-lookup"><span data-stu-id="542f4-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="542f4-108">您可以使用这些属性来确定写入存储区是否将导致超过存储区所允许的最大大小。</span><span class="sxs-lookup"><span data-stu-id="542f4-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="542f4-109">记住独立存储可能被同时访问；因此，当计算剩余存储量时，该存储空间可能在您尝试写入存储区时已被使用。</span><span class="sxs-lookup"><span data-stu-id="542f4-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="542f4-110">但是，您可以使用存储区的最大大小来确定是否将达到可用存储的上限。</span><span class="sxs-lookup"><span data-stu-id="542f4-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="542f4-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> 属性依赖程序集中的证据来正常工作。</span><span class="sxs-lookup"><span data-stu-id="542f4-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="542f4-112">因此，只应在使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> 或 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 方法创建的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 对象上检索此属性。</span><span class="sxs-lookup"><span data-stu-id="542f4-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="542f4-113">以其他任何方式创建的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 对象（例如从 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> 方法返回的对象）将无法返回准确的最大大小。</span><span class="sxs-lookup"><span data-stu-id="542f4-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="542f4-114">示例</span><span class="sxs-lookup"><span data-stu-id="542f4-114">Example</span></span>

<span data-ttu-id="542f4-115">下面的代码示例获取独立存储，创建一些文件，并检索 <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="542f4-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="542f4-116">剩余空间以字节为单位进行报告。</span><span class="sxs-lookup"><span data-stu-id="542f4-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="542f4-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="542f4-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="542f4-118">独立存储</span><span class="sxs-lookup"><span data-stu-id="542f4-118">Isolated Storage</span></span>](isolated-storage.md)
- [<span data-ttu-id="542f4-119">如何：获取独立存储的存储区</span><span class="sxs-lookup"><span data-stu-id="542f4-119">How to: Obtain Stores for Isolated Storage</span></span>](how-to-obtain-stores-for-isolated-storage.md)
