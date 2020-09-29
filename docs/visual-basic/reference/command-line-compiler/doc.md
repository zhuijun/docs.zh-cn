---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 8b80629ce9b2cd62f10d9a53279b83ba41bc4ece
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097704"
---
# <a name="-doc"></a><span data-ttu-id="10df0-102">-doc</span><span class="sxs-lookup"><span data-stu-id="10df0-102">-doc</span></span>

<span data-ttu-id="10df0-103">将文档注释处理到一个 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="10df0-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10df0-104">语法</span><span class="sxs-lookup"><span data-stu-id="10df0-104">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="10df0-105">or</span><span class="sxs-lookup"><span data-stu-id="10df0-105">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="10df0-106">自变量</span><span class="sxs-lookup"><span data-stu-id="10df0-106">Arguments</span></span>  
  
|<span data-ttu-id="10df0-107">术语</span><span class="sxs-lookup"><span data-stu-id="10df0-107">Term</span></span>|<span data-ttu-id="10df0-108">定义</span><span class="sxs-lookup"><span data-stu-id="10df0-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="10df0-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="10df0-109">`+` &#124; `-`</span></span>|<span data-ttu-id="10df0-110">可选。</span><span class="sxs-lookup"><span data-stu-id="10df0-110">Optional.</span></span> <span data-ttu-id="10df0-111">指定 + 或仅 `-doc` 会导致编译器生成文档信息并将其置于 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="10df0-111">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="10df0-112">指定 `-` 相当于未指定 `-doc`，因此不会创建任何文档信息。</span><span class="sxs-lookup"><span data-stu-id="10df0-112">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="10df0-113">如果使用 `-doc:`，则是必需的。</span><span class="sxs-lookup"><span data-stu-id="10df0-113">Required if `-doc:` is used.</span></span> <span data-ttu-id="10df0-114">指定输出 XML 文件（由编译的源代码文件中的注释填充）。</span><span class="sxs-lookup"><span data-stu-id="10df0-114">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="10df0-115">如果文件名包含空格，请用引号 (" ") 括住该名称。</span><span class="sxs-lookup"><span data-stu-id="10df0-115">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10df0-116">备注</span><span class="sxs-lookup"><span data-stu-id="10df0-116">Remarks</span></span>  

 <span data-ttu-id="10df0-117">`-doc` 选项控制编译器是否生成包含文档注释的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="10df0-117">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="10df0-118">如果使用 `-doc:file` 语法，`file` 参数会指定 XML 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="10df0-118">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="10df0-119">如果使用 `-doc` 或 `-doc+`，编译器会从其正在创建的可执行文件或库中获取 XML 文件名。</span><span class="sxs-lookup"><span data-stu-id="10df0-119">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="10df0-120">如果使用 `-doc-` 或未指定 `-doc` 选项，则编译器不会创建 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="10df0-120">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="10df0-121">在源代码文件中，文档注释可先于以下定义：</span><span class="sxs-lookup"><span data-stu-id="10df0-121">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="10df0-122">用户定义类型，例如[类](../../language-reference/statements/class-statement.md)或[接口](../../language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="10df0-122">User-defined types, such as a [class](../../language-reference/statements/class-statement.md) or [interface](../../language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="10df0-123">成员，例如字段、[事件](../../language-reference/statements/event-statement.md)、[属性](../../language-reference/statements/property-statement.md)、[函数](../../language-reference/statements/function-statement.md)或[子例程](../../language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="10df0-123">Members, such as a field, [event](../../language-reference/statements/event-statement.md), [property](../../language-reference/statements/property-statement.md), [function](../../language-reference/statements/function-statement.md), or [subroutine](../../language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="10df0-124">若要将生成的 XML 文件与 Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) 功能配合使用，请将 XML 文件的文件名设为与要支持的程序集相同的名称。</span><span class="sxs-lookup"><span data-stu-id="10df0-124">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="10df0-125">确保 XML 文件与程序集位于同一目录中，以便在 Visual Studio 项目中引用此程序集时，也可以找到 .xml 文件。</span><span class="sxs-lookup"><span data-stu-id="10df0-125">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="10df0-126">IntelliSense 不需要 XML 文档文件来处理项目内或项目引用的项目中的代码。</span><span class="sxs-lookup"><span data-stu-id="10df0-126">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="10df0-127">除非使用 `-target:module` 进行编译，否则 XML 文件包含标记 `<assembly></assembly>`。</span><span class="sxs-lookup"><span data-stu-id="10df0-127">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="10df0-128">这些标记指定包含编译输出文件的程序集清单的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="10df0-128">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="10df0-129">有关从代码中的注释生成文档的方法，请参阅 [XML 注释标记](../../language-reference/xmldoc/index.md)。</span><span class="sxs-lookup"><span data-stu-id="10df0-129">See [XML Comment Tags](../../language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="10df0-130">在 Visual Studio 集成开发环境中设置 -doc</span><span class="sxs-lookup"><span data-stu-id="10df0-130">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="10df0-131">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="10df0-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="10df0-132">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="10df0-132">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="10df0-133">2.单击“编译”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="10df0-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="10df0-134">3.在“生成 XML 文档文件”  框中设置值。</span><span class="sxs-lookup"><span data-stu-id="10df0-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="10df0-135">示例</span><span class="sxs-lookup"><span data-stu-id="10df0-135">Example</span></span>  

 <span data-ttu-id="10df0-136">有关示例，请参阅[使用 XML 来记录代码](../../programming-guide/program-structure/documenting-your-code-with-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="10df0-136">See [Documenting Your Code with XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10df0-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="10df0-137">See also</span></span>

- [<span data-ttu-id="10df0-138">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="10df0-138">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="10df0-139">使用 XML 记录代码</span><span class="sxs-lookup"><span data-stu-id="10df0-139">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
