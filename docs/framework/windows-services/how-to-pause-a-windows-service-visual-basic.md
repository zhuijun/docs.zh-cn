---
title: 如何：暂停 Windows 服务 (Visual Basic)
description: 了解如何通过 Visual Basic 使用 ServiceController 组件暂停本地计算机上的 Windows 服务（如 IIS 管理服务）。
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 628cc2e896f7f8a289e52674b721c4aef605854c
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925561"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="1eb7c-103">如何：暂停 Windows 服务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eb7c-103">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="1eb7c-104">此示例使用 <xref:System.ServiceProcess.ServiceController> 组件暂停本地计算机上的 IIS 管理服务。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eb7c-105">示例</span><span class="sxs-lookup"><span data-stu-id="1eb7c-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="1eb7c-106">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="1eb7c-107">在代码片段选取器中，它位于“Windows 操作系统 > Windows 服务”  中。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="1eb7c-108">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1eb7c-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="1eb7c-109">Compiling the Code</span></span>  
 <span data-ttu-id="1eb7c-110">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="1eb7c-110">This example requires:</span></span>  
  
- <span data-ttu-id="1eb7c-111">对 System.serviceprocess.dll 的项目引用。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="1eb7c-112">对 <xref:System.ServiceProcess> 命名空间成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="1eb7c-113">如果未在代码中完全限定成员名称，则添加 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="1eb7c-114">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1eb7c-115">可靠编程</span><span class="sxs-lookup"><span data-stu-id="1eb7c-115">Robust Programming</span></span>  
 <span data-ttu-id="1eb7c-116">默认情况下，<xref:System.ServiceProcess.ServiceController> 类的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 属性是本地计算机。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="1eb7c-117">要在其他计算机上引用 Windows 服务，请将 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 属性更改为该计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="1eb7c-118">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="1eb7c-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1eb7c-119">服务无法暂停。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-119">The service cannot be paused.</span></span> <span data-ttu-id="1eb7c-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="1eb7c-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="1eb7c-121">访问 API 时出错。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="1eb7c-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="1eb7c-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1eb7c-123">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1eb7c-123">.NET Framework Security</span></span>  
 <span data-ttu-id="1eb7c-124">通过使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 在 <xref:System.ServiceProcess.ServiceControllerPermission> 中设置权限，可以限制计算机上的服务控制。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="1eb7c-125">通过使用 <xref:System.Security.Permissions.PermissionState> 在 <xref:System.Security.Permissions.SecurityPermission> 中设置权限，可以限制访问服务信息。</span><span class="sxs-lookup"><span data-stu-id="1eb7c-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb7c-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="1eb7c-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="1eb7c-127">如何：继续 Windows 服务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eb7c-127">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
