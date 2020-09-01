---
description: -win32icon（C# 编译器选项）
title: -win32icon（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 76a54f9011371492bdc15f15c3e40d51082deed3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138405"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="6b62c-103">-win32icon（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="6b62c-103">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="6b62c-104">-win32icon 选项在输出文件中插入 .ico 文件，为输出文件赋予其在文件资源管理器中所需的外观\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b62c-104">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b62c-105">语法</span><span class="sxs-lookup"><span data-stu-id="6b62c-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b62c-106">自变量</span><span class="sxs-lookup"><span data-stu-id="6b62c-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="6b62c-107">想向输出文件添加的 .ico 文件。</span><span class="sxs-lookup"><span data-stu-id="6b62c-107">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b62c-108">备注</span><span class="sxs-lookup"><span data-stu-id="6b62c-108">Remarks</span></span>  
 <span data-ttu-id="6b62c-109">可以使用[资源编译器](/windows/desktop/menurc/resource-compiler)创建的 .ico 文件。</span><span class="sxs-lookup"><span data-stu-id="6b62c-109">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="6b62c-110">在编译 Visual C++ 程序时会调用资源编译器；.ico 文件是从 .rc 文件创建的。</span><span class="sxs-lookup"><span data-stu-id="6b62c-110">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="6b62c-111">请参阅 [-linkresource](./linkresource-compiler-option.md)（引用）或 [-resource](./resource-compiler-option.md)（附加）.NET Framework 资源文件。</span><span class="sxs-lookup"><span data-stu-id="6b62c-111">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="6b62c-112">请参阅 [-win32res](./win32res-compiler-option.md) 导入 .res 文件。</span><span class="sxs-lookup"><span data-stu-id="6b62c-112">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6b62c-113">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="6b62c-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6b62c-114">打开项目的“属性”页\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b62c-114">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="6b62c-115">单击“应用程序”属性页。</span><span class="sxs-lookup"><span data-stu-id="6b62c-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="6b62c-116">修改“应用程序图标”属性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b62c-116">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="6b62c-117">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>。</span><span class="sxs-lookup"><span data-stu-id="6b62c-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b62c-118">示例</span><span class="sxs-lookup"><span data-stu-id="6b62c-118">Example</span></span>  
 <span data-ttu-id="6b62c-119">编译 `in.cs` 并附加 .ico 文件 `rf.ico` 以生成 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="6b62c-119">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b62c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b62c-120">See also</span></span>

- [<span data-ttu-id="6b62c-121">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="6b62c-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6b62c-122">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="6b62c-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
