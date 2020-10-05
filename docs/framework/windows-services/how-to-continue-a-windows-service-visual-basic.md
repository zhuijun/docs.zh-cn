---
title: 如何：继续 Windows 服务 (Visual Basic)
description: 了解如何通过 Visual Basic 使用 ServiceController 组件继续本地计算机上的 Windows 服务（如 IIS 管理服务）。
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
ms.openlocfilehash: 9e672a19cec814694eddb35672c5c669efd40eb2
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608603"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="c657c-103">如何：继续 Windows 服务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c657c-103">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="c657c-104">本示例使用 <xref:System.ServiceProcess.ServiceController> 组件继续在本地计算机上执行 IIS 管理服务。</span><span class="sxs-lookup"><span data-stu-id="c657c-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c657c-105">示例</span><span class="sxs-lookup"><span data-stu-id="c657c-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="c657c-106">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="c657c-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c657c-107">在代码片段选取器中，它位于“Windows 操作系统 > Windows 服务”  中。</span><span class="sxs-lookup"><span data-stu-id="c657c-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="c657c-108">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="c657c-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c657c-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="c657c-109">Compiling the Code</span></span>  
 <span data-ttu-id="c657c-110">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="c657c-110">This example requires:</span></span>  
  
- <span data-ttu-id="c657c-111">对 System.serviceprocess.dll 的项目引用。</span><span class="sxs-lookup"><span data-stu-id="c657c-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="c657c-112">对 <xref:System.ServiceProcess> 命名空间成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c657c-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="c657c-113">如果未在代码中完全限定成员名称，则添加 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="c657c-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c657c-114">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="c657c-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c657c-115">可靠编程</span><span class="sxs-lookup"><span data-stu-id="c657c-115">Robust Programming</span></span>  
 <span data-ttu-id="c657c-116">默认情况下，<xref:System.ServiceProcess.ServiceController> 类的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 属性是本地计算机。</span><span class="sxs-lookup"><span data-stu-id="c657c-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="c657c-117">要在其他计算机上引用 Windows 服务，请将 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 属性更改为该计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="c657c-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="c657c-118">在服务控制器状态为 <xref:System.ServiceProcess.ServiceControllerStatus.Paused> 之前，无法调用服务上的 <xref:System.ServiceProcess.ServiceController.Continue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c657c-118">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="c657c-119">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="c657c-119">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c657c-120">服务无法恢复。</span><span class="sxs-lookup"><span data-stu-id="c657c-120">The service cannot be resumed.</span></span> <span data-ttu-id="c657c-121">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="c657c-121">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="c657c-122">访问 API 时出错。</span><span class="sxs-lookup"><span data-stu-id="c657c-122">An error occurred when accessing a system API.</span></span> <span data-ttu-id="c657c-123">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="c657c-123">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c657c-124">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="c657c-124">.NET Framework Security</span></span>  
 <span data-ttu-id="c657c-125">通过使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 枚举在 <xref:System.ServiceProcess.ServiceControllerPermission> 类中设置权限，可以限制计算机上的服务控制。</span><span class="sxs-lookup"><span data-stu-id="c657c-125">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="c657c-126">通过使用 <xref:System.Security.Permissions.PermissionState> 枚举在 <xref:System.Security.Permissions.SecurityPermission> 类中设置权限，可以限制访问服务信息。</span><span class="sxs-lookup"><span data-stu-id="c657c-126">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c657c-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="c657c-127">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="c657c-128">如何：暂停 Windows 服务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c657c-128">How to: Pause a Windows Service (Visual Basic)</span></span>](how-to-pause-a-windows-service-visual-basic.md)
