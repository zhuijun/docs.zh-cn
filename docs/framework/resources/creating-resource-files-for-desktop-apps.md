---
title: 为 .NET 应用创建资源文件
description: 为 .NET 应用创建资源文件。 以编程方式生成包含字符串资源的文本文件、XML 文件或二进制文件，或者生成包含字符串、图像或对象数据的 XML 文件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
ms.openlocfilehash: 4730a14e499c75176d7ba7c8378626070d5211e9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865172"
---
# <a name="create-resource-files-for-net-apps"></a><span data-ttu-id="4ebfa-104">为 .NET 应用创建资源文件</span><span class="sxs-lookup"><span data-stu-id="4ebfa-104">Create resource files for .NET apps</span></span>

<span data-ttu-id="4ebfa-105">可以将字符串、图像或对象数据等资源包含在资源文件中，方便应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-105">You can include resources, such as strings, images, or object data, in resources files to make them easily available to your application.</span></span> <span data-ttu-id="4ebfa-106">.NET Framework 提供了五种创建资源文件的方法：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-106">The .NET Framework offers five ways to create resources files:</span></span>

- <span data-ttu-id="4ebfa-107">创建一个包含字符串资源的文本文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-107">Create a text file that contains string resources.</span></span> <span data-ttu-id="4ebfa-108">可以使用[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 将文本文件转换成二进制资源 (.resources) 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-108">You can use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to convert the text file into a binary resource (.resources) file.</span></span> <span data-ttu-id="4ebfa-109">然后使用语言编译器将这个二进制资源文件嵌入可执行应用程序或应用程序库，或者使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 将这个二进制资源文件嵌入附属程序集。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-109">You can then embed the binary resource file  in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="4ebfa-110">有关详细信息，请参阅[文本文件中的资源](creating-resource-files-for-desktop-apps.md#TextFiles)部分。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-110">For more information, see the [Resources in Text Files](creating-resource-files-for-desktop-apps.md#TextFiles) section.</span></span>

- <span data-ttu-id="4ebfa-111">创建一个包含字符串、图像或对象数据的 XML 资源 (.resx) 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-111">Create an XML resource (.resx) file that contains string, image, or object data.</span></span> <span data-ttu-id="4ebfa-112">可以使用[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 将 .resx 文件转换成二进制资源 (.resources) 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-112">You can use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to convert the .resx file into a binary resource (.resources) file.</span></span> <span data-ttu-id="4ebfa-113">然后使用语言编译器将这个二进制资源文件嵌入可执行应用程序或应用程序库，或者使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 将这个二进制资源文件嵌入附属程序集。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-113">You can then embed the binary resource file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="4ebfa-114">有关详细信息，请参阅 [.resx 文件中的资源](creating-resource-files-for-desktop-apps.md#ResxFiles)部分。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-114">For more information, see the [Resources in .resx Files](creating-resource-files-for-desktop-apps.md#ResxFiles) section.</span></span>

- <span data-ttu-id="4ebfa-115">使用 <xref:System.Resources> 命名空间中的类型以编程方式创建一个 XML 资源 (.resx) 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-115">Create an XML resource (.resx) file programmatically by using types in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="4ebfa-116">可以创建一个 .resx 文件、枚举其资源并按名称检索特定资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-116">You can create a .resx file, enumerate its resources, and retrieve specific resources by name.</span></span> <span data-ttu-id="4ebfa-117">有关详细信息，请参阅[以编程方式使用 .resx 文件](working-with-resx-files-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-117">For more information, see [Working with .resx Files Programmatically](working-with-resx-files-programmatically.md).</span></span>

- <span data-ttu-id="4ebfa-118">以编程方式创建一个二进制资源 (.resources) 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-118">Create a binary resource (.resources) file programmatically.</span></span> <span data-ttu-id="4ebfa-119">然后使用语言编译器将该文件嵌入可执行应用程序或应用程序库，或者使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 将这个二进制资源文件嵌入附属程序集。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-119">You can then embed the file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="4ebfa-120">有关详细信息，请参阅 [.resources 文件中的资源](creating-resource-files-for-desktop-apps.md#ResourcesFiles)部分。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-120">For more information, see the [Resources in .resources Files](creating-resource-files-for-desktop-apps.md#ResourcesFiles) section.</span></span>

- <span data-ttu-id="4ebfa-121">使用 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 创建一个资源文件并将其包含在项目中。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-121">Use [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) to create a resource file and include it in your project.</span></span> <span data-ttu-id="4ebfa-122">Visual Studio 提供一个资源编辑器，借助该编辑器，可添加、删除和修改资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-122">Visual Studio provides a resource editor that lets you add, delete, and modify resources.</span></span> <span data-ttu-id="4ebfa-123">编译时，资源文件会自动转换成二进制 .resources 文件，并嵌入应用程序程序集或附属程序集中。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-123">At compile time, the resource file is automatically converted to a binary .resources file and embedded in an application assembly or satellite assembly.</span></span> <span data-ttu-id="4ebfa-124">有关详细信息，请参阅 [Visual Studio 中的资源文件](creating-resource-files-for-desktop-apps.md#VSResFiles)部分。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-124">For more information, see the [Resource Files in Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span>

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a><span data-ttu-id="4ebfa-125">文本文件中的资源</span><span class="sxs-lookup"><span data-stu-id="4ebfa-125">Resources in text files</span></span>

<span data-ttu-id="4ebfa-126">文本（.txt 或 .restext）文件只能用于存储字符串资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-126">You can use text (.txt or .restext) files to store string resources only.</span></span> <span data-ttu-id="4ebfa-127">对于非字符串资源，使用 .resx 文件或以编程方式创建它们。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-127">For non-string resources, use .resx files or create them programmatically.</span></span> <span data-ttu-id="4ebfa-128">包含字符串资源的文本文件使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-128">Text files that contain string resources have the following format:</span></span>

```text
# This is an optional comment.
name = value

; This is another optional comment.
name = value

; The following supports conditional compilation if X is defined.
#ifdef X
name1=value1
name2=value2
#endif

# The following supports conditional compilation if Y is undefined.
#if !Y
name1=value1
name2=value2
#endif
```

 <span data-ttu-id="4ebfa-129">.txt 和 .restext 文件的资源文件格式是相同的。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-129">The resource file format of .txt and .restext files is identical.</span></span> <span data-ttu-id="4ebfa-130">.restext 文件扩展名仅用于明确区分文本文件和基于文本的资源文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-130">The .restext file extension merely serves to make text files immediately identifiable as text-based resource files.</span></span>

 <span data-ttu-id="4ebfa-131">字符串资源显示为名称/值对，其中名称是标识资源的字符串，值是在将名称传递给资源检索方法（例如 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>）时返回的资源字符串     。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-131">String resources appear as *name/value* pairs, where *name* is a string that identifies the resource, and *value* is the resource string that is returned when you pass *name* to a resource retrieval method such as <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ebfa-132">名称和值必须用等号 (=) 分隔开   。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-132">*name* and *value* must be separated by an equal sign (=).</span></span> <span data-ttu-id="4ebfa-133">例如：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-133">For example:</span></span>

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> <span data-ttu-id="4ebfa-134">请勿使用资源文件存储密码、 安全敏感信息或私人数据。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-134">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="4ebfa-135">在文本文件中，允许存在空字符串（即值为 <xref:System.String.Empty?displayProperty=nameWithType> 的资源）。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-135">Empty strings (that is, a resource whose value is <xref:System.String.Empty?displayProperty=nameWithType>) are permitted in text files.</span></span> <span data-ttu-id="4ebfa-136">例如：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-136">For example:</span></span>

```text
EmptyString=
```

 <span data-ttu-id="4ebfa-137">从 .NET Framework 4.5 开始并在所有版本的 .NET Core 中，文本文件支持使用 `#ifdef`symbol  ... `#endif` 和 `#if !`symbol  ... `#endif` 构造的传统编译。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-137">Starting with .NET Framework 4.5 and in all versions of .NET Core, text files support conditional compilation with the `#ifdef`*symbol*... `#endif` and `#if !`*symbol*... `#endif` constructs.</span></span> <span data-ttu-id="4ebfa-138">还可以通过[资源文件生成器 (resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 使用 `/define` 开关来定义符号。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-138">You can then use the `/define` switch with [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to define symbols.</span></span> <span data-ttu-id="4ebfa-139">每个资源都需要其自己的 `#ifdef`symbol... `#endif` 或 `#if !`symbol... `#endif` 构造   。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-139">Each resource requires its own `#ifdef`*symbol*... `#endif` or `#if !`*symbol*... `#endif` construct.</span></span> <span data-ttu-id="4ebfa-140">如果使用的是 `#ifdef` 语句，并且定义了 symbol，则关联的资源将包括在 .resources 文件中；否则，将不包括此资源  。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-140">If you use an `#ifdef` statement and *symbol* is defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span> <span data-ttu-id="4ebfa-141">如果使用的是 `#if !` 语句，并且没有定义 symbol，则关联的资源将包括在 .resources 文件中；否则，将不包括此资源  。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-141">If you use an `#if !` statement and *symbol* is not defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span>

 <span data-ttu-id="4ebfa-142">注释在文本文件中为可选项，并且在每行开头使用分号 (;) 或者井号 (#) 开头。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-142">Comments are optional in text files and are preceded either by a semicolon (;) or by a pound sign (#) at the beginning of a line.</span></span> <span data-ttu-id="4ebfa-143">包含注释的行可位于文件中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-143">Lines that contain comments can be placed anywhere in the file.</span></span> <span data-ttu-id="4ebfa-144">使用[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 创建的已编译 .resources 文件中不包含注释。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-144">Comments are not included in a compiled .resources file that is created by using [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span></span>

 <span data-ttu-id="4ebfa-145">文本文件中的所有空白行将视为空格并忽略。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-145">Any blank lines in the text files are considered to be white space and are ignored.</span></span>

 <span data-ttu-id="4ebfa-146">下面的示例定义名为 `OKButton` 和 `CancelButton` 的两个字符串资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-146">The following example defines two string resources named `OKButton` and `CancelButton`.</span></span>

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 <span data-ttu-id="4ebfa-147">如果文本文件包含名称的重复匹配项，[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 将显示一条警告，并忽略第二个名称  。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-147">If the text file contains duplicate occurrences of *name*, [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) displays a warning and ignores the second name.</span></span>

 <span data-ttu-id="4ebfa-148">值不能包含换行符，但可以使用 C 语言样式的转义符，例如使用 `\n` 表示新行，使用 `\t` 表示制表符  。还可以使用经过转义的反斜杠字符（例如，“\\\\”）。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-148">*value* cannot contain new line characters, but you can use C language-style escape characters such as `\n` to represent a new line and `\t` to represent a tab. You can also include a backslash character if it is escaped (for example, "\\\\").</span></span> <span data-ttu-id="4ebfa-149">此外，允许使用空字符串。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-149">In addition, an empty string is permitted.</span></span>

 <span data-ttu-id="4ebfa-150">使用 little-endian 或 big-endian 字节顺序的 UTF-8 编码或 UTF-16 编码以文本文件格式保存资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-150">Save resources in text file format by using UTF-8 encoding or UTF-16 encoding in either little-endian or big-endian byte order.</span></span> <span data-ttu-id="4ebfa-151">但是在默认情况下，将 .txt 文件转换为 .resources 文件的[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 会将文件默认视为 UTF-8 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-151">However, [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md), which converts a .txt file to a .resources file, treats files as UTF-8 by default.</span></span> <span data-ttu-id="4ebfa-152">如果希望 Resgen.exe 识别使用 UTF-16 编码的文件，必须在文件开头包含 Unicode 字节顺序标记 (U + FEFF)。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-152">If you want Resgen.exe to recognize a file that was encoded using UTF-16, you must include a Unicode byte order mark (U+FEFF) at the beginning of the file.</span></span>

 <span data-ttu-id="4ebfa-153">若要将文本格式的资源文件嵌入到 .NET 程序集，必须使用[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 将文件转换为二进制资源 (.resources) 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-153">To embed a resource file in text format into a .NET assembly, you must convert the file to a binary resource (.resources) file by using [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md).</span></span> <span data-ttu-id="4ebfa-154">然后可使用语言编译器将 .resources 文件嵌入 .NET 程序集，或者使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 将其嵌入附属程序集。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-154">You can then embed the .resources file in a .NET assembly by using a language compiler or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>

 <span data-ttu-id="4ebfa-155">下面的示例在简单的“Hello World”控制台应用程序中使用了一个名为 GreetingResources.txt 的文本格式的资源文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-155">The following example uses a resource file in text format named GreetingResources.txt for a simple "Hello World" console application.</span></span> <span data-ttu-id="4ebfa-156">该文本文件定义了 `prompt` 和 `greeting` 两个字符串，分别用于提示用户输入其名字和显示一条问候。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-156">The text file defines two strings, `prompt` and `greeting`, that prompt the user to enter their name and display a greeting.</span></span>

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

<span data-ttu-id="4ebfa-157">使用以下命令可以将该文本文件转换成 .resources 文件：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-157">The text file is converted to a .resources file by using the following command:</span></span>

```console
resgen GreetingResources.txt
```

 <span data-ttu-id="4ebfa-158">下面的示例展示了某控制台应用程序中的源代码，该控制台应用程序使用 .resources 文件向用户显示信息。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-158">The following example shows the source code for a console application that uses the .resources file to display messages to the user.</span></span>

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 <span data-ttu-id="4ebfa-159">如果使用的是 Visual Basic，且源代码文件名为 Greeting.vb，以下命令将创建一个包含嵌入的 .resources 文件的可执行文件：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-159">If you are using Visual Basic, and the source code file is named Greeting.vb, the following command creates an executable file that includes the embedded .resources file:</span></span>

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 <span data-ttu-id="4ebfa-160">如果使用的是 C#，并且将源代码文件命名为 Greeting.cs，以下命令将创建一个包含嵌入 .resources 文件的可执行文件：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-160">If you are using C#, and the source code file is named Greeting.cs, the following command creates an executable file that includes the embedded .resources file:</span></span>

```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a><span data-ttu-id="4ebfa-161">.resx 文件中的资源</span><span class="sxs-lookup"><span data-stu-id="4ebfa-161">Resources in .resx files</span></span>
 <span data-ttu-id="4ebfa-162">与只能存储字符串资源的文本文件不同，XML 资源 (.resx) 文件可以存储字符串、二进制数据（图像、图标和音频剪辑等）以及编程对象。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-162">Unlike text files, which can only store string resources, XML resource (.resx) files can store strings, binary data such as images, icons, and audio clips, and programmatic objects.</span></span> <span data-ttu-id="4ebfa-163">.resx 文件包含一个标准标头，用以描述资源条目的格式，并指定用于解析数据的 XML 的版本信息。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-163">A .resx file contains a standard header, which describes the format of the resource entries and specifies the versioning information for the XML that is used to parse the data.</span></span> <span data-ttu-id="4ebfa-164">资源文件数据跟在 XML 标头之后。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-164">The resource file data follows the XML header.</span></span> <span data-ttu-id="4ebfa-165">每个数据项由包含在 `data` 标记中的一个名称/值对构成。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-165">Each data item consists of a name/value pair that is contained in a `data` tag.</span></span> <span data-ttu-id="4ebfa-166">其 `name` 属性定义资源名称，而嵌套的 `value` 标记包含资源值。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-166">Its `name` attribute defines the resource name, and the nested `value` tag contains the resource value.</span></span> <span data-ttu-id="4ebfa-167">对于字符串数据，`value` 标记包含字符串。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-167">For string data, the `value` tag contains the string.</span></span>

 <span data-ttu-id="4ebfa-168">例如，以下 `data` 标记定义了一个名为 `prompt` 且值为“Enter your name”的字符串资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-168">For example, the following `data` tag defines a string resource named `prompt` whose value is "Enter your name:".</span></span>

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> <span data-ttu-id="4ebfa-169">请勿使用资源文件存储密码、 安全敏感信息或私人数据。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-169">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="4ebfa-170">对于资源对象，data 标记中包含了 `type` 属性，用于指示资源的数据类型  。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-170">For resource objects, the **data** tag includes a `type` attribute that indicates the data type of the resource.</span></span> <span data-ttu-id="4ebfa-171">对于由二进制数据构成的对象，`data` 标记还包含 `mimetype` 属性，用以指示二进制数据的 `base64` 类型。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-171">For objects that consist of binary data, the `data` tag also includes a `mimetype` attribute, which indicates the `base64` type of the binary data.</span></span>

> [!NOTE]
> <span data-ttu-id="4ebfa-172">所有的 .resx 文件都使用二进制序列化格式化程序来生成和分析指定类型的二进制数据。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-172">All .resx files use a binary serialization formatter to generate and parse the binary data for a specified type.</span></span> <span data-ttu-id="4ebfa-173">因此如果对象的二进制序列化格式以不兼容的方式发生更改，.resx 文件可能失效。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-173">As a result, a .resx file can become invalid if the binary serialization format for an object changes in an incompatible way.</span></span>

 <span data-ttu-id="4ebfa-174">以下示例显示了部分包含 <xref:System.Int32> 资源和位图图像的 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-174">The following example shows a portion of a .resx file that includes an <xref:System.Int32> resource and a bitmap image.</span></span>

```xml
<data name="i1" type="System.Int32, mscorlib">
  <value>20</value>
</data>

<data name="flag" type="System.Drawing.Bitmap, System.Drawing,
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
    mimetype="application/x-microsoft.net.object.bytearray.base64">
  <value>
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…
  </value>
</data>
```

> [!IMPORTANT]
> <span data-ttu-id="4ebfa-175">由于 .resx 文件必须由采用预定义格式的格式标准的 XML 构成，不建议手动使用 .resx 文件，尤其是当 .resx 文件包含非字符串资源时。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-175">Because .resx files must consist of well-formed XML in a predefined format, we do not recommend working with .resx files manually, particularly when the .resx files contain resources other than strings.</span></span> <span data-ttu-id="4ebfa-176">相反，[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 提供一个用于创建和操作 .resx 文件的透明接口。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-176">Instead, [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) provides a transparent interface for creating and manipulating .resx files.</span></span> <span data-ttu-id="4ebfa-177">有关详细信息，请参阅 [Visual Studio 中的资源文件](creating-resource-files-for-desktop-apps.md#VSResFiles)部分。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-177">For more information, see the [Resource Files in Visual Studio](creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span> <span data-ttu-id="4ebfa-178">还可以通过编程方式创建和操作 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-178">You can also create and manipulate .resx files programmatically.</span></span> <span data-ttu-id="4ebfa-179">有关详细信息，请参阅[以编程方式使用 .resx 文件](working-with-resx-files-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-179">For more information, see [Working with .resx Files Programmatically](working-with-resx-files-programmatically.md).</span></span>

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a><span data-ttu-id="4ebfa-180">.resources 文件中的资源</span><span class="sxs-lookup"><span data-stu-id="4ebfa-180">Resources in .resources files</span></span>

<span data-ttu-id="4ebfa-181">可以使用 <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> 类以编程方式从代码中直接创建二进制资源 (.resources) 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-181">You can use the <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> class to programmatically create a binary resource (.resources) file directly from code.</span></span> <span data-ttu-id="4ebfa-182">还可以使用[资源文件生成器 (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) 从文本文件或 .resx 文件创建 .resources 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-182">You can also use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to create a .resources file from a text file or a .resx file.</span></span> <span data-ttu-id="4ebfa-183">.resources 文件除了可以包含字符串数据之外，还可以包含二进制数据（字节数组）和对象数据。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-183">The .resources file can contain binary data (byte arrays) and object data in addition to string data.</span></span> <span data-ttu-id="4ebfa-184">以编程方式创建 .resources 文件需要执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="4ebfa-184">Programmatically creating a .resources file requires the following steps:</span></span>

1. <span data-ttu-id="4ebfa-185">创建一个具有唯一文件名的 <xref:System.Resources.ResourceWriter> 对象。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-185">Create a <xref:System.Resources.ResourceWriter> object with a unique file name.</span></span> <span data-ttu-id="4ebfa-186">可以通过将文件名或文件流指定为 <xref:System.Resources.ResourceWriter> 类构造函数来实现这此操作。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-186">You can do this by specifying either a file name or a file stream to a <xref:System.Resources.ResourceWriter> class constructor.</span></span>

2. <span data-ttu-id="4ebfa-187">调用 <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> 方法的重载之一以便将每个已命名的资源添加到文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-187">Call one of the overloads of the <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> method for each named resource to add to the file.</span></span> <span data-ttu-id="4ebfa-188">该资源可以是字符串、对象或二进制数据（字节数组）集合。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-188">The resource can be a string, an object, or a collection of binary data (a byte array).</span></span>

3. <span data-ttu-id="4ebfa-189">通过调用 <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> 方法将资源写入文件并关闭 <xref:System.Resources.ResourceWriter> 对象。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-189">Call the <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> method to write the resources to the file and to close the <xref:System.Resources.ResourceWriter> object.</span></span>

> [!NOTE]
> <span data-ttu-id="4ebfa-190">请勿使用资源文件存储密码、 安全敏感信息或私人数据。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-190">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>

 <span data-ttu-id="4ebfa-191">下面的示例以编程方式创建了一个名为 CarResources.resources 的 .resources 文件，该文件存储了六个字符串、一个图标和两个由应用程序定义的对象（两个 `Automobile` 对象）。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-191">The following example programmatically creates a .resources file named CarResources.resources that stores six strings, an icon, and two application-defined objects (two `Automobile` objects).</span></span> <span data-ttu-id="4ebfa-192">示例中定义并实例化的 `Automobile` 类，使用 <xref:System.SerializableAttribute> 属性进行标记，这样二进制序列化格式化程序便可持久保留该类。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-192">The `Automobile` class, which is defined and instantiated in the example, is tagged with the <xref:System.SerializableAttribute> attribute, which allows it to be persisted by the binary serialization formatter.</span></span>

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 <span data-ttu-id="4ebfa-193">创建 .resources 文件后，可以通过含入语言编译器的 `/resource` 开关将其嵌入运行时可执行文件或库中，或者通过使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 将其嵌入附属程序集。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-193">After you create the .resources file, you can embed it in a run-time executable or library by including the language compiler's `/resource` switch, or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a><span data-ttu-id="4ebfa-194">Visual Studio 中的资源文件</span><span class="sxs-lookup"><span data-stu-id="4ebfa-194">Resource files in Visual Studio</span></span>

<span data-ttu-id="4ebfa-195">将资源文件添加到 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 项目时，Visual Studio 会在项目目录中创建一个 .resx 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-195">When you add a resource file to your [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) project, Visual Studio creates a .resx file in the project directory.</span></span> <span data-ttu-id="4ebfa-196">Visual Studio 会提供资源编辑器，可用于添加字符串、图像和二进制对象。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-196">Visual Studio provides resource editors that enable you to add strings, images, and binary objects.</span></span> <span data-ttu-id="4ebfa-197">编辑器只能用于处理静态数据，因此不能用于储存编程对象；必须以编程方式将对象数据写入 .resx 文件或 .resources 文件。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-197">Because the editors are designed to handle static data only, they cannot be used to store programmatic objects; you must write object data to either a .resx file or to a .resources file programmatically.</span></span> <span data-ttu-id="4ebfa-198">有关详细信息，请参阅[以编程方式使用 .resx 文件](working-with-resx-files-programmatically.md)和 [.resources 文件中的资源](creating-resource-files-for-desktop-apps.md#ResourcesFiles)部分。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-198">For more information, see [Working with .resx Files Programmatically](working-with-resx-files-programmatically.md) and the [Resources in .resources Files](creating-resource-files-for-desktop-apps.md#ResourcesFiles) section.</span></span>

<span data-ttu-id="4ebfa-199">如果要添加本地化资源，请为它们提供与主资源文件相同的根文件名称。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-199">If you're adding localized resources, give them the same root file name as the main resource file.</span></span> <span data-ttu-id="4ebfa-200">还应在文件名中指定其区域性。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-200">You should also designate their culture in the file name.</span></span> <span data-ttu-id="4ebfa-201">例如，如果要添加一个名为 Resources.resx 的资源文件，或许还需要创建名为 Resources.en-US.resx 和 Resources.fr-fr.resx 的资源文件，分别用以保存英语（美国）和法语（法国）区域性的本地化资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-201">For example, if you add a resource file named Resources.resx, you might also create resource files named Resources.en-US.resx and Resources.fr-FR.resx to hold localized resources for the English (United States) and French (France) cultures, respectively.</span></span> <span data-ttu-id="4ebfa-202">还应该指定应用程序的默认区域性。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-202">You should also designate your application's default culture.</span></span> <span data-ttu-id="4ebfa-203">找不到特定区域性的本地化资源时，将使用此默认区域性的资源。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-203">This is the culture whose resources are used if no localized resources for a particular culture can be found.</span></span> <span data-ttu-id="4ebfa-204">若要指定默认区域性，请在 Visual Studio 的解决方案资源管理器中，右键单击项目名称，指向“应用程序”，单击“程序集信息”，然后在“非特定语言”列表中选择合适的语言/区域性   。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-204">To specify the default culture, in Solution Explorer in Visual Studio, right-click the project name, point to Application, click **Assembly Information**, and select the appropriate language/culture in the **Neutral language** list.</span></span>

<span data-ttu-id="4ebfa-205">编译时，Visual Studio 首先将项目中的 .resx 文件转换为二进制资源 (.resources) 文件，并将其存储在项目 obj  目录的子目录中。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-205">At compile time, Visual Studio first converts the .resx files in a project to binary resource (.resources) files and stores them in a subdirectory of the project's *obj* directory.</span></span> <span data-ttu-id="4ebfa-206">Visual Studio 会将不包含本地化资源的所有资源文件嵌入项目生成的主程序集中。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-206">Visual Studio embeds any resource files that do not contain localized resources in the main assembly that is generated by the project.</span></span> <span data-ttu-id="4ebfa-207">如果资源文件包含本地化资源，Visual Studio 会将其嵌入用于每个本地化区域性的单独的附属程序集中。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-207">If any resource files contain localized resources, Visual Studio embeds them in separate satellite assemblies for each localized culture.</span></span> <span data-ttu-id="4ebfa-208">然后将每个附属程序集存储到名称与本地化区域性相对应的目录中。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-208">It then stores each satellite assembly in a directory whose name corresponds to the localized culture.</span></span> <span data-ttu-id="4ebfa-209">例如，本地化的英语（美国）资源存储在 en-US 子目录的附属程序集中。</span><span class="sxs-lookup"><span data-stu-id="4ebfa-209">For example, localized English (United States) resources are stored in a satellite assembly in the en-US subdirectory.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ebfa-210">请参阅</span><span class="sxs-lookup"><span data-stu-id="4ebfa-210">See also</span></span>

- <xref:System.Resources>
- [<span data-ttu-id="4ebfa-211">桌面应用中的资源</span><span class="sxs-lookup"><span data-stu-id="4ebfa-211">Resources in Desktop Apps</span></span>](index.md)
- [<span data-ttu-id="4ebfa-212">打包和部署资源</span><span class="sxs-lookup"><span data-stu-id="4ebfa-212">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
