---
title: 如何：查看全局程序集缓存的内容
description: 了解如何使用全局程序集缓存 (GAC) 工具 (gacutil.exe) 查看 .NET 中的全局程序集缓存的内容。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: 8b81f78f4ea28b3b9fca374029fe49f809826d8e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558558"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="21a2f-103">如何：查看全局程序集缓存的内容</span><span class="sxs-lookup"><span data-stu-id="21a2f-103">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="21a2f-104">使用[全局程序集缓存工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 可查看全局程序集缓存 (GAC) 的内容。</span><span class="sxs-lookup"><span data-stu-id="21a2f-104">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="21a2f-105">查看 GAC 中的程序集</span><span class="sxs-lookup"><span data-stu-id="21a2f-105">View the assemblies in the GAC</span></span>

<span data-ttu-id="21a2f-106">要查看全局程序集缓存中的程序集列表，请打开 [Visual Studio 适用的开发人员命令提示](../tools/developer-command-prompt-for-vs.md)，然后输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="21a2f-106">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="21a2f-107">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="21a2f-107">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="21a2f-108">在 .NET Framework 的早期版本中，可通过 [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell 扩展在文件资源管理器中查看全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="21a2f-108">In earlier versions of the .NET Framework, the [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="21a2f-109">从 .NET Framework 4 开始，Shfusion.dll 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="21a2f-109">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="21a2f-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="21a2f-110">See also</span></span>

- [<span data-ttu-id="21a2f-111">使用程序集和全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="21a2f-111">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="21a2f-112">Gacutil.exe（全局程序集缓存工具）</span><span class="sxs-lookup"><span data-stu-id="21a2f-112">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
