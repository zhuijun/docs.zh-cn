---
title: 注册客户端提供程序程序集
description: 查看一个示例，该示例演示如何注册包含客户端 UI 自动化提供程序的 DLL。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 034a109bb69c08883c0943b7b6ef69a397a8e7e1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168138"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="8440e-103">注册客户端提供程序程序集</span><span class="sxs-lookup"><span data-stu-id="8440e-103">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
> <span data-ttu-id="8440e-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="8440e-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8440e-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="8440e-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8440e-106">本主题演示如何注册包含客户端 UI 自动化提供程序的 DLL。</span><span class="sxs-lookup"><span data-stu-id="8440e-106">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8440e-107">示例</span><span class="sxs-lookup"><span data-stu-id="8440e-107">Example</span></span>  
 <span data-ttu-id="8440e-108">下面的示例演示如何注册包含控制台窗口提供程序的程序集。</span><span class="sxs-lookup"><span data-stu-id="8440e-108">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="8440e-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8440e-109">See also</span></span>

- [<span data-ttu-id="8440e-110">创建客户端 UI 自动化提供程序</span><span class="sxs-lookup"><span data-stu-id="8440e-110">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
