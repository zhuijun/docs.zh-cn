---
description: -warn（C# 编译器选项）
title: -warn（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 55e80d0bd05e2119154210503bb277d743050e18
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139068"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="0dbf3-103">-warn（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="0dbf3-103">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="0dbf3-104">-warn 选项指定编译器显示的警告等级\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-104">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dbf3-105">语法</span><span class="sxs-lookup"><span data-stu-id="0dbf3-105">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="0dbf3-106">自变量</span><span class="sxs-lookup"><span data-stu-id="0dbf3-106">Arguments</span></span>  
 `option`  
 <span data-ttu-id="0dbf3-107">想要为编译显示的警告等级：较低的数字仅显示高严重性警告；较高的数字显示更多警告。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-107">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="0dbf3-108">该值必须是零或正整数：</span><span class="sxs-lookup"><span data-stu-id="0dbf3-108">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="0dbf3-109">警告级别</span><span class="sxs-lookup"><span data-stu-id="0dbf3-109">Warning level</span></span>|<span data-ttu-id="0dbf3-110">含义</span><span class="sxs-lookup"><span data-stu-id="0dbf3-110">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="0dbf3-111">0</span><span class="sxs-lookup"><span data-stu-id="0dbf3-111">0</span></span>|<span data-ttu-id="0dbf3-112">关闭发出所有警告消息。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-112">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="0dbf3-113">1</span><span class="sxs-lookup"><span data-stu-id="0dbf3-113">1</span></span>|<span data-ttu-id="0dbf3-114">显示严重警告消息。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-114">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="0dbf3-115">2</span><span class="sxs-lookup"><span data-stu-id="0dbf3-115">2</span></span>|<span data-ttu-id="0dbf3-116">显示等级 1 警告以及某些不太严重的警告，如有关隐藏类成员的警告。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-116">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="0dbf3-117">3</span><span class="sxs-lookup"><span data-stu-id="0dbf3-117">3</span></span>|<span data-ttu-id="0dbf3-118">显示等级 2 警告以及某些不太严重的警告，如有关经常计算为 `true` 或 `false` 的表达式的警告。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-118">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="0dbf3-119">4（默认值）</span><span class="sxs-lookup"><span data-stu-id="0dbf3-119">4 (the default)</span></span>|<span data-ttu-id="0dbf3-120">显示所有等级 3 警告以及信息性警告。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-120">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="0dbf3-121">5</span><span class="sxs-lookup"><span data-stu-id="0dbf3-121">5</span></span>|<span data-ttu-id="0dbf3-122">显示等级 4 警告以及 C# 9.0 附带的编译器中的[其他警告](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md)。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-122">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="0dbf3-123">大于 5</span><span class="sxs-lookup"><span data-stu-id="0dbf3-123">Greater than 5</span></span>|<span data-ttu-id="0dbf3-124">任何大于 5 的值都将被视为 5。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-124">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="0dbf3-125">通常，如果使用新的警告等级更新编译器，则可以输入任意大的值（例如 `9999`）以确保始终获取所有警告。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-125">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="0dbf3-126">备注</span><span class="sxs-lookup"><span data-stu-id="0dbf3-126">Remarks</span></span>  
 <span data-ttu-id="0dbf3-127">若要获取有关错误或警告的信息，可以在帮助索引中查找错误代码。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-127">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="0dbf3-128">有关获取错误或警告信息的其他方法，请参阅 [C# 编译器错误](../compiler-messages/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-128">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="0dbf3-129">使用 [-warnaserror](./warnaserror-compiler-option.md) 将所有警告视为错误。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-129">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="0dbf3-130">使用 [-nowarn](./nowarn-compiler-option.md) 禁用某些警告。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-130">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="0dbf3-131">-w 是 -warn 的缩写形式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-131">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0dbf3-132">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="0dbf3-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="0dbf3-133">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-133">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="0dbf3-134">单击“生成”\*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-134">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="0dbf3-135">修改警告等级\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-135">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="0dbf3-136">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>。</span><span class="sxs-lookup"><span data-stu-id="0dbf3-136">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dbf3-137">示例</span><span class="sxs-lookup"><span data-stu-id="0dbf3-137">Example</span></span>  
 <span data-ttu-id="0dbf3-138">编译 `in.cs` 并使编译器仅显示等级 1 警告：</span><span class="sxs-lookup"><span data-stu-id="0dbf3-138">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dbf3-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0dbf3-139">See also</span></span>

- [<span data-ttu-id="0dbf3-140">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="0dbf3-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0dbf3-141">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="0dbf3-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
