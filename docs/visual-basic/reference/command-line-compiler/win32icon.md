---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: c6d5e054063592db5777a76fe19da79337ed5034
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084952"
---
# <a name="-win32icon"></a><span data-ttu-id="c9d1d-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="c9d1d-102">-win32icon</span></span>

<span data-ttu-id="c9d1d-103">将 .ico 文件插入到输出文件。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="c9d1d-104">此 .ico 文件表示文件资源管理器  中的输出文件。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d1d-105">语法</span><span class="sxs-lookup"><span data-stu-id="c9d1d-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9d1d-106">自变量</span><span class="sxs-lookup"><span data-stu-id="c9d1d-106">Arguments</span></span>  
  
|<span data-ttu-id="c9d1d-107">术语</span><span class="sxs-lookup"><span data-stu-id="c9d1d-107">Term</span></span>|<span data-ttu-id="c9d1d-108">定义</span><span class="sxs-lookup"><span data-stu-id="c9d1d-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="c9d1d-109">要向输出文件添加的 .ico 文件。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="c9d1d-110">如果文件名包含空格，则将名称括在引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9d1d-111">备注</span><span class="sxs-lookup"><span data-stu-id="c9d1d-111">Remarks</span></span>  

 <span data-ttu-id="c9d1d-112">可以使用 Microsoft Windows 资源编译器 (RC) 创建 .ico 文件。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="c9d1d-113">在编译 Visual C++ 程序时会调用资源编译器；.ico 文件是从 .rc 文件创建的。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="c9d1d-114">`-win32icon` 和 `-win32resource` 选项互斥。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="c9d1d-115">请参阅 [-linkresource (Visual Basic)](linkresource.md) 以引用 .NET Framework 资源文件，或参阅 [-resource (Visual Basic)](resource.md) 以附加 .NET Framework 资源文件。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-115">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="c9d1d-116">请参阅 [-win32resource](win32resource.md) 以导入 .res 文件。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-116">See [-win32resource](win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="c9d1d-117">若要在 Visual Studio IDE 中设置 -win32icon</span><span class="sxs-lookup"><span data-stu-id="c9d1d-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="c9d1d-118">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c9d1d-119">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c9d1d-120">2.单击“应用程序”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="c9d1d-121">3.修改“图标”  框中的值。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9d1d-122">示例</span><span class="sxs-lookup"><span data-stu-id="c9d1d-122">Example</span></span>  

 <span data-ttu-id="c9d1d-123">下面的代码编译 `In.vb` 并附加 .ico 文件 `Rf.ico`。</span><span class="sxs-lookup"><span data-stu-id="c9d1d-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9d1d-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="c9d1d-124">See also</span></span>

- [<span data-ttu-id="c9d1d-125">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="c9d1d-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c9d1d-126">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="c9d1d-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
