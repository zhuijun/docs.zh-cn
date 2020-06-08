---
title: 如何：调用命令行编译器
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 6def53d4a2d15dda3e3ac43abe35b3100f456fe9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408603"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="3ecc4-102">如何：调用命令行编译器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ecc4-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="3ecc4-103">可以通过在命令行中键入可执行文件的名称（也称为 MS-DOS 提示符）来调用命令行编译器。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="3ecc4-104">如果从默认的 Windows 命令提示符下进行编译，则必须键入可执行文件的完全限定的路径。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="3ecc4-105">若要重写此默认行为，可以使用 Visual Studio 的开发人员命令提示，也可以修改 PATH 环境变量。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="3ecc4-106">无论使用哪种方法，都可以通过键入编译器名称从任何目录中进行编译。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="3ecc4-107">使用 Visual Studio 的开发人员命令提示调用编译器</span><span class="sxs-lookup"><span data-stu-id="3ecc4-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="3ecc4-108">打开 Microsoft Visual Studio 程序组中的“Visual Studio Tools 程序”文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="3ecc4-109">如果安装了 Visual Studio，则可以使用 Visual Studio 的开发人员命令提示从计算机上的任何目录访问编译器。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="3ecc4-110">调用 Visual Studio 开发人员命令提示。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="3ecc4-111">在命令行处，键入 `vbc.exe` sourceFileName  ，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="3ecc4-112">例如，如果将源代码存储在名为 `SourceFiles` 的目录中，则可以打开命令提示符并键入 `cd SourceFiles` 以更改为该目录。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="3ecc4-113">如果该目录已包含一个名为 `Source.vb` 的源文件，则可以通过键入 `vbc.exe Source.vb` 对其进行编译。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="3ecc4-114">将 PATH 环境变量设置为 Windows 命令提示符的编译器</span><span class="sxs-lookup"><span data-stu-id="3ecc4-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="3ecc4-115">使用 Windows Search 功能在本地磁盘上查找 Vbc.exe。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="3ecc4-116">编译器所在目录的确切名称取决于 Windows 目录的位置和安装的“.NET Framework”版本。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="3ecc4-117">如果安装了多个版本的“.NET Framework”，必须确定要使用哪个版本（通常是最新版本）。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="3ecc4-118">在“开始”菜单中，右键单击“我的电脑”，然后从快捷菜单中单击“属性”    。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="3ecc4-119">单击“高级”选项卡，然后单击“环境变量”   。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="3ecc4-120">在“系统”变量窗格中，从列表中选择“路径”，然后单击“编辑”    。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="3ecc4-121">在“编辑系统变量”对话框中，将插入点移到“变量值”字段中字符串的末尾，然后键入一个分号 (;)，随后键入在步骤 1 中找到的完整目录名称   。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="3ecc4-122">单击“确定”  确认编辑内容并关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="3ecc4-123">更改 PATH 环境变量后，可以从计算机上的任何目录中的 Windows 命令提示符处运行 Visual Basic 编译器。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="3ecc4-124">使用 Windows 命令提示符调用编译器</span><span class="sxs-lookup"><span data-stu-id="3ecc4-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="3ecc4-125">在“开始”菜单中，单击“附件”文件夹，然后打开“Windows 命令提示符”    。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="3ecc4-126">在命令行处，键入 `vbc.exe` sourceFileName  ，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="3ecc4-127">例如，如果将源代码存储在名为 `SourceFiles` 的目录中，则可以打开命令提示符并键入 `cd SourceFiles` 以更改为该目录。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="3ecc4-128">如果该目录已包含一个名为 `Source.vb` 的源文件，则可以通过键入 `vbc.exe Source.vb` 对其进行编译。</span><span class="sxs-lookup"><span data-stu-id="3ecc4-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ecc4-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="3ecc4-129">See also</span></span>

- [<span data-ttu-id="3ecc4-130">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="3ecc4-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3ecc4-131">条件编译</span><span class="sxs-lookup"><span data-stu-id="3ecc4-131">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
