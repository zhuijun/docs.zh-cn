---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 7c013270c8a6b7c2b28f02766df7437b43075dd2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098899"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="51116-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51116-102">-out (Visual Basic)</span></span>

<span data-ttu-id="51116-103">指定输出文件的名称。</span><span class="sxs-lookup"><span data-stu-id="51116-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51116-104">语法</span><span class="sxs-lookup"><span data-stu-id="51116-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="51116-105">参数</span><span class="sxs-lookup"><span data-stu-id="51116-105">Arguments</span></span>  
  
|<span data-ttu-id="51116-106">术语</span><span class="sxs-lookup"><span data-stu-id="51116-106">Term</span></span>|<span data-ttu-id="51116-107">定义</span><span class="sxs-lookup"><span data-stu-id="51116-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="51116-108">必需。</span><span class="sxs-lookup"><span data-stu-id="51116-108">Required.</span></span> <span data-ttu-id="51116-109">编译器创建的输出文件的名称。</span><span class="sxs-lookup"><span data-stu-id="51116-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="51116-110">如果文件名包含空格，则将名称括在引号内 (" ")。</span><span class="sxs-lookup"><span data-stu-id="51116-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51116-111">备注</span><span class="sxs-lookup"><span data-stu-id="51116-111">Remarks</span></span>  

 <span data-ttu-id="51116-112">指定要创建的文件的完整名称和扩展名。</span><span class="sxs-lookup"><span data-stu-id="51116-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="51116-113">如果不这样做，.exe 文件将从包含 `Sub Main` 过程的源代码文件中获取名称，.dll 文件将从第一个源代码文件中获取其名称。</span><span class="sxs-lookup"><span data-stu-id="51116-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="51116-114">如果指定不带 .exe 或 .dll 扩展名的文件名，则编译器会根据为 `-target` 编译器选项指定的值自动添加扩展。</span><span class="sxs-lookup"><span data-stu-id="51116-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="51116-115">在 Visual Studio 集成开发环境中设置 -out</span><span class="sxs-lookup"><span data-stu-id="51116-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="51116-116">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="51116-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51116-117">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="51116-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="51116-118">2.单击“应用程序”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="51116-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="51116-119">3.修改“程序集名称”  框中的值。</span><span class="sxs-lookup"><span data-stu-id="51116-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51116-120">示例</span><span class="sxs-lookup"><span data-stu-id="51116-120">Example</span></span>  

 <span data-ttu-id="51116-121">下面的代码编译 `T2.vb` 并创建输出文件 `T2.exe`。</span><span class="sxs-lookup"><span data-stu-id="51116-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="51116-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="51116-122">See also</span></span>

- [<span data-ttu-id="51116-123">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="51116-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="51116-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51116-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="51116-125">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="51116-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
