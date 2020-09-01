---
description: -target:appcontainerexe（C# 编译器选项）
title: -target:appcontainerexe（C# 编译器选项）
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 8c3b85c2f5a20788bd311e9bf3b300c32967da77
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128577"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="b3f3e-103">-target:appcontainerexe（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="b3f3e-103">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="b3f3e-104">如果使用 -target:appcontainerexe 编译器选项，则编译器会创建一个 Windows 可执行 (.exe) 文件，该文件必须在应用容器中运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-104">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="b3f3e-105">此选项与 [-target:winexe](./target-winexe-compiler-option.md) 等效，但专门用于 Windows 8.x 应用商店应用。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-105">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f3e-106">语法</span><span class="sxs-lookup"><span data-stu-id="b3f3e-106">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3f3e-107">备注</span><span class="sxs-lookup"><span data-stu-id="b3f3e-107">Remarks</span></span>  
 <span data-ttu-id="b3f3e-108">为了要求应用在应用容器中运行，此选项在[可移植可执行](/windows/desktop/Debug/pe-format) (PE) 文件中设置了一个位。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-108">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="b3f3e-109">设置该位时，如果 CreateProcess 方法尝试在应用容器外启动该可执行文件，就会发生错误。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-109">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="b3f3e-110">除非使用 [-out](./out-compiler-option.md) 选项，否则输出文件名采用包含 [Main](../../programming-guide/main-and-command-args/index.md) 方法的输入文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-110">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="b3f3e-111">如果在命令提示符处指定此选项，则在下一个 -out 或 -target 选项之前，会使用所有文件来创建可执行文件\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-111">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="b3f3e-112">在 IDE 中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="b3f3e-112">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="b3f3e-113">在“解决方案资源管理器”  中，打开项目的快捷菜单，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-113">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="b3f3e-114">在“应用程序”\*\*\*\* 选项卡上，在“输出类型”\*\*\*\* 列表中选择“Windows 应用商店应用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-114">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="b3f3e-115">此选项仅可用于 Windows 8.x 应用商店应用模板。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-115">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="b3f3e-116">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-116">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3f3e-117">示例</span><span class="sxs-lookup"><span data-stu-id="b3f3e-117">Example</span></span>  
 <span data-ttu-id="b3f3e-118">以下命令将 `filename.cs` 编译为一个只能在应用容器中运行的 Windows 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="b3f3e-118">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3f3e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3f3e-119">See also</span></span>

- [<span data-ttu-id="b3f3e-120">-target（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="b3f3e-120">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="b3f3e-121">-target:winexe（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="b3f3e-121">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="b3f3e-122">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="b3f3e-122">C# Compiler Options</span></span>](./index.md)
