---
title: 使用 XML 记录代码
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590924"
---
# <a name="document-your-code-with-xml-visual-basic"></a><span data-ttu-id="2247b-102">用 XML （Visual Basic）记录你的代码</span><span class="sxs-lookup"><span data-stu-id="2247b-102">Document your code with XML (Visual Basic)</span></span>

<span data-ttu-id="2247b-103">在 Visual Basic 中，可以使用 XML 记录代码。</span><span class="sxs-lookup"><span data-stu-id="2247b-103">In Visual Basic, you can document your code using XML.</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="2247b-104">XML 文档注释</span><span class="sxs-lookup"><span data-stu-id="2247b-104">XML documentation comments</span></span>

<span data-ttu-id="2247b-105">Visual Basic 提供了一种简单的方法来自动创建项目的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="2247b-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="2247b-106">可以为类型和成员自动生成 XML 主干，然后提供每个参数的摘要、描述性文档和其他备注。</span><span class="sxs-lookup"><span data-stu-id="2247b-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="2247b-107">使用适当的设置，XML 文档将自动发送到具有与项目相同的根文件名的 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="2247b-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same root file name as your project.</span></span> <span data-ttu-id="2247b-108">有关详细信息，请参阅 [-doc](../../reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="2247b-108">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="2247b-109">可以使用 XML 文件或以其他方式将其作为 XML 来处理。</span><span class="sxs-lookup"><span data-stu-id="2247b-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="2247b-110">此文件与项目的输出 .exe 或 .dll 文件位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="2247b-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="2247b-111">XML 文档以开头 `'''` 。</span><span class="sxs-lookup"><span data-stu-id="2247b-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="2247b-112">处理这些注释时存在一些限制：</span><span class="sxs-lookup"><span data-stu-id="2247b-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="2247b-113">文档必须是格式正确的 XML。</span><span class="sxs-lookup"><span data-stu-id="2247b-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="2247b-114">如果 XML 格式不正确，则会生成警告，并且文档文件将会显示一条注释，指出遇到了错误。</span><span class="sxs-lookup"><span data-stu-id="2247b-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="2247b-115">开发人员可以随意创建自己的标记集。</span><span class="sxs-lookup"><span data-stu-id="2247b-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="2247b-116">建议使用一组标记（请参阅[XML 注释标记](../../language-reference/xmldoc/index.md)）。</span><span class="sxs-lookup"><span data-stu-id="2247b-116">There is a recommended set of tags (see [XML Comment Tags](../../language-reference/xmldoc/index.md)).</span></span> <span data-ttu-id="2247b-117">部分建议标记具有特殊含义：</span><span class="sxs-lookup"><span data-stu-id="2247b-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="2247b-118">\<param>标记用于描述参数。</span><span class="sxs-lookup"><span data-stu-id="2247b-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="2247b-119">如果使用，编译器将验证该参数是否存在，以及文档是否描述了所有参数。</span><span class="sxs-lookup"><span data-stu-id="2247b-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="2247b-120">如果验证失败，则编译器会发出警告。</span><span class="sxs-lookup"><span data-stu-id="2247b-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="2247b-121">`cref` 属性可以附加到任何标记，以提供对代码元素的引用。</span><span class="sxs-lookup"><span data-stu-id="2247b-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="2247b-122">编译器验证此代码元素是否存在。</span><span class="sxs-lookup"><span data-stu-id="2247b-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="2247b-123">如果验证失败，则编译器会发出警告。</span><span class="sxs-lookup"><span data-stu-id="2247b-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="2247b-124">`Imports`查找特性中所述的类型时，编译器还会考虑所有语句 `cref` 。</span><span class="sxs-lookup"><span data-stu-id="2247b-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="2247b-125">\<summary>Visual Studio 中的 IntelliSense 使用标记显示关于类型或成员的其他信息。</span><span class="sxs-lookup"><span data-stu-id="2247b-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="2247b-126">相关章节</span><span class="sxs-lookup"><span data-stu-id="2247b-126">Related sections</span></span>

<span data-ttu-id="2247b-127">有关创建包含文档注释的 XML 文件的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="2247b-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="2247b-128">-doc</span><span class="sxs-lookup"><span data-stu-id="2247b-128">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="2247b-129">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="2247b-129">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="2247b-130">处理 XML 文件</span><span class="sxs-lookup"><span data-stu-id="2247b-130">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="2247b-131">如何：创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="2247b-131">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="2247b-132">Visual Studio 中的 XML 工具</span><span class="sxs-lookup"><span data-stu-id="2247b-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="2247b-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2247b-133">See also</span></span>

- [<span data-ttu-id="2247b-134">使用 Visual Basic 开发应用程序</span><span class="sxs-lookup"><span data-stu-id="2247b-134">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="2247b-135">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="2247b-135">Visual Basic Programming Guide</span></span>](../index.md)
