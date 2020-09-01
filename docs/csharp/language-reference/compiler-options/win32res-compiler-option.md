---
description: -win32res（C# 编译器选项）
title: -win32res（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: c220c78a6d2c3109402a20f0de40fe9665d6c730
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140810"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="8f0b0-103">-win32res（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="8f0b0-103">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="8f0b0-104">-win32res 选项会在输出文件中插入 Win32 资源\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-104">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0b0-105">语法</span><span class="sxs-lookup"><span data-stu-id="8f0b0-105">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f0b0-106">自变量</span><span class="sxs-lookup"><span data-stu-id="8f0b0-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="8f0b0-107">想向输出文件添加的资源文件。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-107">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f0b0-108">备注</span><span class="sxs-lookup"><span data-stu-id="8f0b0-108">Remarks</span></span>  
 <span data-ttu-id="8f0b0-109">Win32 资源文件可以用[资源编译器](resource-compiler-option.md)创建。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-109">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="8f0b0-110">在编译 Visual C++ 程序时会调用资源编译器；.res 文件是从 .rc 文件创建的。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-110">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="8f0b0-111">Win32 资源可以包含版本或位图（图标）信息，这些信息有助于在文件资源管理器中标识您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-111">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="8f0b0-112">如果不指定 -win32res，编译器将根据程序集版本生成版本信息。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-112">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="8f0b0-113">请参阅 [-linkresource](./linkresource-compiler-option.md)（引用）或 [-resource](./resource-compiler-option.md)（附加）.NET Framework 资源文件。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-113">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8f0b0-114">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="8f0b0-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="8f0b0-115">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="8f0b0-116">单击“应用程序”属性页。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="8f0b0-117">单击“资源文件”按钮，然后使用组合框选择一个文件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f0b0-117">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f0b0-118">示例</span><span class="sxs-lookup"><span data-stu-id="8f0b0-118">Example</span></span>  
 <span data-ttu-id="8f0b0-119">编译 `in.cs` 并附加 Win32 资源文件 `rf.res` 以生成 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="8f0b0-119">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f0b0-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f0b0-120">See also</span></span>

- [<span data-ttu-id="8f0b0-121">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="8f0b0-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8f0b0-122">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="8f0b0-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
