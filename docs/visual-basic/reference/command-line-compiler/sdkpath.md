---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 18bf22861c1cbc3a37ef917b421491c2d01efba8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085108"
---
# <a name="-sdkpath"></a><span data-ttu-id="787a4-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="787a4-102">-sdkpath</span></span>

<span data-ttu-id="787a4-103">指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="787a4-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="787a4-104">语法</span><span class="sxs-lookup"><span data-stu-id="787a4-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="787a4-105">自变量</span><span class="sxs-lookup"><span data-stu-id="787a4-105">Arguments</span></span>  

 `path`  
 <span data-ttu-id="787a4-106">目录中包含要用于编译的 mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本。</span><span class="sxs-lookup"><span data-stu-id="787a4-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="787a4-107">加载此路径后才会对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="787a4-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="787a4-108">如果目录名包含空格，则将名称括在引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="787a4-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="787a4-109">备注</span><span class="sxs-lookup"><span data-stu-id="787a4-109">Remarks</span></span>  

 <span data-ttu-id="787a4-110">此选项告诉 Visual Basic 编译器从非默认位置加载 mscorlib.dll 和 Microsoft.VisualBasic.dll 文件。</span><span class="sxs-lookup"><span data-stu-id="787a4-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="787a4-111">`-sdkpath` 选项专门与 [-netcf](netcf.md) 一起使用。</span><span class="sxs-lookup"><span data-stu-id="787a4-111">The `-sdkpath` option was designed to be used with [-netcf](netcf.md).</span></span> <span data-ttu-id="787a4-112">.NET Compact Framework 使用这些支持库的不同版本，以避免使用设备上没有的类型和语言功能。</span><span class="sxs-lookup"><span data-stu-id="787a4-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="787a4-113">`-sdkpath` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="787a4-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="787a4-114">加载 Visual Basic 设备项目时，将设置 `-sdkpath` 选项。</span><span class="sxs-lookup"><span data-stu-id="787a4-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="787a4-115">可以使用 `-vbruntime` 编译器选项指定：应在不引用 Visual Basic 运行时库的情况下进行编译。</span><span class="sxs-lookup"><span data-stu-id="787a4-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="787a4-116">有关详细信息，请参阅 [-vbruntime](vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="787a4-116">For more information, see [-vbruntime](vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="787a4-117">示例</span><span class="sxs-lookup"><span data-stu-id="787a4-117">Example</span></span>  

 <span data-ttu-id="787a4-118">以下代码使用 C 盘上 .NET Compact Framework 的默认安装目录中的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 版本，通过 .NET Compact Framework 编译 `Myfile.vb`。</span><span class="sxs-lookup"><span data-stu-id="787a4-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="787a4-119">通常，会使用 .NET Compact Framework 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="787a4-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="787a4-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="787a4-120">See also</span></span>

- [<span data-ttu-id="787a4-121">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="787a4-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="787a4-122">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="787a4-122">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="787a4-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="787a4-123">-netcf</span></span>](netcf.md)
- [<span data-ttu-id="787a4-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="787a4-124">-vbruntime</span></span>](vbruntime.md)
