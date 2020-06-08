---
title: 如何：删除注册表项
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: ea537d302f64933176f1a44fec2e27b804ff5809
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363314"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="1ba8c-102">如何：在 Visual Basic 中删除注册表项</span><span class="sxs-lookup"><span data-stu-id="1ba8c-102">How to: Delete a Registry Key in Visual Basic</span></span>

<span data-ttu-id="1ba8c-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> 和 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> 方法可以用于删除注册表项。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1ba8c-104">过程</span><span class="sxs-lookup"><span data-stu-id="1ba8c-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="1ba8c-105">删除注册表项</span><span class="sxs-lookup"><span data-stu-id="1ba8c-105">To delete a registry key</span></span>  
  
- <span data-ttu-id="1ba8c-106">使用 `DeleteSubKey` 方法删除注册表项。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="1ba8c-107">此示例将删除 CurrentUser 配置单元中的软件/TestApp 项。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="1ba8c-108">可在代码中更改为相应的字符串，或使它依赖于用户提供的信息。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1ba8c-109">可靠编程</span><span class="sxs-lookup"><span data-stu-id="1ba8c-109">Robust Programming</span></span>  

 <span data-ttu-id="1ba8c-110">如果键/值对不存在，`DeleteSubKey` 方法将返回一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="1ba8c-111">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="1ba8c-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1ba8c-112">密钥名称是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="1ba8c-113">用户没有删除注册表项的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="1ba8c-114">项名称超过 255 个字符的限制 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="1ba8c-115">注册表项为只读 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1ba8c-116">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1ba8c-116">.NET Framework Security</span></span>  

 <span data-ttu-id="1ba8c-117">如果未授予足够的运行时权限 (<xref:System.Security.Permissions.RegistryPermission>) 或用户没有用于创建或写入设置的适当访问权限（由 ACL 确定），则注册表调用将失败。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="1ba8c-118">例如，具有代码访问安全性权限的本地应用程序可能没有操作系统权限。</span><span class="sxs-lookup"><span data-stu-id="1ba8c-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba8c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ba8c-119">See also</span></span>

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="1ba8c-120">安全性与注册表</span><span class="sxs-lookup"><span data-stu-id="1ba8c-120">Security and the Registry</span></span>](security-and-the-registry.md)
- [<span data-ttu-id="1ba8c-121">读取和写入注册表</span><span class="sxs-lookup"><span data-stu-id="1ba8c-121">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
