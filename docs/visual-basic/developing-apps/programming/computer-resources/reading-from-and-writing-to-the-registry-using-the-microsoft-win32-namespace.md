---
title: 使用 Microsoft.Win32 命名空间读取和写入注册表
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 10431b1ad40ed320541a22fb46cc8db6dbb775b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360067"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="fa56a-102">使用 Microsoft.Win32 命名空间读取和写入注册表 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa56a-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="fa56a-103">虽然在针对注册表进行编程时，`My.Computer.Registry` 应涵盖你的基本需求，不过你还可以使用 .NET Framework 的 <xref:Microsoft.Win32> 命名空间中的 <xref:Microsoft.Win32.Registry> 和 <xref:Microsoft.Win32.RegistryKey> 类。</span><span class="sxs-lookup"><span data-stu-id="fa56a-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="fa56a-104">注册表类中的项</span><span class="sxs-lookup"><span data-stu-id="fa56a-104">Keys in the Registry Class</span></span>  

 <span data-ttu-id="fa56a-105"><xref:Microsoft.Win32.Registry> 类提供可以用于访问子项及其值的注册表基项。</span><span class="sxs-lookup"><span data-stu-id="fa56a-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="fa56a-106">这些基项本身是只读的。</span><span class="sxs-lookup"><span data-stu-id="fa56a-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="fa56a-107">下表列出并介绍了 <xref:Microsoft.Win32.Registry> 类公开的七个项。</span><span class="sxs-lookup"><span data-stu-id="fa56a-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="fa56a-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="fa56a-108">**Key**</span></span>|<span data-ttu-id="fa56a-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="fa56a-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="fa56a-110">定义文档的类型以及与这些类型关联的属性。</span><span class="sxs-lookup"><span data-stu-id="fa56a-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="fa56a-111">包含不是特定于用户的硬件配置信息。</span><span class="sxs-lookup"><span data-stu-id="fa56a-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="fa56a-112">包含有关当前用户首选项的信息，如环境变量。</span><span class="sxs-lookup"><span data-stu-id="fa56a-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="fa56a-113">包含动态注册表数据，如虚拟设备驱动程序使用的数据。</span><span class="sxs-lookup"><span data-stu-id="fa56a-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="fa56a-114">包含保存本地计算机的配置数据的五个子项（硬件、SAM、安全性、软件和系统）。</span><span class="sxs-lookup"><span data-stu-id="fa56a-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="fa56a-115">包含软件组件的性能信息。</span><span class="sxs-lookup"><span data-stu-id="fa56a-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="fa56a-116">包含有关默认用户首选项的信息。</span><span class="sxs-lookup"><span data-stu-id="fa56a-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="fa56a-117">将数据写入当前用户 (<xref:Microsoft.Win32.Registry.CurrentUser>) 比写入本地计算机 (<xref:Microsoft.Win32.Registry.LocalMachine>) 更安全。</span><span class="sxs-lookup"><span data-stu-id="fa56a-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="fa56a-118">当你创建的项以前已由其他进程（可能是恶意的）进行了创建时，会发生通常称为“强占”的情况。</span><span class="sxs-lookup"><span data-stu-id="fa56a-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="fa56a-119">若要防止此情况发生，请使用在项尚未存在时返回 `Nothing` 的方法（如 <xref:Microsoft.Win32.RegistryKey.GetValue%2A>）。</span><span class="sxs-lookup"><span data-stu-id="fa56a-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="fa56a-120">从注册表中读取值</span><span class="sxs-lookup"><span data-stu-id="fa56a-120">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="fa56a-121">下面的代码演示如何从 HKEY_CURRENT_USER 中读取字符串。</span><span class="sxs-lookup"><span data-stu-id="fa56a-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="fa56a-122">下面的代码读取一个字符串，使它递增，然后将它写入 HKEY_CURRENT_USER。</span><span class="sxs-lookup"><span data-stu-id="fa56a-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="fa56a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa56a-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="fa56a-124">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="fa56a-124">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="fa56a-125">读取和写入注册表</span><span class="sxs-lookup"><span data-stu-id="fa56a-125">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="fa56a-126">安全性与注册表</span><span class="sxs-lookup"><span data-stu-id="fa56a-126">Security and the Registry</span></span>](security-and-the-registry.md)
