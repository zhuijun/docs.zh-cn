---
description: -main（C# 编译器选项）
title: -main（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 61e63de8082a335b448ffee1ae35170d3a1cf6b4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125262"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="5f0da-103">-main（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="5f0da-103">-main (C# Compiler Options)</span></span>

<span data-ttu-id="5f0da-104">如果多个类包含 **Main** 方法，此选项将指定包含程序入口点的类。</span><span class="sxs-lookup"><span data-stu-id="5f0da-104">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f0da-105">语法</span><span class="sxs-lookup"><span data-stu-id="5f0da-105">Syntax</span></span>

```console
-main:class
```

## <a name="arguments"></a><span data-ttu-id="5f0da-106">自变量</span><span class="sxs-lookup"><span data-stu-id="5f0da-106">Arguments</span></span>
 `class`  
 <span data-ttu-id="5f0da-107">此类型包含 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="5f0da-107">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="5f0da-108">提供的类名必须是完全限定类名；它必须包括完整命名空间（包含类），后跟类名。</span><span class="sxs-lookup"><span data-stu-id="5f0da-108">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="5f0da-109">例如，当 `Main` 方法位于 `MyApplication.Core` 命名空间中的 `Program` 类中时，编译器选项必须为 `-main:MyApplication.Core.Program`。</span><span class="sxs-lookup"><span data-stu-id="5f0da-109">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f0da-110">备注</span><span class="sxs-lookup"><span data-stu-id="5f0da-110">Remarks</span></span>

<span data-ttu-id="5f0da-111">如果编译包含具有 [Main](../../programming-guide/main-and-command-args/index.md) 方法的多个类型，则可以指定哪个类型包含你想用作程序入口点的 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="5f0da-111">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>

<span data-ttu-id="5f0da-112">此选项在编译 .exe 文件时使用。</span><span class="sxs-lookup"><span data-stu-id="5f0da-112">This option is for use when compiling an *.exe* file.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5f0da-113">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="5f0da-113">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="5f0da-114">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="5f0da-114">Open the project's **Properties** page.</span></span>

2. <span data-ttu-id="5f0da-115">单击“应用程序”属性页。</span><span class="sxs-lookup"><span data-stu-id="5f0da-115">Click the **Application** property page.</span></span>

3. <span data-ttu-id="5f0da-116">修改“启动对象”属性。</span><span class="sxs-lookup"><span data-stu-id="5f0da-116">Modify the **Startup object** property.</span></span>

    <span data-ttu-id="5f0da-117">若要以编程方式设置此编译器选项，请参阅 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。</span><span class="sxs-lookup"><span data-stu-id="5f0da-117">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a><span data-ttu-id="5f0da-118">通过手动编辑 .csproj 文件来设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="5f0da-118">To set this compiler option by manually editing the *.csproj* file</span></span>

<span data-ttu-id="5f0da-119">可以通过编辑 .csproj 文件并在 `PropertyGroup` 部分添加元素 `StartupObject` 来设置此选项。</span><span class="sxs-lookup"><span data-stu-id="5f0da-119">You can set this option by editing the .csproj file and adding an element `StartupObject` inside the `PropertyGroup` section.</span></span> <span data-ttu-id="5f0da-120">例如：</span><span class="sxs-lookup"><span data-stu-id="5f0da-120">For example:</span></span>

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a><span data-ttu-id="5f0da-121">示例</span><span class="sxs-lookup"><span data-stu-id="5f0da-121">Example</span></span>

<span data-ttu-id="5f0da-122">编译 `t2.cs` 和 `t3.cs`，指出 **Main** 方法可在 `Test2` 中找到：</span><span class="sxs-lookup"><span data-stu-id="5f0da-122">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a><span data-ttu-id="5f0da-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f0da-123">See also</span></span>

- [<span data-ttu-id="5f0da-124">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="5f0da-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5f0da-125">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="5f0da-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
