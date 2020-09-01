---
description: -nostdlib（C# 编译器选项）
title: -nostdlib（C# 编译器选项）
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125093"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="5a6cc-103">-nostdlib（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="5a6cc-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="5a6cc-104">-nostdlib 可防止导入 mscorlib.dll，后者定义了整个 System 命名空间\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a6cc-105">语法</span><span class="sxs-lookup"><span data-stu-id="5a6cc-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="5a6cc-106">备注</span><span class="sxs-lookup"><span data-stu-id="5a6cc-106">Remarks</span></span>

<span data-ttu-id="5a6cc-107">如果你想要定义或创建自己的 System 命名空间和对象，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="5a6cc-108">如果未指定 -nostdlib，则 mscorlib.dll 将被导入到程序中（与指定 -nostdlib- 相同）\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="5a6cc-109">指定 -nostdlib 与指定 -nostdlib+ 相同\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="5a6cc-110">在 Visual Studio 中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="5a6cc-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="5a6cc-111">以下说明仅适用于 Visual Studio 2015（及更早版本）。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="5a6cc-112">Visual Studio 的新版本中不存在“不引用 mscorlib.dll”\*\*\*\* 生成属性。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="5a6cc-113">打开项目的“属性” \*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="5a6cc-114">单击“生成” \*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="5a6cc-115">单击“高级”按钮。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="5a6cc-116">修改“不引用 mscorlib.dll” \*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="5a6cc-117">以编程方式设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="5a6cc-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="5a6cc-118">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。</span><span class="sxs-lookup"><span data-stu-id="5a6cc-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a6cc-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a6cc-119">See also</span></span>

- [<span data-ttu-id="5a6cc-120">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="5a6cc-120">C# Compiler Options</span></span>](./index.md)
