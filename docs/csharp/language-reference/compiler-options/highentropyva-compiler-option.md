---
description: -highentropyva（C# 编译器选项）
title: -highentropyva（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2c2e2780693a89072c4bb55b318be94089bf3ced
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125652"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="8b0bc-103">-highentropyva（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="8b0bc-103">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="8b0bc-104">-highentropyva 编译器选项可向 Windows 内核提供下列信息：特定的可执行文件是否支持高熵地址空间布局随机化 (ASLR)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b0bc-105">语法</span><span class="sxs-lookup"><span data-stu-id="8b0bc-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b0bc-106">自变量</span><span class="sxs-lookup"><span data-stu-id="8b0bc-106">Arguments</span></span>  
 <span data-ttu-id="8b0bc-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8b0bc-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="8b0bc-108">此选项指定 64 位可执行文件或由 [-platform:anycpu](./platform-compiler-option.md) 编译器选项标记的可执行文件支持高熵虚拟地址空间。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="8b0bc-109">默认情况下，此选项处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-109">The option is disabled by default.</span></span> <span data-ttu-id="8b0bc-110">通过 -highentropyva+ 或 -highentropyva 启用它\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b0bc-111">备注</span><span class="sxs-lookup"><span data-stu-id="8b0bc-111">Remarks</span></span>  
 <span data-ttu-id="8b0bc-112">当随机化进程的地址空间布局包含在 ASLR 中时，-highentropyva 选项允许 Windows 内核的兼容版本使用更高程度的熵\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="8b0bc-113">使用更高程度的熵意味着，可向内存区域（例如堆栈或堆）分配更多的地址。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="8b0bc-114">因此，猜测特定内存区域的位置会更加困难。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="8b0bc-115">指定 -highentropyva 编译器选项时，目标可执行文件及其依赖的任何模块在作为 64 位进程运行时，必须能够处理大于 4 GB 的指针值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8b0bc-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
