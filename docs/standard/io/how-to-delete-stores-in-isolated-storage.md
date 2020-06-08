---
title: 如何：删除独立存储中的存储区
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
ms.openlocfilehash: 885dc8e3ca0ea99de460cee7dd093b061f916388
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291885"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="2323b-102">如何：删除独立存储中的存储区</span><span class="sxs-lookup"><span data-stu-id="2323b-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="2323b-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> 类提供了两个用于删除独立存储文件的方法：</span><span class="sxs-lookup"><span data-stu-id="2323b-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="2323b-104">实例方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> 不采用任何参数，并删除调用它的存储区。</span><span class="sxs-lookup"><span data-stu-id="2323b-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="2323b-105">此操作无需任何权限。</span><span class="sxs-lookup"><span data-stu-id="2323b-105">No permissions are required for this operation.</span></span> <span data-ttu-id="2323b-106">可以访问此存储区的任何代码都可以删除该存储区内的任何或所有数据。</span><span class="sxs-lookup"><span data-stu-id="2323b-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="2323b-107">静态方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> 采用 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 枚举值，并删除当前运行该代码的用户的所有存储区。</span><span class="sxs-lookup"><span data-stu-id="2323b-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="2323b-108">此操作需要 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 权限来写入 <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> 值。</span><span class="sxs-lookup"><span data-stu-id="2323b-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2323b-109">示例</span><span class="sxs-lookup"><span data-stu-id="2323b-109">Example</span></span>  
 <span data-ttu-id="2323b-110">下面的代码示例演示了如何使用静态的实例方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> 。</span><span class="sxs-lookup"><span data-stu-id="2323b-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="2323b-111">该类获取两个存储区：一个按用户和程序集隔离；另一个按用户、域和程序集隔离。</span><span class="sxs-lookup"><span data-stu-id="2323b-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="2323b-112">随后，将通过调用独立存储文件 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> 的  `isoStore1`方法来删除用户、域和程序集存储区。</span><span class="sxs-lookup"><span data-stu-id="2323b-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="2323b-113">接下来，将通过调用静态方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>来删除该用户的所有剩余存储区。</span><span class="sxs-lookup"><span data-stu-id="2323b-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2323b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2323b-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="2323b-115">独立存储</span><span class="sxs-lookup"><span data-stu-id="2323b-115">Isolated Storage</span></span>](isolated-storage.md)
