---
title: 如何在注册表中创建注册表项 - C# 编程指南
description: 了解如何在注册表中创建注册表项。 参阅代码示例，了解如何编译指令，并参考其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: c51fa61aa4c501921d5c7ace99a8c5aaf7b29f58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203912"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="6279b-104">如何在注册表中创建注册表项（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="6279b-104">How to create a key in the registry (C# Programming Guide)</span></span>

<span data-ttu-id="6279b-105">本示例将值对“Name”和“Isabella”添加到当前用户注册表中的项“Names”之下。</span><span class="sxs-lookup"><span data-stu-id="6279b-105">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="6279b-106">示例</span><span class="sxs-lookup"><span data-stu-id="6279b-106">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6279b-107">编译代码</span><span class="sxs-lookup"><span data-stu-id="6279b-107">Compiling the Code</span></span>  
  
- <span data-ttu-id="6279b-108">复制代码，并将其粘贴到控制台应用程序的 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="6279b-108">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="6279b-109">将 `Names` 参数替换为直接存在于注册表 HKEY_CURRENT_USER 节点下的项的名称。</span><span class="sxs-lookup"><span data-stu-id="6279b-109">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="6279b-110">将 `Name` 参数替换为直接存在于“Names”节点下的值的名称。</span><span class="sxs-lookup"><span data-stu-id="6279b-110">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6279b-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="6279b-111">Robust Programming</span></span>  

 <span data-ttu-id="6279b-112">检查注册表结构，查找适合项的位置。</span><span class="sxs-lookup"><span data-stu-id="6279b-112">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="6279b-113">例如，可能需要打开当前用户的 Software 项，并用公司的名称创建一项。</span><span class="sxs-lookup"><span data-stu-id="6279b-113">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="6279b-114">然后将注册表值添加到公司的项上。</span><span class="sxs-lookup"><span data-stu-id="6279b-114">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="6279b-115">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="6279b-115">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="6279b-116">项的名称为空。</span><span class="sxs-lookup"><span data-stu-id="6279b-116">The name of the key is null.</span></span>  
  
- <span data-ttu-id="6279b-117">用户没有创建注册表项的权限。</span><span class="sxs-lookup"><span data-stu-id="6279b-117">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="6279b-118">项名称超过 255 个字符的限制。</span><span class="sxs-lookup"><span data-stu-id="6279b-118">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="6279b-119">项已关闭。</span><span class="sxs-lookup"><span data-stu-id="6279b-119">The key is closed.</span></span>  
  
- <span data-ttu-id="6279b-120">注册表项为只读。</span><span class="sxs-lookup"><span data-stu-id="6279b-120">The registry key is read-only.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="6279b-121">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="6279b-121">.NET Security</span></span>  

 <span data-ttu-id="6279b-122">将数据写入用户文件夹 `Microsoft.Win32.Registry.CurrentUser` 比写入本地计算机 `Microsoft.Win32.Registry.LocalMachine` 更安全。</span><span class="sxs-lookup"><span data-stu-id="6279b-122">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="6279b-123">创建注册表值时，需要确定该值已存在时应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="6279b-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="6279b-124">另一进程（可能是恶意进程）可能已创建了该值，并拥有对该值的访问权。</span><span class="sxs-lookup"><span data-stu-id="6279b-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="6279b-125">将数据放入注册表值后，其他进程即可使用这些数据。</span><span class="sxs-lookup"><span data-stu-id="6279b-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="6279b-126">若要防止出现这种情况，请使用 `Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="6279b-126">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="6279b-127">方法。</span><span class="sxs-lookup"><span data-stu-id="6279b-127">method.</span></span> <span data-ttu-id="6279b-128">如果项不存在，则该方法返回 null。</span><span class="sxs-lookup"><span data-stu-id="6279b-128">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="6279b-129">即使注册表项受访问控制列表 (ACL) 保护，在注册表中以纯文本形式存储机密信息（例如密码）也不安全。</span><span class="sxs-lookup"><span data-stu-id="6279b-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6279b-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="6279b-130">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="6279b-131">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6279b-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6279b-132">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="6279b-132">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- <span data-ttu-id="6279b-133">[Read, write and delete from the registry with C#](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)（使用 C# 在注册表中执行读取、写入和删除操作）</span><span class="sxs-lookup"><span data-stu-id="6279b-133">[Read, write and delete from the registry with C#](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)</span></span>
