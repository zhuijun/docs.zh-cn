---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 94a8b43a891df9837925869e17fac4536a995264
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414267"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="bdd75-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd75-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="bdd75-103">使编译器将第一次出现的警告视为错误。</span><span class="sxs-lookup"><span data-stu-id="bdd75-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd75-104">语法</span><span class="sxs-lookup"><span data-stu-id="bdd75-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bdd75-105">自变量</span><span class="sxs-lookup"><span data-stu-id="bdd75-105">Arguments</span></span>  
  
|<span data-ttu-id="bdd75-106">术语</span><span class="sxs-lookup"><span data-stu-id="bdd75-106">Term</span></span>|<span data-ttu-id="bdd75-107">定义</span><span class="sxs-lookup"><span data-stu-id="bdd75-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="bdd75-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="bdd75-108">+ &#124; -</span></span>|<span data-ttu-id="bdd75-109">可选。</span><span class="sxs-lookup"><span data-stu-id="bdd75-109">Optional.</span></span> <span data-ttu-id="bdd75-110">默认情况下，`-warnaserror-` 生效；警告不会阻止编译器生成输出文件。</span><span class="sxs-lookup"><span data-stu-id="bdd75-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="bdd75-111">`-warnaserror` 选项与 `-warnaserror+` 相同，会导致将警告视为错误。</span><span class="sxs-lookup"><span data-stu-id="bdd75-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="bdd75-112">可选。</span><span class="sxs-lookup"><span data-stu-id="bdd75-112">Optional.</span></span> <span data-ttu-id="bdd75-113">`-warnaserror` 选项适用的警告 ID 编号列表，以逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="bdd75-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="bdd75-114">如果未指定警告 ID，则 `-warnaserror` 选项适用于所有警告。</span><span class="sxs-lookup"><span data-stu-id="bdd75-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdd75-115">备注</span><span class="sxs-lookup"><span data-stu-id="bdd75-115">Remarks</span></span>  
 <span data-ttu-id="bdd75-116">`-warnaserror` 选项将所有警告视为错误。</span><span class="sxs-lookup"><span data-stu-id="bdd75-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="bdd75-117">通常将报告为警告的任何消息都报告为错误。</span><span class="sxs-lookup"><span data-stu-id="bdd75-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="bdd75-118">编译器将随后出现的相同警告报告为警告。</span><span class="sxs-lookup"><span data-stu-id="bdd75-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="bdd75-119">默认情况下，`-warnaserror-` 生效，导致警告仅提供信息。</span><span class="sxs-lookup"><span data-stu-id="bdd75-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="bdd75-120">`-warnaserror` 选项与 `-warnaserror+` 相同，会导致将警告视为错误。</span><span class="sxs-lookup"><span data-stu-id="bdd75-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="bdd75-121">如果希望仅将一些特定警告视为错误，则可以指定视为错误的警告编号的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="bdd75-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdd75-122">`-warnaserror` 选项不控制警告的显示方式。</span><span class="sxs-lookup"><span data-stu-id="bdd75-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="bdd75-123">使用 [-nowarn](nowarn.md) 选项来禁用警告。</span><span class="sxs-lookup"><span data-stu-id="bdd75-123">Use the [-nowarn](nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="bdd75-124">设置 -warnaserror 以将所有警告视为 Visual Studio IDE 中的错误</span><span class="sxs-lookup"><span data-stu-id="bdd75-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="bdd75-125">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="bdd75-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bdd75-126">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="bdd75-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="bdd75-127">2.单击“编译”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="bdd75-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="bdd75-128">3.确保“禁用所有警告”  复选框处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="bdd75-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="bdd75-129">4.选中“将所有警告视为错误”  复选框。</span><span class="sxs-lookup"><span data-stu-id="bdd75-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="bdd75-130">设置 -warnaserror 以将特定警告视为 Visual Studio IDE 中的错误</span><span class="sxs-lookup"><span data-stu-id="bdd75-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="bdd75-131">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="bdd75-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bdd75-132">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="bdd75-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="bdd75-133">2.单击“编译”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="bdd75-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="bdd75-134">3.确保“禁用所有警告”  复选框处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="bdd75-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="bdd75-135">4.确保“将所有警告视为错误”  复选框处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="bdd75-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="bdd75-136">5.从应将其视为错误的警告旁的“通知”  列中选择“错误”  。</span><span class="sxs-lookup"><span data-stu-id="bdd75-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bdd75-137">示例</span><span class="sxs-lookup"><span data-stu-id="bdd75-137">Example</span></span>  
 <span data-ttu-id="bdd75-138">以下代码编译 `In.vb` 并指示编译器在第一次发现每个警告时显示错误。</span><span class="sxs-lookup"><span data-stu-id="bdd75-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="bdd75-139">示例</span><span class="sxs-lookup"><span data-stu-id="bdd75-139">Example</span></span>  
 <span data-ttu-id="bdd75-140">以下代码编译 `T2.vb` 并仅将未使用的本地变量 (42024) 的警告视为错误。</span><span class="sxs-lookup"><span data-stu-id="bdd75-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdd75-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="bdd75-141">See also</span></span>

- [<span data-ttu-id="bdd75-142">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="bdd75-142">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bdd75-143">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="bdd75-143">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="bdd75-144">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bdd75-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
